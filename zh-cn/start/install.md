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

## 后端配置
> 复制 `.env.templete` 到 `.env` 文件配置

```shell
 #进入项目源码根目录
 cp .env.templete .env
```

> 按配置的信息启动并创建mysql 数据库 `development_stone_db` & 启动redis服务器 

## 前端配置
> 复制 `.env.templete` 到 `.env` 文件配置

```shell
 cd stone-ui
 cp .env.templete .env
```



## 一键初始化后端数据库

修改`phinx.php`文件
[phinx 官网](https://book.cakephp.org/phinx/0/en/contents.html)

```shell

#配置正确的数据库环境。
<?php

return
[
    'paths' => [
        "migrations" => "plugin/stone/database/migrations",
        "seeds"      => "plugin/stone/database/seeds"
    ],
    'environments' => [
        'default_migration_table' => 'phinx_migrations',
        'default_environment' => 'development',
        'production' => [
            'adapter' => 'mysql',
            'host' => 'localhost',
            'name' => 'production_db',
            'user' => 'root',
            'pass' => '',
            'port' => '3306',
            'charset' => 'utf8mb4',
        ],
        'development' => [
            'adapter' => 'mysql',
            'host' => 'localhost',
            'name' => 'development_stone_db1',
            'user' => 'root',
            'pass' => 'root',
            'port' => '3306',
            'charset' => 'utf8mb4',
        ],
        'testing' => [
            'adapter' => 'mysql',
            'host' => 'localhost',
            'name' => 'testing_db',
            'user' => 'root',
            'pass' => '',
            'port' => '3306',
            'charset' => 'utf8mb4',
        ]
    ],
    'version_order' => 'creation'
];



```

```shell
cd ./stone

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