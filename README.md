# Docker LNMP  环境一键部署
## 安装
 ```
git clone https://github.com/snakelis/docker-php.git
cd docker-php 
docker-compose build // 等待编译
```
## 创建挂载项目
    //创建测试项目 
     D:/web/htdocs/demo
     
     //创建测试文件
     D:/web/htdocs/demo/index.php
     
     //创建数据库目录
     D:/web/data
     
     //创建日志文件
     D:/web/log/nginx
     
## 启动服务
```
// 启动服务 nginx mysql redis memcache
docker-compose up -d 
```
## 测试
```
访问 localhost //可以看到 phpinfo 信息
```


