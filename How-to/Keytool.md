Java system trusted cacerts storage 

```shell
# add sert
keytool -import -trustcacerts -keystore C:\Programs\jdk-17\lib\security\cacerts -storepass changeit \
        -noprompt -alias mycert -file certificate.cer
# remove cert
keytool -delete -alias mycert -keystore C:\Programs\jdk-17\lib\security\cacerts -storepass changeit
```

Create keystore with key-cert pair and then delete them (alias)

```shell
keytool -genkey -alias mydomain -keyalg RSA -keystore keystore.jks -storepass 123456
keytool -delete -alias mydomain -keystore keystore.jks
```
