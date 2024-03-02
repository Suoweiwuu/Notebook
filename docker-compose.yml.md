# docker-compose.yml

```
version: '3'

services:
  mysql_8.0:
    image: mysql:8.0
    restart: always
    container_name: "mysql_8.0"
    environment:
      - MYSQL_DATABASE=generatedata
      - MYSQL_PASSWORD=Qwer1234.
      - MYSQL_ROOT_PASSWORD=Qwer1234.  
    ports:
      - 3306:3306
    volumes:
      - /data/middleware/mysql/mysql8.0/my.cnf:/root/.my.cnf
      - /data/middleware/mysql/mysql8.0/conf.d:/etc/mysql/conf.d
      - /data/middleware/mysql/mysql8.0/logs:/var/log/mysql
      - /data/middleware/mysql/mysql8.0/initdb.d:/docker-entrypoint-initdb.d
      - /data/middleware/mysql/mysql8.0/common:/common
      - /data/middleware/mysql/mysql8.0/auto-generate:/auto-generate

  mysql_5.7:
    image: mysql:5.7
    restart: always
    container_name: "mysql_5.7"
    environment:
      - MYSQL_DATABASE=test
      - MYSQL_PASSWORD=Qwer1234.
      - MYSQL_ROOT_PASSWORD=Qwer1234.
    ports:
      - 3307:3306
    volumes:
      - /data/middleware/mysql_5.7/my.cnf:/root/.my.cnf
      - /data/middleware/mysql_5.7/conf.d:/etc/mysql/conf.d
      - /data/middleware/mysql_5.7/logs:/var/log/mysql
      - /data/middleware/mysql_5.7/initdb.d:/docker-entrypoint-initdb.d
      - /data/middleware/mysql_5.7/common:/common
      - /data/middleware/mysql_5.7/auto-generate:/auto-generate

  redis:
     image: redis:6.0
     restart: always
     container_name: redis
     ports:
       - "5070:6379"
     volumes:
       - /data/middleware/redis/conf:/etc/redis/conf 
       - /data/middleware/redis/data:/data      
     command: redis-server /etc/redis/conf/redis.conf 
     privileged: true
```
