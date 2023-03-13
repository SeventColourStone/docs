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


。。未完待续