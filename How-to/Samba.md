Jast add to end file /etc/samba/smb.conf new shares

```properties
[data1]
    comment = Samba on Ubuntu Server data1
    path = /mnt/data1
    public = yes
    writable = yes
    read only = no
    guest ok = yes
    guest account = root
    create mask = 0777
    directory mask = 0777
    force create mode = 0777
    force directory mode = 0777
    force user = latch
[data2]
    comment = Samba on Ubuntu Server data2
    path = /mnt/data2
    public = yes
    writable = yes
    read only = no
    guest ok = yes
    guest account = root
    create mask = 0777
    directory mask = 0777
    force create mode = 0777
    force directory mode = 0777
    force user = latch
```

force user - user on whose behalf the guest will act

More https://www.dmosk.ru/instruktions.php?object=samba-ubuntu

systemctl restart smbd
