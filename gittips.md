# Git tips

## 1. 初始化

* 进入空文件夹或是有项目的文件夹，执行

  ```bash
  git init
  ```

  可以初始化repository，建立仓库，产生 **.git/** 文件。

  **.git/**中的**config**文件中包含本地repository的信息。

* 执行

  ```bash
  git config [--global] user.name "LeiShen"
  git config [--global] user.name "shenl15@..."
  ```

  加`--global`会指明**所有**repository的本地机器信息，不加则表示本地机器信息。

* 仓库布局

  这时候就建好一个仓库了，

  > 建好的仓库只是一个本地仓库，即origin->master

  > origin只是仓库的一个标签或是指针，对应repository。
  >
  > master是仓库的master分支，对应branch。

  1. 如果你有一个项目的http或ssh地址，可以拷贝下来

     ```bash
     git clone <ssh ADDR|http ADDR>
     ```

     这是的origin++++++

  2. 如果想连远程仓库

     ```bash
     git remote add origin <ssh ADDR|http ADDR>
     ```

     ++++++



## 2. 操作本地仓库

1. 本地master仓库

* 新建文件

  ```bash
  echo "hello">>hello.txt
  echo "My name is Shen Lei">>myname.txt
  ```

  执行

  ```bash
  git add .
  git commit -m "my information"
  ```

  `git add .`提交时有警告

  > master warning: LF will be replaced by CRLF in www/css/style.css.> 

  这是因为Git默认编码格式换行符是CRLF（windows），很多情况下编辑器的格式是LF（linux），Git上传的时候是默认CRLF版本，所以会警告，帮助自动格式转换。解决方案，关闭格式自动转换功能：

  ```bash
  git config --global core.autocrlf false
  ```

* 修改文件

  ```bash
  echo "I am a student in TS">>myinfo.txt
  echo ".">>myname.txt
  rm hello.txt
  ```

  执行

  ```bash
  git status
  ```

  可以查看仓库现在的信息，包含本地变化，和缓存区。

  再执行

  ```bash
  git add .
  git status
  ```

  > 注：有没有`git add .`，仓库的状态不一样，文件到达的位置不一样。

  * `git add .`, `git add -u`, `git add -A`三者有如下图：

    ![1539795402345](C:\Users\shenlei\AppData\Roaming\Typora\typora-user-images\1539795402345.png)

* 查看更改历史`git diff`

  查看修改了哪些**文本**，会用到`git diff`。

  > 注：`git diff`+*文件名*，只能查看add之前的文本文件，如果已经add了，就查不到了。

  **如此说来**，git提交分为两步，第一步是提交修改，对应`git add`；第二步是提交新文件，对应`git commit`。

## 3. 操作远程仓库

* 首先连接远程仓库

  ```bash
  git init
  git remote add origin <ssh ADDR|http ADDR>
  ```

  init的作用是把本地仓库和之前连接远程仓库初始化，断开连接。

  `git remote`：查看远程**仓库**，一般返回**branch**

  `git remote -v`：显示远程仓库的详细地址

* 

## 4. 分支切换

* 本地

  1. 查看分支

     ```bash
     git branch [-a]
     ```

     可以查看本地【远程】分支情况，*表示的是当前分支。

  2. 建立新分支

     ```bash
     git branch <branch-a>
     ```

     建立新分支branch-a

  3. 跳转分支

  ```bash
  git checkout <branch-a>
  ```

  切换到刚建立分支branch-a

  > `git chechout -b <branch-a>`等于上面两条命令的和。建立新分支，并立即进入。

  4. 