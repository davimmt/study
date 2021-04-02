## Permitting and Blocking Traffic with the IPTables Firewall

### Configure Server1 (10.0.1.10) so that it only permits HTTP connections (port 80) from Client1 (10.0.1.11).
 
- Verify that a firewall is running:
  - ```systemctl status iptables```
- Verify that the host listening on port 80:
  - ```ss -lntp | grep :80```

### Verify that port 80 is blocked, and add a rule to permit traffic coming from 10.0.1.11

- From Client1 (10.0.1.11), try to curl 10.0.1.10:
  - ```curl 10.0.1.10```
- You'll need to add a rule on Server1 to permit the traffic:
  - ```iptables -I INPUT -p tcp -s 10.0.1.11 --dport 80 -j ACCEPT```
- Test from Client1 again, and also with Client2. If Client1 is successful and Client2 isn't, save your existing chain with:
  - ```service iptables save```