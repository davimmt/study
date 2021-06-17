## Topologia
![](../img//setup-aws-bastion-host-topology/topology.png)

## Passo-a-passo
1. Criar VPC
   - Adicionar CIDRs necessários
1. Criar IG; alocar na VPC; adicionar na Route Table
1. Criar public subnet 1 e private subnet 1
1. Criar EC2 (web server 1) dentro da private subnet 1
   - Bootstrap:
        ```
        #!/bin/bash
        yum update -y
        yum install httpd -y
        systemctl start httpd
        systemctl enable httpd
        echo "dataRain 01" > /var/www/html/index.html
        ```
    - Chek output: ```/var/log/cloud-init-output.log```
1. Criar EC2 (bastion host 1) dentro da public subnet 1
    - Bootstrap:
        ```
        #!/bin/bash
        yum update -y
        yum install firewalld -y
        systemctl start firewalld
        systemctl enable firewalld
        firewall-cmd --permanent --new-zone=web-server-01
        firewall-cmd --reload
        firewall-cmd --set-default-zone=web-server-01
        firewall-cmd --reload
        firewall-cmd --permanent --add-port=80/tcp
        firewall-cmd --permanent --add-service=http
        firewall-cmd --permanent --add-masquerade
        firewall-cmd --permanent --add-source=<ec2_web_server_1_ip/mask>
        firewall-cmd --permanent --add-forward-port=port=80:proto=tcp:toport=80:toaddr=<ec2_web_server_1_ip>
        firewall-cmd --reload
        ```
    - Talvez seja necessário: ```iptables -A INPUT -p tcp --dport 80 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT```
1. Criar security group private-web-server
    - SSH <bastion_host_ip/mask>
    - HTTP <bastion_host_ip/mask>
1. Criar NACL acl-private-subnet
    - INPUT
        - SSH <bastion_host_ip/mask> ALLOW
        - HTTP <bastion_host_ip/mask> ALLOW
        - \* All DENY
    - OUTPUT (fora as acima, adicionar saída efêmera)
      - Custom TCP 32768 - 65535 <bastion_host_ip/mask> ALLOW