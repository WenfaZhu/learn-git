# Git 的使用说明

`Git` 以及 `Github` 相关的设置和操作，有点混乱，待整理。

### 配置全局信息

```shell
$ git config --global user.name "yourName"

$ git config --global user.email "yourEmail"
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
$ git remote add coding master git@git.coding.net:gogotanc/learn-git.git

# 添加名为 origin 的远程仓库
$ git remote add origin master git@github.com:gogotanc/learn-git.git 
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

> 这些命令在你输入 git status 的时候会有提示你接下来如何操作。

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

### 查看远程仓库信息

查看远程仓库分支的信息

```shell
$ git ls-remote

From git@github.com:gogotanc/docker-spark.git
bbdf3430e3ea3504c53c753c51a720b673a69ff7	HEAD
bbdf3430e3ea3504c53c753c51a720b673a69ff7	refs/heads/master
e52ba1da9eb7c8d1709abcb0020be2e899ad5545	refs/heads/v1.1.1onHadoop2.6.0
ac7358bdc61b09cba61a699fa5e90cb0f461ad0e	refs/heads/v1.1.1onHadoop2.6.0-ubuntu
c5cdf7ff7b253114a4dff682f8d1e14a48bde603	refs/heads/v1.1onHadoop-2.5.1
ef718168d10f660807c24ff3ada8a4d83521d49f	refs/heads/v1.2.0onHadoop2.6.0
61b01fad61ac482c867ed30ad7fd4ebbaa6c9e3f	refs/heads/v1.2.0onHadoop2.6.0-ubuntu
4c800ec6991af5a9708fb2d560a2be3fd999412e	refs/heads/v1.2.1onHadoop2.6.0
4bfd538b17cfc50d9bd2c9ae38a3d18c2f6fc313	refs/heads/v1.2.1onHadoop2.6.0-ubuntu
51ff7a94bd5397eab22f1372f812ef8ea4b3d533	refs/heads/v1.3.0onHadoop2.6.0
865f897cd75615bce4bf8303d8a4d4b6c7be3c72	refs/heads/v1.3.0onHadoop2.6.0-ubuntu
aded62d12469bad880d6b1d7a1fd46f6fd82b268	refs/heads/v1.3.1onHadoop2.6.0
2afb1d7c131cf4b6574394418a856cf6f5b4e738	refs/heads/v1.3.1onHadoop2.6.0-ubuntu
23f1dac4a9e5b82838789f156d04aea638e9b5a0	refs/heads/v1.4.0onHadoop2.6.0
25f8c145d3adaaeb26d7f0c4d4403ef95ef6f6ee	refs/heads/v1.5.1onHadoop2.6.0
07e053bbbeeb3770f5032b241ecce3c2767a3e83	refs/heads/v1.6.0onHadoop2.6.0
```

还可以使用下面的命令查看

```shell
$ git remote show origin

* 远程 origin
  获取地址：git@github.com:gogotanc/docker-spark.git
  推送地址：git@github.com:gogotanc/docker-spark.git
  HEAD 分支：master
  远程分支：
    master                     已跟踪
    v1.1.1onHadoop2.6.0        已跟踪
    v1.1.1onHadoop2.6.0-ubuntu 已跟踪
    v1.1onHadoop-2.5.1         已跟踪
    v1.2.0onHadoop2.6.0        已跟踪
    v1.2.0onHadoop2.6.0-ubuntu 已跟踪
    v1.2.1onHadoop2.6.0        已跟踪
    v1.2.1onHadoop2.6.0-ubuntu 已跟踪
    v1.3.0onHadoop2.6.0        已跟踪
    v1.3.0onHadoop2.6.0-ubuntu 已跟踪
    v1.3.1onHadoop2.6.0        已跟踪
    v1.3.1onHadoop2.6.0-ubuntu 已跟踪
    v1.4.0onHadoop2.6.0        已跟踪
    v1.5.1onHadoop2.6.0        已跟踪
    v1.6.0onHadoop2.6.0        已跟踪
  为 'git pull' 配置的本地分支：
    master 与远程 master 合并
  为 'git push' 配置的本地引用：
    master 推送至 master (最新)
```

### 拉取本地没有的远程分支

使用下面的命令即可将远端信息全部拉取过来

```shell
$ git pull origin
```

然后使用分支命令，对分支进行开发

```shell
$ git checkout -b yourBranchName origin/remoteBranchName
```

`yourBranchName` 可以是任意的名称，`remoteBranchName` 即远程的分支名称。
