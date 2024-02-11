# Install

`./setup_console.sh /usr/lib/jvm/jre-1.8.0`

# Uninstall

`./setup_console.sh /usr/lib/jvm/jre-1.8.0 -force -ru -uninstall -jcp -cpssl -rmsetting`

# Cleaning

```shell
rm -rf /etc/.java
rm -rf /usr/lib/jvm/jre-1.8.0/.systemPrefs
rm -rf /root/.java
rm -rf /home/user/.java
```
or for Windows registry
`HKEY_CURRENT_USER\Software\JavaSoft\Prefs\ru\/Crypto/Pro`

# Required license

https://www.cryptopro.ru/forum2/default.aspx?g=posts&t=15507<br />
`java -cp '*' ru.CryptoPro.JCP.tools.License -required`<br />

# Used license

`/usr/lib/jvm/jre-17/bin/java -cp '*' ru.CryptoPro.JCP.tools.License`<br />
`java -cp 'JCP.jar' ru.CryptoPro.JCP.tools.License`

Keys directory: /var/opt/cprocsp/keys/root or %userprofile%\AppData\Local\Crypto Pro\

# SMEV Adapter

After install SMEV Adapter need add to Java 8 ext directory /usr/lib/jvm/jre/lib/ext files xmlsec-1.4.5.jar and commons-logging-1.2.jar This need for correct singn working.
