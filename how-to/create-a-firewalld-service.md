## Create a Firewalld Service

### Use firewalld to create a new service, add that new service to permitted connections for the default zone, drop all traffic from an IPSet, and add a rich rule for traffic from a specific subnet.
### You will need to create an IPSet for the '10.0.1.12' and '192.168.1.0/24' IPS.

- Create a new service in firewalld:
  - ```firewall-cmd --permanent --new-service=jobsub```
- Set the description for the service:
  - ```firewall-cmd --permanent --service=jobsub --set-description="Job Submission"```
- The service's ports are: TCP 5671-5677:
  - ```firewall-cmd --permanent --service=jobsub --add-port=5671-5677/tcp```
- This service should be enabled for the default zone (public).
  - ```firewall-cmd --reload```
  - ```firewall-cmd --permanent --add-service=jobsub```
- Create an IPSet in firewalld:
  - ```firewall-cmd --permanent --new-ipset=kiosk --type=hash:ip```
- Add the specified IP addresses to the IPSet:
  - ```firewall-cmd --permanent --ipset=kiosk --add-entry=10.0.1.12```
  - ```firewall-cmd --permanent --ipset=kiosk --add-entry=192.168.1.0/24```
- Reload the firewall:
  - ```firewall-cmd --reload```
- Send all traffic from the kiosk IPSet to the drop zone:
  - ```firewall-cmd --permanent --zone=drop --add-source=ipset:kiosk```
- Add a rich rule to accept traffic from 10.0.1.0/24 to port 8080:
  - ```firewall-cmd --permanent --add-rich-rule='rule family=ipv4 source address=10.0.1.0/24 port port=8080 protocol=tcp accept'```