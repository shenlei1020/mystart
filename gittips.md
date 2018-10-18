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



## 2. 修改仓库文件

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
