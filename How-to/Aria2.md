# Aria2 config: /etc/aria2.daemon

```properties
##main
daemon=true
dir=/mnt/data1/Downloads
file-allocation=falloc
listen-port=6801
dht-listen-port=6801

##logging
##log=/var/log/aria2.log
##console-log-level=warn
##log-level=notice

##remote
enable-rpc=true
rpc-allow-origin-all=true
rpc-listen-all=true
##sudo openssl rand -base64 32
rpc-secret=3Cg4pwFqITqfijVe+C4aLYXE3E2opbQwxNv0VJRSPvQ=

##session
save-session=/var/aria2/aria2.session
input-file=/var/aria2/aria2.session
force-save=true
continue=true
save-session-interval=10

##downloads
max-overall-upload-limit=256K
```
# Systemd service: /lib/systemd/system/aria2.service

```properties
[Unit]
Description=Aria2c download manager
Requires=network.target
After=dhcpcd.service

[Service]
Type=forking
User=latch
ExecStart=/usr/bin/aria2c --conf-path=/etc/aria2.daemon
WorkingDirectory=/mnt/data1/Downloads
ExecReload=/usr/bin/kill -HUP $MAINPID
RestartSec=1min
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

touch /var/aria2/aria2.session
```shell
systemctl daemon-reload
systemctl start aria2
systemctl status aria2
systemctl enable aria2
```
