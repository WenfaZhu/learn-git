# git 初始化操作

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