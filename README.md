# ubuntu-
买了电脑，装个ubuntu。期间遇到了一些问题，第一，装ubuntu系统的分区问题，第二，然后要更新显卡驱动什么的，cuda cdnn

问题一：win装双系统ubuntu
https://www.e-learn.cn/content/linux/376881   
不过我boot设置为主分区。


问题二：ubuntu无法进入tty （未解决）
按照网上教程，说什么ctrl + alt + fn可以进入，结果从ctrl + alt +f1 -f7都没有用，ctrl + alt +f1直接锁屏，其他直接黑屏。然后看贴子，说什么重启
进入ubuntu高级设置，然后选择那个 grub 选择更新grub，然后哦resume normal 重启。发现分辨率变了，图标变大了。然后ctrl + alt + f2。3....可以进入tty
wen't

问题三：WIn10+Anaconda 环境下安装 PyTorch 避坑指南
https://blog.csdn.net/red_stone1/article/details/86669362


问题三：linux + pycharm（py3.6） 中跑出现提示cuda 驱动版本过低，但合用的电脑cuda又动不得， 只能通过降低torch版本。（pycharm中不同解释器里面的 torch什么的可能    
        都不同，之前（cuda 9.0 + torch 1.2.0 + torchvision 0.4.0 + nvidia driver 390）提示要升级nvidia driver -----> 转为 cuda9.0 + torch 1.0.0
        
解决：  因为师兄是py3.6， cuda version：9.0.176 + torch 1.0.0 +torchvisoion 0.2.1 回退torch版本与torchvision版本  
       方法： pip3 install  torch==1.0.0 
              pip3 install torchvision == 0.2.1 （pip install 某版本后，会自动卸载原有的版本；当安装的torchvision 0.3.0以上，会同时安装 torch1.2.0版本。所以，要记得换torch 版本。）
              此时，环境貌似和师兄一样，跑一下gpu的代码，OK，好了！
       下面记录下查询各种版本用到的命令：
       
   1> 查询cuda版本：
       在：huangpan@logos-server：~$      输入：cat /usr/local/cuda/version.txt            输出：CUDA Version 9.0.176
   2> 查询显卡型号：
       在：huangpan@logos-server：~$      输入：lspci  |grep  VGA                           输出：两个1080ti
   3> 查询nvidia驱动：
       在：huangpan@logos-server：~$      输入：sudo dpkg --list | grep nvidia-*           输出：一大窜，其中nvidia driver：390
   4> 在pycharm 系统解释器中 查看 torch  torchvision版本
   5> 查看网络状态 
       在：huangpan@logos-server：~$      输入：ifconfig -a      其中enpos31f6： 这一栏 inet：为主机ip地址 ，
   6> 查看（ip默认22端口号）22号端口：
       在：huangpan@logos-server：~$      输入：netstat -an | grep ：22
       
       
       
