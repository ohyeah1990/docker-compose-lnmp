# docker-compose-lnmp

## 使用步骤

- 安装最新版本docker
- 直接git clone 在本地目录
- 在目录下执行docker-compose up -d 开箱即用
- 安装docker kitematic 或 docker portainer搭配使用

## 相关命令

```bash
#!/bin/bash

进入mysql
docker exec -ti mysql /bin/bash

进入fpm
docker exec -ti php73 /bin/bash

进入nginx
docker exec -ti nginx /bin/bash

进入redis
docker exec -ti redis /bin/bash
```

### 待完善，好心给个star,谢谢啦！后续有空出个docker swarm
