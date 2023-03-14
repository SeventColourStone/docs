# 连接池


套用 [walkor 大佬在workmaner 社区给兄弟们的一段释义](https://www.workerman.net/q/5389)：

![](https://s3.bmp.ovh/imgs/2023/03/14/9d4bc88db5f00896.png)


## smproxy 使用

> 使用外部连接池中间件[smproxy](https://smproxy.louislivi.com/#/)


docker 启动：


创建目录：`/data/webpage/smproxy/conf` 、`/data/webpage/smproxy/logs` 并赋予写入权限。

编辑配置:`database.json`、`server.json`内容。


```shell
//database.json {
  "database": {
    "account": {
      "root": {
        "user": "root",
        "password": "#ascfsa3sasfagsa!"
      }
    },
    "serverInfo": {
      "server1": {
        "write": {
          "host": ["172.16.3.113"],
          "port": 3306,
          "timeout": 2,
          "account": "root"
        }
      }
    },
    "databases": {
      "oms_saas": {//主库
        "serverInfo": "server1",
        "startConns": "swoole_cpu_num()*2",
        "maxSpareConns": "swoole_cpu_num()*2",
        "maxSpareExp": 3600,
        "maxConns": "swoole_cpu_num()*2",
        "charset": "utf8mb4"
      },
      "oms_saas_business": {//业务库
        "serverInfo": "server1",
        "startConns": "swoole_cpu_num()*2",
        "maxSpareConns": "swoole_cpu_num()*2",
        "maxSpareExp": 3600,
        "maxConns": "swoole_cpu_num()*2",
        "charset": "utf8mb4"
      }
    }
  }
}
 server.json
 
{
  "server": {
    "user": "root",
    "password": "12345677",
    "charset": "utf8mb4",
    "host": "0.0.0.0",
    "port": "3366",
    "mode": "SWOOLE_PROCESS",
    "sock_type": "SWOOLE_SOCK_TCP",
    "logs": {
      "open":true,
      "config": {
        "system": {
          "log_path": "ROOT/logs",
          "log_file": "system.log",
          "format": "Y/m/d"
        },
        "mysql": {
          "log_path": "ROOT/logs",
          "log_file": "mysql.log",
          "format": "Y/m/d"
        }
      }
    },
    "swoole": {
      "worker_num": "swoole_cpu_num()",
      "max_coro_num": 6000,
      "open_tcp_nodelay": true,
      "daemonize": true,
      "heartbeat_check_interval": 60,
      "heartbeat_idle_time": 600,
      "reload_async": true,
      "log_file": "ROOT/logs/swoole.log",
      "pid_file": "ROOT/logs/pid/server.pid"
    },
    "swoole_client_setting": {
      "package_max_length": 16777215
    },
    "swoole_client_sock_setting": {
      "sock_type": "SWOOLE_SOCK_TCP"
    }
  }
}

```

```shell
//拉取镜像
docker pull louislivi/smproxy
 
//创建容器
docker create -v /data/webpage/smproxy/conf:/usr/local/smproxy/conf -v /data/webpage/smproxy/logs:/usr/local/smproxy/logs -p 3366:3366 --name SMProxy louislivi/smproxy
 
//查看命令
docker exec SMProxy /usr/local/smproxy/SMProxy
 
//启动容器
docker start SMProxy 
```

> 修改业务库配置信息，使用smproxy.server.json 的账号信息。


# Q&A

> Q:SMProxy@Reach max connections! Cann't pending fetch!
 
> A:适当增加maxSpareConns或maxConns,或增加database.json中的timeout项。

具体可以参考 [常见问题](https://smproxy.louislivi.com/#/README?id=%e5%b8%b8%e8%a7%81%e9%97%ae%e9%a2%98)