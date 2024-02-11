```shell
systemctl status firewalld
firewall-cmd --permanent --zone=public --add-service=http
firewall-cmd --permanent --zone=public --add-service=https
firewall-cmd --permanent --zone=public --add-service=telnet
firewall-cmd --permanent --zone=public --add-port=80/tcp --add-port=80/udp
firewall-cmd --permanent --zone=public --add-port=443/tcp --add-port=443/udp
firewall-cmd --permanent --zone=public --add-port=8080/tcp --add-port=8080/udp
firewall-cmd --reload
```
