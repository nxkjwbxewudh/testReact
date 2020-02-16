# 学习使用 Git 

## 0 前言

在Github上新建了一个项目用来测试



## 1 SSH Key

### 1.1 设置&查看自己的私钥

```bash
$ git config --global user.name   "用户名"
$ git config --global user.email  "邮箱"


$ cd ~/.ssh
$ ls
或者
$ ll
//看是否存在 id_rsa 和 id_rsa.pub文件，如果存在，说明已经有SSH Key


//如果没有SSH Key
$ ssh-keygen -t rsa -C "邮箱"


$ cat id_rsa.pub
//拷贝秘钥 ssh-rsa开头
```



![](https://raw.githubusercontent.com/nxkjwbxewudh/testReact/master/images/xiong/SSHkey.png)



## 2 clone项目 + 提交图片和md文档

进入相应文件夹，启动bash，克隆代码到本地

```bash
$ git clone [url]
```

将图片文件夹拷贝到images文件夹里

```bash
$ git add [文件夹名]
$ git commit -m [信息]
$ git push
```

之后在md中引用图片地址【相关注意事项见2.1】



### 2.1 Github 图片引用问题

github经常无法显示图片，解决办法：

在https://githubusercontent.com.ipaddress.com/网站搜索`avatars0.githubusercontent.com`

结果如图所示：

https://githubusercontent.com.ipaddress.com/avatars0.githubusercontent.com



![](https://raw.githubusercontent.com/nxkjwbxewudh/testReact/master/images/xiong/githubIP.PNG)

复制IP地址199.232.28.133



在C:\Windows\System32\drivers\etc路径下打开hosts文件

我用的notepad++打开的

添加

```
# GitHub Start 
# 199.232.28.133 raw.githubusercontent.com
# GitHub End
```



在本地编辑markdown的时候

引用https://raw.githubusercontent.com/[后面是图片路径] 的格式



成功显示图片