# WAMP setup

## Installation

1. Download [WAMP](http://www.wampserver.com/en/#download-wrapper)
2. Install WAMP
3. Startup WAMP Server
4. Ensure the apache server, mysql server and phpmyadmin has already been running.

## Troubleshooting

1. I cannot login the mysql server on phpmyadmin. How do I fix it?
    The default account of your mysql server will be "root" with no password encrypted. If you cannot successfully login, you may try [resetting your password](#reset-mysql-pw).

2. I cannot startup my apache server. What's going on?
    The apache server normally takes over the port 80 by default. Make sure your 80 port is not occupied by other applications. Then restart the apache service.

### Reset mysql pw

1. Stop wamp mysql service.
2. Edit the my.ini, add the below line(s) exactly after the heading section

```
skip-grant-tables
```

3. Start mysql services
4. Open mysql console from wamp->mysql
5. Input the below commands in the mysql Kernel.

```
UPDATE mysql.user SET Password=PASSWORD('<MY_NEW_PASSORD>') WHERE User='root';
FLUSH PRIVILEGES;
```

6. Stop wamp mysql service
7. Edit the my.ini, remove the below line(s) exactly after the heading section

```
skip-grant-tables
```

8. Start mysql services
9. Done.