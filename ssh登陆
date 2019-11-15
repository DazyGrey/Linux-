从服务器A登陆到服务器B，我们可以用ssh密码登陆的方式
`ssh -p user@ip`
然后根据提示输入对应的密码。
但是，如果我们想登到服务器C，服务器D，服务器E.....，并随时可能在多台服务器上切换登陆。
难道我们每次都得输入user，ip，password吗？有没有更好更灵活的方式?

### 免密登陆
1.首先在服务器A上查看有没有密钥文件
`ls -l ~/.ssh/`
如果看到有id_rsa（私钥），id_rsa.pub（公钥）这两个文件，说明密钥文件已经存在，无需再生成（当然你可以更新密钥文件，不过不建议这么做，因为和这台主机关联的其它服务器配置都得修改一遍）

2.生成密钥文件
`ssh-keygen`

<img width="745" alt="屏幕快照 2019-11-15 上午6 14 48" src="https://user-images.githubusercontent.com/13326128/68900815-9fae8380-076f-11ea-97e0-0ee4506cd39d.png">

可以一直按Enter键跳过

3.将公钥复制到服务器B
`ssh-copy-id user@ip`

<img width="896" alt="image" src="https://user-images.githubusercontent.com/13326128/68901329-b30e1e80-0770-11ea-9531-f3ffdcd44f9d.png">

这一条命令的本质上是将服务器A上的公钥追加到服务器B的authorized_keys中。
所以你也可以这样做
`scp ~/.ssh/id_rsa.pub user@ip:~/.ssh/A.pub`
然后登陆到服务器B，将A.pub内容写入到authorized_keys中
`cat A.pub >> authorized_keys`

4.然后就可以ssh免密登陆服务器B了
`ssh user@ip`

> 哈哈哈，终于不用每次登陆都输入密码了😍。等等，我很懒，我都不想输入xxx@xxx，有没有更好的方式？

### 快速登陆
1.进入~/.ssh，编辑config
`vim config`
格式为：
Host xxx（自定义）
HostName xxx（服务器B地址，ip或域名）
Port xxx (服务器B端口）
User xxx（服务器B用户名）

Host xxx（自定义）
HostName xxx（服务器C地址，ip或域名）
Port xxx (服务器C端口）
User xxx（服务器C用户名）
...

<img width="295" alt="image" src="https://user-images.githubusercontent.com/13326128/68903159-2dd93880-0775-11ea-8e0e-3653d612331b.png">


2.实现快速登陆
`ssh Dee`

> OK，这样是不是方便了很多🤪
