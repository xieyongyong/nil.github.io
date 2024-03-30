首先声明，Windows系统如果用中文名作为路径的话，会导致很多不必要的麻烦（例如某些软件运行时会因为中文转码后找不到路径），因此，用户名最好使用英文，即C:\Users下的文件夹名，例如下图为admin

![image](https://github.com/xieyongyong/xieyongyong.github.io/assets/55351400/2a84ba03-52e2-4e53-bb02-19bdafe6f450)
**那么如果我们已经用了很长时间了，但是又不想重装系统该怎么办呢？**

接下来进入正题（干货！）：

1. 以管理员身份打开cmd（桌面左下角搜索框搜索cmd，选择以管理员身份打开，一定要用管理员身份！）， 然后输入引号内代码“net user administrator /active:yes”，回车，这时候会发现它提示成功，我们已经可以登录管理员（administrator）账号了。
![image](https://github.com/xieyongyong/xieyongyong.github.io/assets/55351400/fc9ddc93-a053-46ae-aeb3-4df31ea9b03b)
![image](https://github.com/xieyongyong/xieyongyong.github.io/assets/55351400/3dd238d3-9b39-4626-b637-a8ba353dd2c0)
 2. 重启电脑，会发现多了一个administrator账户，选择这个账户登录（这时会有引导你进入系统的动画，根据它的步骤走就行），进入系统后打开“此电脑”，打开C盘，再打开“用户”文件夹，找到中文名称的那个文件夹(你想修改的中文文件夹) 

> 如果修改时提示文件夹正在被使用，一定要注销掉想要修改的那个账户

 3. 使用快捷键“win+R”（也就是Alt左边的那个键和R键一起摁），随后会出现一个小窗口，在里面输入regedit后点击确认，我们就打开了注册表
 然后在最上面的搜索框中输入：
 计算机\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList
![image](https://github.com/xieyongyong/xieyongyong.github.io/assets/55351400/60689f03-e7fd-4fc1-9e7e-6347ce65dde8)

 4.  修改用户名
![image](https://github.com/xieyongyong/xieyongyong.github.io/assets/55351400/81c50c44-81bb-40ba-80a6-06d974e06206)
5. 再次重启电脑，登录我们原来的那个账户，打开“此电脑”，打开C盘，双击“用户”文件夹，此时我们会发现原来那个中文名的文件夹已经被我们成功重命名了。然后我们再次以管理员身份打开cmd，然后我们再输入下面引号内的代码：“net user administrator /active:no”，这样做的目的是关闭我们第一步所打开的administrator账户，这样以后我们以后开机就不会出现两个账户了
![image](https://github.com/xieyongyong/xieyongyong.github.io/assets/55351400/0595264f-8a29-4f3a-bd39-73c90ac391c8)



