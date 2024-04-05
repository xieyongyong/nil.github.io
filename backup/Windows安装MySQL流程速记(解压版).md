### _前言_
这里用的是MySQL5.7 windows的zip版本。
对zip解压版独有好感，因为zip版本对系统依赖小，不会向注册表写入各种东西，也不会在系统目录下面放一下执行文件。
因为方便用脚本命令部署（命令也没有很多）,可以用来做一键部署的程序。

### **1.下载**
官方的下载地址如下：https://dev.mysql.com/downloads/mysql/

### **2.安装**
将下载好的压缩包解压到自己要安装的文件夹下
**_注意： 解压存放的目录路径名称不能包含中文_**

> 解压后的文件夹不包含data文件夹和my.ini配置文件

![image](https://github.com/xieyongyong/xieyongyong.github.io/assets/55351400/f49266a0-152c-4fd8-9c32-ce3d37e97262)

**_2.1接下来我们创建一个my.ini文件，打开进行配置_**

```
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8

[mysqld]
#设置3306端口
port = 3306
# 设置mysql的安装目录（要配置自己的路径）
basedir=D:\mysql-5.7.32-winx64
# 设置mysql数据库的数据的存放目录（要配置自己的路径）
datadir=D:\mysql-5.7.32-winx64\data       
# 允许最大连接数
max_connections=200
# 服务端使用的字符集默认为8比特编码的latin1字符集
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
```

**_2.2保存my.ini文件后，使用cmd管理员模式进入MySQL的bin目录下_**（**管理员**模式！！！）

![image](https://github.com/xieyongyong/xieyongyong.github.io/assets/55351400/a75143fe-391e-4b8b-b1d2-7b2bb58502c0)

**_2.3初始化_**

`mysqld --initialize-insecure
或
mysqld --initialize
#初始化没有失败的话，会在data目录下面有个“机器名字.er的日志文件，启动的时候会随机生成一个密码。
#最后一句"A temporary password is generated for root@localhost:pXHc//f?04u2",后面的"pXHc//f?o4u2"就是随机密码，这个密码是临时密码，启动后进去的时候要修改。
`

**_2.4安装服务_**

`mysqld -install`
若出现Service successfully installed，证明安装成功

**_2.5启动服务_**

`net start mysql`

**_2.6修改密码_**

`mysqladmin -uroot password root(root为你要修改的密码)`


### _3.可能出现的异常_

**3.1 缺少dll文件**
![image](https://github.com/xieyongyong/xieyongyong.github.io/assets/55351400/16574371-fbf4-4c9a-b5c6-09d0f4620b0f)

**_解决方式：_**
由于电脑系统缺少部分配置文件引起的，安装  vcredist  下载相关配置文件即可。
安装https://www.ghxi.com/visualcppredist.html
或
x86:https://aka.ms/vs/17/release/vc_redist.x86.exe
x64:https://aka.ms/vs/17/release/vc_redist.x64.exe
或
官网地址 (vcredist) ：[Download Visual C++ Redistributable Packages for Visual Studio 2013 from Official Microsoft Download Center](https://www.microsoft.com/zh-CN/download/details.aspx?id=40784)

**3.2 一些其他命令**

```
#跳过密码（mysqld标签下）
skip-grant-tables

#刷新权限
flush privileges 

#启动/停止mysql服务
net stop mysql
net start mysql

#删除mysql服务
sc delete mysql
```