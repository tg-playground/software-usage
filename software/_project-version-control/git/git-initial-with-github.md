# Git Initial With GitHub

# git连接github

### 一、windows下git连接github

##### 1.windows安装msysgit

(1)download 
 mysygit又称git for windows

访问 https://git-for-windows.github.io/ ，选择自己电脑对应的版本，下载windows for git。 
 (2)install 
 双击安装，选择相应的安装目录。 
 一直点击下一步，选择默认配置就行。 
 最后完成安装。 
 (3)检验是否安装成功 
 在系统空白处，右键会有git bash选项，说明安装成功。

##### linux安装git

 

```
$ sudo apt-get install git
//检查安装是否成功
$ git --version
```

##### 2.git密钥

(0)设置本地git的user name和email

 

```
git config --global user.name "taogen"
git config --global user.email "taogenjia@gmail.com"
```

查看设置的name和email

 

```
git config user.name
git config user.email
```

(1)查看是否已经有了ssh密钥 
 cd ~/.ssh  //windows and linux  
 如果没有密钥则不会有此文件夹，如果有则备份后，删除

(2)生成密钥 
 右键，选择git bash，打开git。输入下面命令生成密钥。

 

```
$ ssh-keygen -t rsa -C "taogenjia@gmail.com"   
//"注释内容，一般为邮件地址"，生成的公钥后面会带上注释，这个注释用处，标识一下是你。  
Enter file in which to save the key (/c/Users/jiatg/.ssh/id_rsa):  
//提示输入一个钥匙的名称，不输入默认为：id_rsa (私钥） 和 id_rsa.pub（公钥），回车选择默认的  
//通常在企业里面一台服务器有很多人使用，因此默认的名称很可能已经有人使用了，所以这里可以输入一个你自己的名字为好。需要先创建一个空文件作为密钥文件。如填写D:/sshkey/taogen，需要在D盘创建目录sshkey，文件taogen。  
Enter passphrase (empty for no passphrase):  
Enter same passphrase again:  
//提示输入密码，一般不用密码，直接回车。  
```

默认公钥的路径：C:\Users\jiatg.ssh\id_rsa.pub 
 linux默认在~/.ssh/id_rsa.pub

(3)在github上添加ssh密钥的公钥（添加公钥id_rsa.pub） 
 登录github添加密钥公钥 
 访问http://www.github.com，登录github，点击右上角的 Settings—>SSH and GPG keys —> New SSH key 
 填写title 
 如win10_20170422 
 填写key 
 将本地生成的密钥公钥id_rsa.pub 文件内容复制到里面（key文本框中）， 点击 Add SSH key 就ok了

(4)本地测试连接是否成功 
 打开git bash ，输入 

 

```
$ ssh -T git@github.com
//如果在生成本地密钥时，添加了密码，那么执行上面命令时会要求输入密码。

出现，Hi xxx , You've successfully authenticated, but GitHub does not provide shell access. 说明你连接成功了

```

##### 3.

连接成功后，接下来可以clone本地关联的github仓库的代码，并且提交到该仓库中。 
 不连接的话，只能clone到本地查看代码，不能提交。

##### 4.其它问题

 

```
$ ssh -T git@github.com
Warning: Permanently added the RSA host key for IP address '192.30.255.113' to t he list of known hosts.
Hi TaogenJia! You've successfully authenticated, but GitHub does not provide she ll access.
$ ssh -T git@github.com
Warning: Permanently added the RSA host key for IP address '192.30.255.113' to the list of known hosts.
Hi TaogenJia! You've successfully authenticated, but GitHub does not provide shell access.
$ ssh -T git@github.com
Hi TaogenJia! You've successfully authenticated, but GitHub does not provide shell access.
```

