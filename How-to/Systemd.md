# /opt/service-name/service-name.service

```properties
[Unit]
Description=sm-crypto service
After=syslog.target
After=network.target

[Service]
WorkingDirectory=/opt/service-name
ExecStart=/usr/lib/jvm/jre-17-openjdk/bin/java -jar /opt/service-name/service-name.jar
Restart=always
StandardOutput=syslog
StandardError=syslog
SyslogIdentifier=sm-crypto
User=root
Type=simple

[Install]
WantedBy=multi-user.target
```
# Create symlink

`ln -s /opt/service-name/service-name.service /etc/systemd/system/service-name.service`
# Start service

`systemctl start service-name.service`
# Enable start of boot

`systemctl enable service-name.service`
# Service log

```shell
journalctl -u service-name -n 50
or
journalctl -u service-name --since "5 minute ago"
or
journalctl -u service-name -f
```
