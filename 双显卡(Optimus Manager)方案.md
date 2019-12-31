# see:
    1. https://wiki.manjaro.org/index.php?title=Optimus_Manager
    2. https://wiki.archlinux.org/index.php/NVIDIA_Optimus
   
   
    3. https://www.v2ex.com/t/630119
       manjaro 安装 Nvidia 显卡驱动， Intel + Nvidia 双显卡解决方案。（已解决）
    4. https://github.com/Askannz/optimus-manager/blob/master/README.md
   
# 问题:
    笔记本电脑有独立显卡,以及核显.同时我常用virtual box 虚拟机, 如何合理的使用这两个显示硬件模块呢?
    
    分析:
      1. 理想的双显卡使用方式是,性能和功耗要均衡,特别是在使用电池的时候,更要考虑他们之间的均衡
      2. 在不使用电池的时候,可以不那么在乎功耗
      3. virtual box 虚拟机对性能要求比较高
      4. 解决方案要简单,容易操作
      5. 综合以上,目前最好的方案是 Optimus Manager
      6. Optimus Manager 可以切换 双显卡.
      7. 其实我只需要 独立显卡, 关闭核显, 没有简单的方法, bios不支持显卡关闭
      8. 其它方案: 大黄蜂驱动已经装上,但是最后无法让 virtual box的虚拟机使用指定的独显,显卡直通技术太难.放弃
   
# 准备
      查看硬件信息的几个指令:
      screenfetch  
      neofetch  
      inxi -Fx  
      lspci  

      uname -r
   
 # 驱动安装 
   ##  安装 bumblebee, 
      1. manjaro setting 中找到 hardware configure,打开这个配置窗口  
      2. 点左上的 "Auto install proprietary driver"  
      3. 将会安装 Bumblebee 驱动程序,   
      4. 运行命令: $gpasswd -a user bumblebee
      5. Reboot your system: $reboot
      
   ## bumblebee 删除方法
      1. Pamac 图形界面 里面找到 所有的 bumblebee 组件,卸载
      2. manjaro setting 中找到 hardware configure,打开这个配置窗口 
      3. 找到 Bumblebee, 点鼠标右键,可以看到一个菜单,可以重装或者卸载这个驱动程序
      4. 卸载 Bumblebee 驱动.
      5. 同样的方法可以卸载其它的驱动,如果需要的话.
      
# Installation optimus-manager

      1. pamac install optimus-manager
      2. systemctl enable optimus-manager
      3. systemctl start optimus-manager
      
# Usage optimus-manager

      Make sure the SystemD service optimus-manager.service is running, then run
      $ optimus-manager --switch nvidia
      $ optimus-manager --switch intel
      $ optimus-manager --status
      $ optimus-manager --help
      $ optimus-manager --set-startup MODE     # MODE can be intel, nvidia, or nvidia_once

      查看当前哪个显卡在运行
      glxinfo | grep "server glx vendor string"

# N卡常用命令
      nvidia-smi  N卡性能监控命令
      nvidia-settings  N卡设置命令
   
# optimus-manager-qt  安装
      //optimus-manager-qt  是一个图形切换显卡工具
      $ pacman -Sy yay
      $ yay -Sy optimus-manager-qt
      
# 安装 optimus-manager OK
      $ optimus-manager --status
      Optimus Manager (Client) version 1.2.2

      Current GPU mode : nvidia
      GPU mode requested for next login : nvidia
      GPU mode for next startup : nvidia
      Temporary config path: no
      $ 
      
      $ glxinfo | grep "server glx vendor string"
      server glx vendor string: NVIDIA Corporation
      $
    
# 进入Virutualbox 客户机 
      1. 需要关闭 虚拟机的3D加速,否则虚拟机客户无法显示
      2. 客户机桌面图形更新也快多了
      3. 笔记本电脑 也安静了好多, CPU不热了,风扇不会狂飙.
            估计是工作量移到独显上, 热量分散啦
 
# 总结: 
### 双显卡 折腾好久, 绝望了好多次. 终于成功啦!
  --- 只要功夫深,铁杵磨成针!

# The End!

  

      
