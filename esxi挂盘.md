# ESXI挂载硬盘方法

!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/gua1.png" />
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/gua2.png" />
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/gua3.png" />
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/gua4.png" />

#
#
fdisk -l           # 第一步输入命令查看要挂载的硬盘编号

fdisk /dev/sdb     # 第二步，输入命令，sdb根据你硬盘编号改

输入fdisk /dev/sdb命令后，一次按  n  p  1 回车2次  wq  回车保存

mkfs.ext4 /dev/sdb1  # 第三步，格式化挂载盘，根据你挂载硬盘的编号加个1，比如我的sdb1

blkid                # 第四步，输入命令查看挂载盘的UUID 

vi /etc/fstab        # 第五步，输入命令后增加挂载盘的UUID

UUID=38b401e1-f528-480b-98a5-83a38c12c81c /mnts/disk ext4 defaults,nofail 0 0      

 输入命令后增加挂载盘的UUID格式，38b401e1-f528-480b-98a5-83a38c12c81cs是UUID，/mnts/disk是挂载路径，你自己修改成你喜欢挂载的

mount -a          # 第六步，输入命令

reboot           # 第七步，重启系统

df -h            # 重启系统后，输入命令查看挂载成功没
