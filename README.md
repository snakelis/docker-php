# Docker LNMP  环境一键部署

## 安装
 ```
git clone https://github.com/snakelis/docker-php.git
cd docker-php
```

## 根据服务器切换分支 windows:master 分支,linux ：linux 分支
 
    // 等待编译    
    docker-compose build 

## 创建挂载项目
```

//创建测试项目目录
mkdir -p /web/htdocs/demo

// 创建数据目录
mkdir -p /web/data

// 创建日志目录
mkdir -p /web/log/nginx

// 创建测试文件
tee /web/htdocs/demo/index.php <<<- 'EOF'
<?php
     phpinfo();
?>
EOF

```
## 启动服务
```
// 启动服务 nginx mysql redis memcache
docker-compose up -d 
```
## 测试
```
curl localhost //可以看到 phpinfo 信息
```


