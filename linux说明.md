# 1.linux常用命令

## 1.1 开关机

* init 0   关机
* init 6   重启   

## 1.2 常用命令

* cd   切换目录
* ls   查看当前目录下面的文件
* ctrl+c      中断当前程序
* ctrl+l  / (clear)   清屏

##  1.3 查看ip地址

* ip addr           查看ip地址
  * ![image-20201123103234574](.\linux说明.assets\image-20201123103234574.png)

* ifconfig -a  查看ip地址
  * 如果没有这个命令需要先安装
  * 查询这个命令 yum search ifconfig
  * 根据查询结果安装 yum install -y 包名
  * ![image-20201123103509990](.\linux说明.assets\image-20201123103509990.png)
* ping 127.0.0.1   看网络是否通畅

## 1.4 创建删除相关

* touch aaa.txt     在当前目录下面创建一个aaa.txt的文件
* rm -rm aaa.zip  删除一个文件

## 1.5 shell命令技巧

* tab补全
* 上下键盘    查看最近的历史命令
* history 查看命令历史
  * !2  调用历史中编号为2的命令
  * ![image-20201123104719250](.\linux说明.assets\image-20201123104719250.png)

## 1.6 创建用户及修改密码

* useradd zhangsan  添加用户
* passwd zhangsan   设置密码
* userdel -rf zhangsan  删除用户
  * -r：递归的删除目录下面文件以及子目录下文件。

# 2 linux目录

* root目录  
  * linxu 超级权限 root 的主目录
* home目录
  * 普通用户家目录
  * 创建一个zhangsan用户   useradd zhangsan
  * 在home下就有一个zhangsan的文件夹 
    * ![image-20201123111108881](.\linux说明.assets\image-20201123111108881.png)
  * 系统默认的用户主目录，如果添加用户是不指定用户的主目录，默认在/home 下创建与用户同名的文件夹。
* bin 目录
  * 存放系统所需要的重要命令，比如文件或目录操作的命令 ls、cp、mkdir 等，另外 /usr/bin 也放了一些系统命令。这些命令对应着文件都是可以执行的。
* sbin 目录
  * 存放只有 root 超级管理员才能执行的程序
* boot 目录
  * 存放着 linux 启动时内核及引导系统程序所需要的核心文件
* dev 目录
  * 存放这 linux 系统下的设备文件，如光驱等。
* etc 目录
  * 存放系统的配置文件，作为一些软件启动时默认配置文件读取的目录
* mnt 目录
  * 临时文件挂载目录、 也可以说是测试目录
* opt 目录
  * 第三方软件存放目录
* media 目录
  * 即插即用型设备挂载点，光盘默认挂载点，通常光盘挂载于/mnt/cdrom 下。
* tmp 目录
  * 临时文件夹
* usr 目录
  * 应用程序存放目录，安装 linux 软件包是默认安装到/usr/local 目录下
* var 目录
  * 目录经常变动，/var/log 存放系统日志，/var/log 存放系统库文件。

# 3 文件目录管理

## 3.1 创建文件

>  touch file1

![image-20201123112757431](.\linux说明.assets\image-20201123112757431.png)

## 3.2 修改文件及移动

>  mv file1 file11

![image-20201123112949956](.\linux说明.assets\image-20201123112949956.png)

> mv index.html /root/

![image-20201123113309388](.\linux说明.assets\image-20201123113309388.png)

## 3.3 删除文件

> rm -rf file11

* -r：递归的删除目录下面文件以及子目录下文件。
* -f：强制删除，忽略不存在的文件，从不给出提示

![image-20201123113104387](.\linux说明.assets\image-20201123113104387.png)

##  3.4 复制文件

> cp index2.html index3.html

![image-20201123113511340](.\linux说明.assets\image-20201123113511340.png)

## 3.5 批量创建/删除

> touch file{1..10}.text

![image-20201123113735459](.\linux说明.assets\image-20201123113735459.png)

> rm -rf file{1..10}.text

