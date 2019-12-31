### See:
    https://wiki.archlinux.org/index.php/Bumblebee
    https://www.jianshu.com/p/6367d737f349
  
##  查看当前显卡
    screenfetch  
    neotetch  
    inxi -Fx  
    lspci  
   
## 安装驱动
    manjaro setting 中找到 hardware configure,打开这个配置窗口  
    点左上的 "Auto install proprietary driver"  
    将会安装 Bumblebee 驱动程序,   
    运行命令: $gpasswd -a user bumblebee
    Reboot your system: $reboot
  
##  TEST:
    $optirun glxgears -info
    $optirun glxspheres64
    如果一个内有动画的窗口出现，那么 Optimus 和 Bumblebee 正在工作。
  
    lspci
      3D controller: NVIDIA Corporation GM108M [GeForce 940MX] (rev ff)
      可以看到 Gefore 940MX 后面的 rev ff表示独立显卡已经关闭
  
##  usage:
    optirun -b none nvidia-settings -c :8
  
    bumblebee的作用是禁用nvidia独立显卡，需要使用独显时，使用”optirun 程序名“ 
    手动开启nvidia来运行需要加速的程序，如optirun vmware。
   
   ------------------

## 打开N卡设置：
    $optirun nvidia-settings -c :8
    注释: 
      此时在另外一个命令行窗口下 输入 lspci
      可以看到这样一条: 3D controller: NVIDIA Corporation GM108M [GeForce 940MX] (rev a2)
      说明 独立显卡已经打开了.
      关闭 N卡设置窗口再输入  lspci
      3D controller: NVIDIA Corporation GM108M [GeForce 940MX] (rev ff)
      独立显卡立马关闭
   
----------------------------------
## General usage

    $ optirun [options] application [application-parameters]

    For example, start Windows applications with Optimus:

    $ optirun wine application.exe

    For another example, open NVIDIA Settings panel with Optimus:

    $ optirun -b none nvidia-settings -c :8

    Note: A patched version of nvdockAUR is available in the package nvdock-bumblebeeAUR.

    For a list of all available options, see optirun(1). 
   
   
 
    #下面的功能用不了
    如果需要不依赖Bumblebee来使用CUDA, 为开启NVIDIA显卡，运行
    sudo tee /proc/acpi/bbswitch <<  
    注意，重启完N卡又会回复关闭状态。
    # 这个功能用不了

   
   
