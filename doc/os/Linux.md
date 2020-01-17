# Linux

## 理解, [参考链接](description)
  > Linux 本身只是一个内核，它为程序员定义了操作系统的基本元素，但最终用户无法直接操作它也无法使用它。所以，除了开发者以外的用户，无法知道 Linux 是什么。
  > Linux 是一个相对自由的世界，所以围绕 Linux 内核你可以搭建出各种各样的上层系统。这样搭建起来的系统，称为「发行版」。普通用户只能接触到发行版，无法接触到 Linux 本身，而发行版中所带的命令行，shell，X Window 系统，都不属于 Linux 的一部分。王垠曾经说过：Linux 可以是这样，Linux 可以是那样，Linux 可以是任何样子。
  > Android 是目前当下用户最多的 Linux 发行版。除了它之外，其他的 Linux 发行版，相比 Android 来说都只占用非常小的比例，这里面包括 Ubuntu，以及各种基于 GNU 的发行版。GNU 并不是 Linux 不可分割的一部分，所以 Android 里虽然几乎不含有 GNU 的元素，但它仍然是纯正的正宗的 Linux。
  > 既然，Linux 本身从来就没有定义它该是什么图形系统，与用户该是什么操作，甚至也从来没有定义它该有什么命令行（那些往往是 POSIX 或者 GNU 定义的东西），所以，非开发者讨论 Linux 是否好用根本没意义，因为你接触到的那些部分，都不属于 Linux。——普通用户只能讨论具体的某个「发行版」是否好用。——在当下，如果要讨论当前最流行的发行版，那么讨论的目标无疑应该是 Android。

## 相关概念
  - GNU:
      GNU是一个自由的操作系统，其内容软件完全以GPL方式发布。这个操作系统是GNU计划的主要目标，名称来自GNU's Not Unix!的递归缩写，因为GNU的设计类似Unix，但它不包含具著作权的Unix代码
  - POSIX:
      可移植操作系统接口（英语：Portable Operating System Interface，缩写为POSIX）是IEEE为要在各种UNIX操作系统上运行软件，而定义API的一系列互相关联的标准的总称
  - BSD:
      伯克利软件包（英语：Berkeley Software Distribution，缩写：BSD；也被称为伯克利Unix或Berkeley Unix）是一个派生自Unix（类Unix）的操作系统

      Linux 只是一个宏内核。宏内核负责管理 CPU、内存、进程间通信、设备驱动程序、文件系统和系统服务调用
  - UNIX:
      是一种广泛使用的商业操作系统的名称

## 其他
  stdin,stdout,stderr(标准输入, 输出, 错误): 变量包含与标准I/O 流对应的流对象.，是内建在每一个UNIX系统中的管道

