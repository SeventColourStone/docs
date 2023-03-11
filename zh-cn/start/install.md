# 安装


## 快速安装

> 拉取 github 代码库

```shell
git clone git@github.com:SeventColourStone/StoneAdmin.git
```

## 安装前后端代码库依赖包
```shell
#后端
cd ./stoneAdmin
composer install

#前端
cd ./stoneAdmin/stone-ui
npm i


```

> 修改后端 `.env` 文件配置

```shell
vim ./stoneAdmin/.env
```
```shell
#app相关配置
#APP_NAME=StoneAdmin
#APP_ENV=local
WEB_LISTEN=8788
WEBSOCKET_LISTEN=3132
WEBSOCKET_API_LISTEN=3233

#本地db相关配置
DB_CONNECTION=mysql
DB_DRIVER =mysql
DB_HOST=您的数据库链接
DB_PORT=您的数据库链接端口
DB_DATABASE=stone
DB_USERNAME=stone
DB_PASSWORD=您的数据库密码
DB_CHARSET = utf8mb4
DB_COLLATION = utf8mb4_general_ci
DB_PREFIX = stone_



#redis相关
REDIS_HOST=您的redis链接
REDIS_PASSWORD=您的redis密码
REDIS_PORT=6379
REDIS_DB = 1
REDIS_QUEUE_DB = 14


#最高权限人id
SUPER_ADMIN = 16128263327904
#角色id
ADMIN_ROLE = 16128263327905

#代码生成器生成目录
GENCODE_PATH = D:/home
```

> 修改前端 `.env` 文件配置

```shell
vim ./stoneAdmin/stone-ui/.env
```
```shell
# 基础url
#VUE_APP_URL=http://127.0.0.1:9501
VUE_APP_URL=http://127.0.0.1:8788

# 代理API前缀
VUE_APP_API=/api

# WebSocket url
VUE_APP_WS_URL=ws://127.0.0.1:3132

VUE_APP_WS_AUTH_URL=/api/plugin/webman/push/auth

```


## 一键初始化后端数据库

修改`phinx.php`文件
[phinx 官网](https://book.cakephp.org/phinx/0/en/contents.html) 

```shell
<?php

return
[
    'paths' => [
        'migrations' => '%%PHINX_CONFIG_DIR%%/db/migrations',
        'seeds' => '%%PHINX_CONFIG_DIR%%/db/seeds'
    ],
    'environments' => [
        'default_migration_table' => 'phinxlog',
        'default_environment' => 'development',
        'production' => [
            'adapter' => 'mysql',
            'host' => 'localhost',
            'name' => 'production_db',
            'user' => 'root',
            'pass' => '',
            'port' => '3306',
            'charset' => 'utf8',
        ],
        'development' => [
            'adapter' => 'mysql',
            'host' => 'localhost',
            'name' => 'development_db',
            'user' => 'root',
            'pass' => '',
            'port' => '3306',
            'charset' => 'utf8',
        ],
        'testing' => [
            'adapter' => 'mysql',
            'host' => 'localhost',
            'name' => 'testing_db',
            'user' => 'root',
            'pass' => '',
            'port' => '3306',
            'charset' => 'utf8',
        ]
    ],
    'version_order' => 'creation'
];


```

```shell
cd ./stoneAdmin

#创建数据库

#运行生成基础表结构
vendor/bin/phinx migrate

#运行生成数据库数据
php vendor/bin/phinx seed:run
```

![](https://s3.bmp.ovh/imgs/2023/03/11/041bf76588ec400f.jpg)
![](https://s3.bmp.ovh/imgs/2023/03/11/8c13f098716758d4.png)

> 当出现异常时请手动检查自己创建的数据库编码集是否跟文件 `database/migrations/20220617101508_init_stone.php` 的`encoding` 与 `collation` 一致


## 启动

```shell
#后端启动
cd ./stoneAdmin
php webman start 

#前端启动
cd ./stoneAdmin/stone-ui
npm run dev

```

# 体验

```shell
#浏览器打开
#前端
http://localhost:2800/

用户名：superAdmin
密码：admin123
```