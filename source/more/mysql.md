# MySQL
```
[mysqld]
ssl-ca=/etc/mysql-ssl/ca-cert.pem
ssl-cert=/etc/mysql-ssl/server-cert.pem
ssl-key=/etc/mysql-ssl/server-key.pem
ssl-cipher=AES128+EECDH:AES128+EDH
```
## replication
```
GRANT REPLICATION SLAVE ON *.* to ‘repl’@’%’ REQUIRE SSL;
STOP SLAVE;
CHANGE MASTER MASTER_SSL=1,
MASTER_SSL_CA=’/etc/mysql-ssl/ca-cert.pem’,
MASTER_SSL_CERT=’/etc/mysql-ssl/client-cert.pem’,
MASTER_SSL_KEY=’/etc/mysql-ssl/client-key.pem';
SHOW SLAVE STATUS\G;
START SLAVE;
SHOW SLAVE STATUS\G;
```
