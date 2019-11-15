# docker-compose-lnmp

## 相关命令

```bash
#!/bin/bash
docker run -d -v D:\Web\log\mysql:/var/log/mysql/ -v D:\Web\conf\mysql:/etc/mysql/ -p 3306:3306 -e MYSQL_ROOT_PASSWORD=ohyeah1990 --name mysql mysql:5.7 --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
docker exec -ti mysql /bin/bash

启动fpm
docker run -d -v D:\Web\conf\php73:/usr/local/etc -v D:\Web\www:/var/www -v D:\Web\log\php73:/usr/local/var/log -p 9000:9000 --link mysql:mysql --link redis:redis --name php73 php:7.3-fpm
docker exec -ti php73 /bin/bash

启动nginx
docker run -d -v D:\Web\conf\nginx:/etc/nginx -v D:\Web\log\nginx:/usr/local/var/log -v D:\Web\www:/var/www -p 80:80 --link php73:phpfpm --name nginx nginx:1.16
docker exec -ti nginx /bin/bash

启动redis
docker run --name redis -d -p 6379:6379 redis redis-server --appendonly yes
docker exec -ti redis /bin/bash
```
