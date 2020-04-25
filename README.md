# spring-mvc-ssl
Example of implementing SSL with spring boot

There are variosu approaches for implementing SSL with Spring Boot.
Refer below for implementing a self-signed SSL certificate for you rSpring Boot application.

1. Use the "keytool" application, that comes with JDK, to generate JKS keystore. Leet it be keystore_jks.jks
2. We can use the same tool "keytool" again to generate the PKCS12 keystore, let it be keystore_pkcs.jks. PKCS12 uses industry standard where as JKS uses a proprietory format.
3. For PKCS12 keystore the key-store-password and key-password must be same, where as for JKS keystore they may be different if we want.
4. In the "application.yml" resources file under "src/main/resources" folder provide the key-store details under server.ssl block, i.e  server.ssl.key-store, server.ssl.key-store-password, server.ssl.key-store-type, server.ssl.key-alias, server.ssl.key-password

<I>
<pre>
server:
  ssl:
    key-store: src/main/resources/keystore_jks.jks
    key-store-password: my_password1
    key-store-type: PKCS12
    key-alias: my_alias
    key-password: my_password2
</pre>
</I>

<I>
<pre>
server:
  ssl:
    key-store: src/main/resources/keystore_pkcs.jks
    key-store-password: my_password2
    key-store-type: PKCS12
    key-alias: my_alias
    key-password: my_password2
</pre>
</I>


For the keystore path we can use `classpath:keystore_jks.jks` but I used the phycal path to the keystor i.e. esrc/main/resources/keystore.jks based on the error message printed.
