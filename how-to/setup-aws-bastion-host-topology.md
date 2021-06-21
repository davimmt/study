## Topologia 00
![](../img//setup-aws-bastion-host-topology/topology.png)

## Passo-a-passo
1. Criar AMI User _ec2-manager_ com Programmatic access
   - Attach existing policies directly: AmazonEC2FullAccess
   - Salvar Acess key ID e Secret access key
1. Criar VPC _vpc-topology-00_
   - Adicionar CIDR _10.0.0.0/16_
1. Criar IG _igw-topology-00_; alocar na VPC _topology-00_; adicionar na Route Table gerada automaticamente
1. Criar subnets:
   - sn-public-0-topology-00 / 1a / 10.0.0.0/24
   - sn-private-0-topology-00 / 1a / 10.0.1.0/24
   - sn-public-1-topology-00 / 1b / 10.0.2.0/24
   - sn-private-1-topology-00 / 1b / 10.0.3.0/24
      - Habilitar auto-assign public ip
1. Criar NACL _nacl-private-subnet_
    - INPUT
        - 100 SSH 10.0.0.0/24 ALLOW
        - 200 HTTP 10.0.0.0/24 ALLOW
        - 201 HTTP 10.0.2.0/24 ALLOW
        - \* All DENY
    - OUTPUT
       - 100 Custom TCP 32768 - 65535 10.0.0.0/24 ALLOW
       - 101 Custom TCP 32768 - 65535 10.0.2.0/24 ALLOW
       - \* All DENY
1. Mudar o default security group
    - SSH My IP
    - SSH 10.0.0.0/16
    - HTTP My IP
    - HTTP 10.0.0.0/16
1. Criar security group _secg-bastion-host_
    - SSH My IP
1. Criar security group _secg-proxy-server_
    - SSH secg-bastion-host
    - HTTP 0.0.0.0/0
1. Criar security group _secg-private-web-server_
    - SSH secg-bastion-host
    - HTTP secg-proxy-server
1. Criar EC2 _ec2-bastion-host_ dentro da _sn-public-0_
1. Criar EC2 _ec2-web-server_ dentro da _sn-private-0_
   - Bootstrap:
        ```
        #!/bin/bash
        yum update -y
        amazon-linux-extras enable php8.0
        yum install php httpd -y
        systemctl start httpd
        systemctl enable httpd
        echo '<?php echo "Server Address: " . $_SERVER["SERVER_ADDR"]; ?>' > /var/www/html/index.php
        ip=$(curl http://169.254.169.254/latest/meta-data/local-ipv4)
        mac=$(curl http://169.254.169.254/latest/meta-data/mac)
        nif_id=$(curl http://169.254.169.254/latest/meta-data/network/interfaces/macs/"$mac"/interface-id)
        new_ip="10.0.${ip:5:1}.50"
        echo "IP = $ip"
        echo "MAC = $mac"
        echo "NIF = $nif_id"
        echo "New IP = $new_ip"
        aws configure set aws_access_key_id {Acess key ID}
        aws configure set aws_secret_access_key {Secret acess key}
        aws configure set default.region {Region ID}
        aws ec2 assign-private-ip-addresses --network-interface-id "$nif_id" --private-ip-addresses "$new_ip"
        systemctl restart httpd
        systemctl restart network
        ```
        - Para  saber a versão mais recente do php: ```amazon-linux-extras | grep php```
1. Criar EC2 _ec2-proxy-server_ dentro da _sn-public-0_
    - Bootstrap:
        ```
        #!/bin/bash
        yum update -y
        yum install httpd -y
        a2enmod proxy
        a2enmod proxy_http
        a2enmod proxy_ajp
        a2enmod rewrite
        a2enmod deflate
        a2enmod headers
        a2enmod proxy_balancer
        a2enmod proxy_connect
        a2enmod proxy_html
        ip=$(curl http://169.254.169.254/latest/meta-data/local-ipv4)
        web_server_ip="10.0.$((${ip:5:1} + 1)).50"
        echo "Web server IP = $web_server_ip"
        echo -e "<VirtualHost *:*>\nProxyPreserveHost On\nProxyPass / http://$web_server_ip\nProxyPassReverse / http://$web_server_ip\nServerName localhost\n</VirtualHost>" > /etc/httpd/conf.d/proxy.conf
        systemctl restart httpd
        ```