## 开始学习

  #### 基本目录
  - /：/是根目录.Unix 和 Linux 中,没有盘符. 只有一个硬盘,一个根.
  - /bin ：系统的常用命令目录. 包括控制台命令, 系统可执行文件, 系统的核心二进制文件等.
  - /etc： 发布目录, 相当于 windows 系统中的 windows 目录, 保存系统中的所有核心内容. 要求控制权限高, 建议不要随便读写.
  - /usr ：用户目录, 相当于 windows 系统中的 program files 目录. 常用于安装系统所有用户共用的软件,资源的.
  - /root ：root 根用户的用户目录 . 相当于 windows 系统中的C:/users/administrator 目录.
  - /home ：保存其他用户主目录的目录. 如: Linux 系统中有 oldlu 用户. 那么一定有/home/oldlu 目录存在. 代表用户的主目录.
  - /var :系统运行过程的数据目录.

  #### 常用命令
  - cd： change directory - 切换目录. 特殊目录符号。其中当前目录为 - ‘.’ , 父目录为 - ‘..’ 它的使用方式为：使用根目录作为定位标准, 绝对寻址. cd：/xxx/yyy/。相对寻址为：cd xxx/yyy/zzz 。直接进入用户主目录 cd cd ~; cd - 返回上一次所在目录
  - ls: list - 列表目录中的内容.默认显示当前目录下的文件列表 .其中ls -a [目录] 表示当前目录下的所有的文件和目录。
  - ll：简化命令list list - 以列表的信息,显示指定目录中的内容. 列表代表的是文件的详情.
  - clear：清空屏
  - touch ：创建空白文件在 Linux 系统中,文件不需要强制后缀名. 如: 文本文件可以定义为, a | a.txt | a.text
  - cat ：查看文件的全部内容. 一次性显示文件中所有内容.
  - more 分屏显示文件内容, 显示后,使用空格显示下一屏, 回车显示下一行,q 退出分屏显示. ctrl+c,退出命令.
  - head 显示文件的前多少行, 默认显示前 10 行. head -number filename 查看文件中的前多少行.
  - tail ：显示文件末尾多少行.默认显示末尾 10 行. tail -number filename
  - mkdirmake directory - 创建目录. 用法为mkdir directoryName ，一次性创建多级目录mkdir -p parentDirectoryName/childDirectoryName
  - cp ：copy - 复制命令. 使用方式 copy source target copy 源信息 目录：copy 源信息 目录信息
  - rm remove - 删除 ：使用方式 rm source rm 要删除的资源
  - mv ：move - 移动或重命名. 相当于剪切和重命名.
  + vi | vim 编辑文件, vim 是增强命令. 不代表所有的 Linux 都支持. vim 增强在有高亮显示.
    + 模式切换: 
      - i: 编辑模式
      - esc: 进入命令模式
      - "shift + : " :底行模式
    > 打开文件：vi file 文件名 ,处在命令模式
    > 命令模式下，不能编辑文件，要切换到编辑模式才能编辑
    > 按i,可以从命令模式进入编辑模式
    > 命令模式常用的快捷键
    > yy:复制当前行
    > p:粘贴
    > dd:删除当前行

    > 在编辑模式下，只能编辑，不能保存和退出。要切换到"底行模式"才能保存和退出
    > 1.不能从编辑模式直接进入底行模式，只能从命令模式进入底行模式，所以在编辑模式下要先按"Esc"键进入令模式。

    > 2.在命令模式下，按"shift+:"进入底行模式
    > 在底行模式下，有如下命令行
    > 1.wq 保存并退出(一般情况下都是使用这个)
    > 2.q 退出
    > 3.q! 强制退出(出异常了就可以使用强制退出)
  - ifconfig 查看网络编辑器. 查看网卡信息. eth0 - 命名为 eth0 的网卡信息
  - service 服务控制命令. 常用服务: iptables - 防火墙, vsftpd ftp 文件服务器, mysql 防火墙建议关闭. 否则除 80,22 端口外,其他所有端口无法访问.
  - ps 进程信息查看命令.
  - grep 过滤|筛选, 筛选符合关键字的数据.
  - pwd
  - tail -f 文件名 :滚动的查看文件. 查看tomcat的日志(了解)
  - tar 能够将用户所指定的文件或目录打包成一个文件，但不做压缩
    - tar -cvf 要打包成的包名称 被打包的文件(目录);
    - 打包: tar -cvf demo.tar *.txt
      - c --create
      - v --verbose
      - f --file
      - z--zgip
      - x --extract
    - tar -xvf 文件包 -C 目录 解包到指定目录;
    - 解包: tar -xvf app2.tar -C test3
  - ping
  - ps -ef :查看所有进程(很重要)(Process Status)
  - |:管道 前面的输出作为后面的输入-------->就是从|之前的命令查询到的结果中筛选出符合|之后的条件的内容**
  -​ grep:查找指定的内容,grep -i:忽略大小写
  - kill -9 进程号(pid):杀死指定的进程
  - ssh: 登录远程 & 查看日志
    ssh test@10.100.172.133
    cd /log/java/biz-mkt-activity/log
    tail -f tail -f biz-mkt-activity-srv.log
  - fdisk
  - df -h
  - chmod
  - chown
  - who
    

    <!-- + 压缩
    - 第一步 压缩成.zip文件 大小不会变, 且生成.zip文件
    tar -cvf c1.zip c.txt
    - 第二步 将.zip压缩成.gz文件,文件大小会显著变化, 且将原.zip文件变成.zip.gz
    gzip c1.zip
  + 解压
    gzip -d c1.zip.gz -->



[description]: https://www.zhihu.com/question/19653283/answer/20527425 'description'