# Github 不显示图片问题





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

引用https://raw.githubusercontent.com/[后面是图片路径]的格式



成功显示图片

【即使这样，也还是要看运气。。。】