## Tour-Project (https://yash-srivastav16.github.io/Tour-Project/)
Dockerfile written to build image and created containers using docker compose file. 
Tour &amp; Travel Project (Using HTML, CSS, php, Javascript).

## Dockerfile
FROM ubuntu<br>
RUN apt-get update \<br>
  && apt-get install -y apache2
<br>COPY . /var/www/html/
<br>CMD ["apachectl", "-D", "FOREGROUND"]
<br>EXPOSE 80

## Docker compose file
version: '2'<br>
services:<br>
  db:<br>
    image: mysql<br>
    container_name: mysql_db<br>
    restart: always<br>
    environment:<br>
      - MYSQL_ROOT_PASSWORD="secret"<br>
  web:<br>
    image: apache<br>
    build: ./web<br>
    depends_on:<br>
      - db<br>
    container_name: apache_web<br>
    restart: always<br>
    ports:<br>
      - 8080:80<br>

 ## How to run this project
 $docker compose up

 ## Docker containers
 $docker compose up<br>
[+] Building 0.0s (0/0)                                      docker:default<br>
[+] Running 2/0<br>
 ✔ Container mysql_db    Running                                       0.0s <br>
 ✔ Container apache_web  Running                                       0.0s <br>
Attaching to apache_web, mysql_db<br>
mysql_db    | 2024-03-14T15:49:05.583996Z 0 [System] [MY-015015] [Server] MySQL Server - start.<br>
mysql_db    | 2024-03-14T15:49:08.346819Z 0 [System] [MY-010116] [Server] /usr/sbin/mysqld (mysqld 8.3.0) starting as process 1<br>
mysql_db    | 2024-03-14T15:49:08.458534Z 1 [System] [MY-013576] [InnoDB] InnoDB initialization has started.<br>
mysql_db    | 2024-03-14T15:49:10.445691Z 1 [System] [MY-013577] [InnoDB] InnoDB initialization has ended.<br>
mysql_db    | 2024-03-14T15:49:12.081491Z 0 [Warning] [MY-010068] [Server] CA certificate ca.pem is self signed.<br>
mysql_db    | 2024-03-14T15:49:12.081593Z 0 [System] [MY-013602] [Server] Channel mysql_main configured to support TLS. Encrypted connections are now supported for this channel.
<br>mysql_db    | 2024-03-14T15:49:12.098605Z 0 [Warning] [MY-011810] [Server] Insecure configuration for --pid-file: Location '/var/run/mysqld' in the path is accessible to all OS users. Consider choosing a different directory. <br>

 ## How to access tour project<br>
 http://localhost:8080/
