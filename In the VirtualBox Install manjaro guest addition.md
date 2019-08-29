# In the VirtualBox Install manjaro guest addition

1. Fist way: 
  sudo pacman -S virtualbox-guest-utils
  This is a easy way. but I failed.
  see:
  https://forum.manjaro.org/t/help-with-virtualbox-6-installing-guest-additions/72996
  
 2. Use VBoxGuestAdditions.iso
    
    I succeeded with this way
    
    >>>
vitualbox device菜单点击安装增强功能选项。
在manjaro中打开文件管理，左侧往下拉，会有个磁盘管理，这里面会多一个已经挂载的磁盘
点击磁盘进入该磁盘所在目录，在目录下右击root，打开命令窗口，输入./xxxxxxxx.run,,,,这里的xxxxx是指文件夹下面的run文件名
直译过来：请安装与当前内核匹配的Linux内核“header”文件，原因是Linux4.19内核的RedHat内核版本的头文件的位置发生了变化，导致安装失败。解决办法：使用 sudo pacman -S linux-headers 命令 选择对应的内核版本 安装完毕后，重启系统，再次安装即可
 ———————————————— 
版权声明：本文为CSDN博主「xiaolei565」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/xiaolei565/article/details/89925131
>>>
 
 a. 使用VirtualBox安装manjaro后，如何安装增强功能（详细介绍）
 https://blog.csdn.net/xiaolei565/article/details/89925131
 
 b. manjaro系统在VirtualBox虚拟机中无法安装增强插件
 https://blog.csdn.net/qq_42050903/article/details/85273163
 
 
