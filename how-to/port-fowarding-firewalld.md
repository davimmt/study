## Port Forwarding with the Firewall

### The Scenario:
- Server1 10.0.1.10: The current web server
- Server2 10.0.1.20: The in-development web server
- Client1 10.0.1.11: For testing

### Configure Server1 so that incoming web traffic (port 80) requests from 10.0.1.0/24 are forwarded to Server2. Requests from all other sources should remain unforwarded.

### Client1
- Verify web content availability from Server1 and Server2:
  - ```curl 10.0.1.10```
  - ```curl 10.0.1.20```

### Server1
- Create a Zone, testing, to Handle the Subnet Requests
  - ```firewall-cmd --permanent --new-zone=testing```
  - ```firewall-cmd --reload```
- Add the subnet as the source:
  - ```firewall-cmd --permanent --zone=testing --add-source=10.0.1.0/24```
- Make sure http as a service is added and reload the configuration again to pick up these changes:
  - ```firewall-cmd --permanent --zone=testing --add-service=http```
  - ```firewall-cmd --reload```
- Enable Masquerading for the Zone, in order to permit forwarding:
  - ```firewall-cmd --permanent --zone=testing --add-masquerade```
  - ```firewall-cmd --reload```
- Add the Forwarding Rule to the Zone:
  - ```firewall-cmd --permanent --zone=testing --add-forward-port=port=80:proto=tcp:toport=80:toaddr=10.0.1.20```
  - ```firewall-cmd --reload```

### Client1
- Confirm the Port is Forwarded:
  - ```curl 10.0.1.10```