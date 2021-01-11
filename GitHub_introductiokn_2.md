Git:Hub实战入门(二)

Git和GitHub

# 3.1 代码托管中心

代码托管中心相当于一个寄包处，可以寄包取包

## 3.1.1 不同的代码托管中心

### 1> LAN(局域网/私网)下

GitLab

### 1> WAN(广域网/外网)下

GitHub(国外托管)

码云（国内托管更快）

## 3.1.2 本地库和托管库

![](D:\GitHub\github_introduction\how_to_work_like_a_team.png)

- Push: 把库推送到远程
- clone:下载代码
- fork: 复制远程库
- merge: 合并远程库

## 3.1.3 working dictionary，cached, repository



# 3.2 Git命令行基本操作

## 1> 显示当前文件夹路径

```c++
$ pwd
```

效果：<img src="D:\GitHub\github_introduction\pwd.png" style="zoom:50%;" />

注意：文件夹不能有除了26个字母，下划线，数字外的其他字符！

## 2> 查看目录和文件

查看显示目录和文件

```c++
$ ll
```

查看隐式目录和文件

```c++
$ ls -la
```

## 3> 切换目录

```c++
$ cd pan_number:/file_name/next.../
```

路径包含文件夹一定要正确，否则会出现 cd: too many arguments  的报错

切到系统用户文件夹

```c++
$ cd ~
```

## 3> 停止、重启、终止进程

停止某个工作进程

```c++
$ ctrl+z 
```

当提示 there are stopped jobs 而无法正常退出(exit/ logout) 时，说明有进程没有结束。

查看被停止的进程

```c++
$ jobs
```

系统显示

```c++
[1]+ Stopped ...
[2]+ Stopped ...
```

此时，有两个被停止的进程

可以重启或停止某一个进程

```c++
$ fg %2 //重启索引为2的进程
$ kill %1 //结束索引为1的进程    
```

# 3.3 本地库操作

### 1> 本地库初始化

选择一个本地文件夹，右键窗口中点Git Bash Here

2. 创建仓库

```c++
$ mkdir file_name
```

3. 初始化repository——git可管理的

```c++
$ git init
```

有.git 目录等

4. 给repository设置签名

- 目的：仅仅标识repository开发者，和代码托管中心的账户无关

- 作用范围：

1>仓库级：标识仅作用于当前repository

```c++
$ git config user.name eva.yx.wang
$ git config user.email eva_yx_wang@163.com
```

config信息位置：当前目录/.git/config

2>系统用户级：作用于当前OS登陆用户的all repository

```c++
$ git config --global user.name eva.yx.wang
$ git config --global user.email eva_yx_wang@163.com
```

config信息位置：~/.gitconfig



必须设置，同时设置仓库级和系统用户级时取仓库级的签名

查看.git/ config信息

```c++
$ cat .git/config
```

5. 查看working area(工作区), stage(暂存区) 状态

   ```c++
   $ git status
   ```

显示：Untracked files—-存在文件夹中但未被git追踪的文件，即no committed files 

6. add to  stage (还未commit)

```c++
$ git add file_name
```

<img src="D:\GitHub\github_introduction\git_add.png" style="zoom:50%;" />

- changes to be commited: 可提交的更改即stage 内files

  new file: cached 新增文件，被git 追踪

- Untracked files：工作区files，未被git 追踪

7. 撤销stage的commit

```c++
$ git rm --cached <file>...
```

git rm --cached   GitHub_introductiokn_2.md 后

<img src="D:\GitHub\github_introduction\git_rm.png" style="zoom:50%;" />
123

8. 用vim编辑器打开或编辑

```c++
$ vim <file_name>
```

按insert键编辑内容

完成编辑时，先Ctrl+c, 再在底部输入以下信息即可退出vim

```c#
:wq
```

![](D:\GitHub\github_introduction\edit_file.png)

(添加了‘123’后退出)

用git status 查看，发现有修改痕迹(修改的是工作区文件)

<img src="D:\GitHub\github_introduction\edittedBcommitted.png" style="zoom:50%;" />

9. commit  files 到repository

最好先add to stage 再commit ，否则一旦commit就无法撤回

```c++
$ git commit -m "commit message..." <file> 
```

commit message最好包含date, filename, changes conclusion
