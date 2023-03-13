# 快速开发

> 运行后前往开发工具->代码生成器进行一键前后端代码生成

![](https://s3.bmp.ovh/imgs/2023/03/11/12ba90839fe89d37.jpg)


> 可以实时预览生成的代码逻辑
![](https://s3.bmp.ovh/imgs/2023/03/11/d373c4d90e81b7ac.jpg)

![](https://s3.bmp.ovh/imgs/2023/03/12/d6e6b044fc24e359.png)


## 命令行生成

```phpregexp
#执行
# -t [表名] & --table=[表名]  【必填】
# -bm [父级菜单id] & --belong_menu_id=[父级菜单id]  【不填默认为业务管理子菜单】
# -mn [应用模块名] & --module_name=[应用模块名]  【不填默认为业务管理子菜单】
# -m [生成菜单名] & --menu_name=[生成菜单名]  【不填默认取表描述】
# -gm [生成的功能按钮] & --generate_menus=[生成的功能按钮]  【不填默认为'save,update,read,delete,recycle,changeStatus,numberOperation,import,export'所有】


php webman quick:gen:table -t test 
php webman quick:gen:table --table=test 
```

> 运行命令行后进入目录

![](https://s3.bmp.ovh/imgs/2023/03/13/784ba2a303a658ad.jpg)

```shell
cd D:\home\php\plugin\stone\app
#复制下面的文件到`plugin/stone/app`下，启动`webman`即可直接接口访问



```

![](https://s3.bmp.ovh/imgs/2023/03/13/e9c9c30436ae8584.jpg)

> 注意：默认所有接口都会存在登录校验，您可以在控制器内数组`$noNeedLogin`设置不需要登录校验直接访问。

![](https://s3.bmp.ovh/imgs/2023/03/13/4670430793e3b290.jpg)


>请求接口结果
![](https://s3.bmp.ovh/imgs/2023/03/13/2c2c5eb8914aa770.jpg)

。。未完待续