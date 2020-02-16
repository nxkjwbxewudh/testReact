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

之后在md中引用图片地址【相关注意事项见2.2】



### 2.2 提交本地仓库时常见问题

多人合作开发的情况下，很有可能自己提交的时候远程仓库以及被其他人更新过了，就会出现下图所示的问题：

![](https://raw.githubusercontent.com/nxkjwbxewudh/testReact/master/images/xiong/pushfalse.PNG)

就需要我们先pull再push



####  git pull 与 git pull --rebase

```bash
git pull = git fetch + git merge

git pull --rebase = git fetch + git rebase
```



如果我们使用

```bash
$ git pull
```

完成之后，查看git log会有一条记录：

![](https://raw.githubusercontent.com/nxkjwbxewudh/testReact/master/images/xiong/mergebranch.PNG)

意思是git pull把origin pull下来，和自己本地的合并成一个新版本



如果使用

```bash
$ git pull --rebase
```

这会生成新版本，同时会废除之前本地提交的版本

**执行完git pull --rebase之后如果有合并冲突，使用以下三种方式处理这些冲突：**

- git rebase --abort 会放弃合并，回到rebase操作之前的状态，之前的提交的不会丢弃；

- git rebase --skip 则会将引起冲突的commits丢弃掉（慎用！！）；

- git rebase --continue 合并冲突，结合"git add 文件"命令一起用与修复冲突，提示开发者，一步一步地有没有解决冲突。（fix conflicts and then run “git rebase --continue”）

  

解决完冲突之后

```bash
$ git add .

$ git rebase --continue

$ git push
```

在任何时候，都可以用git rebase --abort参数来终止rebase的行动，并且mywork分支会回到rebase开始前的状态。



### 2.2 Github 图片引用问题

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

【即使这样，也还是要看运气。。。】



## 3 查看提交记录 + 版本回退

```bash
$ git log
```

如果出现下图情况：

![](https://raw.githubusercontent.com/nxkjwbxewudh/testReact/master/images/xiong/gitlog.PNG)

输入Q就行了

如果想要回退到之前的版本

```bash
git checkout [SHA1版本号]
/*版本回退*/
```





## 4 创建分支

```bash
$ git branch [分支号]
/*创建分支*/

$ git branch
/*查询是否创建成功*/

$ git checkout [分支号]
/*切换分支*/
```



如果这个分支把bug修复好了那么就可以跟主分支进行合并了
我们先切换到主分支

```bash
$ git checkout master

$ git merge [分支号]
/*然后在进行合并*/
```



要是以后不打算在使用这个分支了,接下来就可以把这个分支删除

```bash
git branch -D developer

git branch
/*确认一下是否删除成功*/
```



