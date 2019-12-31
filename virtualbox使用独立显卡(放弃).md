
大黄蜂驱动下 显卡直连kvm或vbox 虚拟机怎么做 
https://bbs.deepin.org/forum.php?mod=viewthread&tid=182586

同这个一模一样的任务:


1秒更新一次监视 n卡状态
watch -n 1 optirun nvidia-smi
此命令可以行. 
运行测试程序:
optirun glxspheres64
可以看到 nvidia-smi 中 GPU的占用率在飙升
GPU的显存再用也在飙升.

但是启动 optirun virtualbox,
nvidia-smi 就没有变动,一点点都没有动.
再启动 其它的虚拟机也没有变动.
暂时放弃,步研究啦

