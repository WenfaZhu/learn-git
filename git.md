# Git 的使用说明

### 配置全局信息

```shell
$ git config --global user.name "tanc"

$ git config --global user.email "gogotanc@163.com"
```


### 初始化和添加远程仓库

```shell
$ git init

$ git remote add origin git@github.com:gogotanc/learn-git.git

$ git pull origin master
```

### 生成公钥和 github 权限

```shell
$ ssh-keygen

$ cat ~/.ssh/id_rsa.pub
```

将打印出来的信息拷贝到 `github.com` `ssh` 管理里面就行了。

### 添加多个远程仓库

```shell
# 添加名为 coding 的远程仓库
$ git remote add coding master git@git.coding.net:gogotanc/tanc-blog.git

# 添加名为 origin 的远程仓库
$ git remote add origin master git@github.com:gogotanc/tanc-blog.git 
```

# 恢复删除的文件（commit操作之前）

```shell
$ git status
#=> 这里会显示删除的文件

$ git checkout <file>
#=> checkout命令后面加上需要恢复的文件，即可恢复删除的文件。
```



