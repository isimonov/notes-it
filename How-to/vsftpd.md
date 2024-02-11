vsftpd (Very Secure FTP Daemon)

Configuration for anonymous users, not system.

/etc/vsftpd.conf

```properties
anonymous_enable=YES
local_enable=NO
write_enable=YES

anon_root=/var/ftp/
no_anon_password=YES
hide_ids=YES

nopriv_user=ftp
allow_writeable_chroot=YES
anon_world_readable_only=NO
anon_upload_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES

# Need opening the Firewall: sudo ufw status
pasv_min_port=40000
pasv_max_port=50000
```

```bash
mkdir -p /var/ftp/pub
chown ftp:ftp /var/ftp/pub
chmod 777 /var/ftp/pub
echo "vsftpd test file" | tee /var/ftp/pub/test.txt
```

```bash
mkdir -p /var/ftp/html/
mount --bind /var/ftp/html/ /var/www/html
mcedit /etc/fstab
/var/ftp/html   /var/www/html    none    bind    0       0
```

```bash
systemctl start vsftpd
systemctl enable vsftpd
```
