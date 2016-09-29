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

```shell
$ git ls-files -d | xargs -i git checkout {}
#=> 恢复多个文件
```

### 设置相关

`git` 设置关闭自动换行

```shell
$ git config --global core.autocrlf false 
```

为了保证文件的换行符是以安全的方法，避免 `windows` 与 `unix` 的换行符混用的情况，最好也加上这么一句。 

```shell
$ git config --global core.safecrlf true
```

`git` 变更项目地址

```shell
git remote set-url origin git@192.168.6.70:res_dev_group/test.git 
git remote -v
```

查看某个文件的修改历史

```shell
$ git log --pretty=oneline 文件名 # 显示修改历史 
$ git show 356f6def9d3fb7f3b9032ff5aa4b9110d4cca87e # 查看更改
```

查看配置列表

```shell
$ git config --list
```

### 版本回退

版本回退用于线上系统出现问题后恢复旧版本的操作，回退到的版本。

```shell
$ git reset --hard 248cba8e77231601d1189e3576dc096c8986ae51 
```

回退的是所有文件，如果后悔回退可以 `git pull` 就可以了。

### 历史版本对比

查看日志 `git log`

查看某一历史版本的提交内容，这里能看到版本的详细修改代码。

```shell
$ git show 4ebd4bbc3ed321d01484a4ed206f18ce2ebde5ca
```

对比不同版本

```shell
$ git diff c0f28a2ec490236caa13dec0e8ea826583b49b7a 2e476412c34a63b213b735e5
```