![image-20201123113817794](.\linux说明.assets\image-20201123113817794.png)

## 3.6 编辑文件

### 3.6.1 基本操作

> vi index2.html

![image-20201123114040988](.\linux说明.assets\image-20201123114040988.png)

进入文件后进入编辑模式

> 按回车或者i

退出编辑模式

> 按Esc

保存/不保存退出

> :wq/:q

### 3.6.2 遇到的问题

当我们的编辑器被强制退出后

* 编辑器保留了几个临时存档文件
  * ![image-20201123121042046](.\linux说明.assets\image-20201123121042046.png)

* 这些文件默认是不会显示的，需要我们手动删除
  * ![image-20201123121139026](.\linux说明.assets\image-20201123121139026.png)

### 3.6.3 命令行模式操作

* **编辑模式**
  * a 在光标所在位置下一个字符开始输入
  * A 在光标所在行尾开始输入
  * i 在光标所在位置开始输入
  * I 在光标所在行首开始输入
  * o 在光标所在行下新增一行，并在新增行行首开始输入
  * O 在光标所在行上新增一行，并在新增行行首开始输入

* **命令模式**

  * : 执行命令

    * q(quit)表示退出编辑器
    * wq(write quit)保存退出
    * q!强制退出
    * wq!强制保存退出为

  * / 正向搜索

    ![image-20201123145831458](.\linux说明.assets\image-20201123145831458.png)

  * ? 反向搜索

* **操作模式**

  * 剪切  
    * dd  剪切光标所在位置的整行
    * ndd n为数字，表示从当前行开始，从上到下剪切n行
  * 粘贴
    * p  将缓冲区中的内容放到当前行之下
    * np  n是数字，相当于执行n次p命令
  * 复制
    * y  从光标处开始复制（只复制一个字）
    * yy  复制当前行
    * nyy  n为数字，表示从当前行开始，从上到下复制n行
  * 修改
    * r  修改光标位置的字符（只修改一个字，第一次按r第二次按想要修改的字）
    * R  从光标位置开始替换，并进入文本输入模式(ESC退出)
  * 删除
    * x  删除光标所在的那个字
  * 撤销
    * u  撤销上一次操作

## 3.7 创建目录

> mkdir dir1 dir2 dir3

![image-20201123151515739](.\linux说明.assets\image-20201123151515739.png)

递归创建目录

> mkdir -p a/b/c/d/e/f/g

![image-20201123151945853](.\linux说明.assets\image-20201123151945853.png)

## 3.8 修改及移动

> mv dir1 dir11

![image-20201123151834012](.\linux说明.assets\image-20201123151834012.png)

## 3.9 删除目录

> rm -rf dir1 dir2

* -r：递归的删除目录下面文件以及子目录下文件。
* -f：强制删除，忽略不存在的文件，从不给出提示
* rm -rf dir* 以 dir 开头的所有文件删除

![image-20201123151652731](.\linux说明.assets\image-20201123151652731.png)

## 3.10 复制目录

> cp -rf a /root

![image-20201123152259811](.\linux说明.assets\image-20201123152259811.png)

## 3.11 递归查看目录

> tree a

![image-20201123152419714](.\linux说明.assets\image-20201123152419714.png)

如果没有tree命令则安装tree

> yum install tree -y

![image-20201123152507887](.\linux说明.assets\image-20201123152507887.png)

## 3.12 文件类型

Linux 下可以用 ll 命令来判断文件类型，主要是根据每行的首个字符来判断

* -rw-r—r— "-“开头的都是普通文件
* drw-r—r— "d"开头的是目录文件
* brw-r—r— "b"开头的文件都是块设备文件;
* crw-r—r— "c"开头的文件都是字符设备文件
* lrw-r—r— "l"开头的文件都是软链接文件
* prw-r—r— "p"开头的文件都是管道文件
* srw-r—r— "s"开头的文件都是 socket 文件; (e.g. srwxrwxrwx 1 mysql mysql 0 Sep 9 13:49 mysql.sock)