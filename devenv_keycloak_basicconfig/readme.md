
# keycloak & apache basic congfiguration useing docker

# How to use

Run these commands and start up the containers.

```
cd devenv_keycloak_basicconfig
docker-compose up -d --build
```

Set the domain name in `hosts` file

```
127.0.0.1 apache.example.com
127.0.0.1 keycloak.example.com
```

Apache http server configuration is like this  
Domain: apache.example.com  
Sample private page: http(s)://apache.example.com/private  
Sample public page: http(s)://apache.example.com/public  
Port number: 80(http) / 443(https)  

Keycloak server configuration is like this  
Domain: keycloak.example.com  
Admin console(http): http://keycloak.example.com:8080/auth/admin  
Admin console(https): https://keycloak.example.com:8443/auth/admin  
Port number: 8080(http) / 8443(https)  

You can login as admin using  
admin ID : `admin`  
admin PW : `admin`  

Initially, these users have already been made in `demorealm`  

(ID/PW/EMAIL)  
user01/user01/user01@example.com  
.  
.  
.  
user05/user05/user05@example.com

# End

```
docker-compose down
```


# Enter the containers

docker exec -it -u root dev_httpd /bin/bash
docker exec -it -u root dev_keycloak /bin/bash

or

docker-compose exec httpd /bin/bash
docker-compose exec keycloak /bin/bash


