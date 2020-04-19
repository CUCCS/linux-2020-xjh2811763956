# 动手实战Systemd


## 软件环境
* asciinema
* Ubuntu 18.04.4 Server 64bit
  
## 实验过程
* [命令篇](https://asciinema.org/a/JjPOyOwXtNREjS1DxenYW5w9B)

* [实战篇](https://asciinema.org/a/h3E8BT6O89qdzxG2udLYavJ8o)

  
## 自查清单

### 1. 如何添加一个用户并使其具备sudo执行程序的权限？
  ```
  # 添加一个用户
  useradd username 或 adduser  username

  # 赋予sudo权限
  usermod -a -G sudo username
  ```

### 2. 如何将一个用户添加到一个用户组？
  `sudo usermod -a -G groupname username`
  
### 3. 如何查看当前系统的分区表和文件系统详细信息？
```
# 查看分区表
sudo fdisk -l

# 查看文件系统详细信息
df -Th
```

### 4. 如何实现开机自动挂载Virtualbox的共享目录分区？
```
# 执行并重启后生效
sudo mount -t vboxsf sharing /mnt/share
```

### 5. 基于LVM（逻辑分卷管理）的分区如何实现动态扩容和缩减容量？

* 扩容
  ```
  # 查看卷组剩余大小，没有剩余空间则要增加磁盘
  vgs

  # 查看各lv类型
  df -Th

  # lv扩容
  lvextend -L size dir

  # 使用resize2f调整ext2/3/4格式文件系统大小
  resize2fs dir
  ```

* 缩减容量
  ```
  # 逻辑卷回缩不能在线进行，所以要卸载
  umount dir

  # 缩小文件系统
  resize2f dir size

  # 缩小逻辑卷
  lvreduce -L dir size

  # 查看并挂载逻辑卷
  lvdisplay
  mount dir
  ```

 
### 6. 如何通过systemd设置实现在网络连通时运行一个指定脚本，在网络断开时运行另一个脚本？
```
# 修改systemd-networkd.service配置文件中的[Service]区块

ExecStartPost=指定脚本
ExecStopPost=另一个脚本 

# 重载修改过的配置文件
sudo systemctl daemon-reload

# 重启相关服务
sudo systemctl restart systemd-networkd.service
``` 

### 7. 如何通过systemd设置实现一个脚本在任何情况下被杀死之后会立即重新启动？实现杀不死？
```
# 打开配置文件
sudo systemctl vi 服务的配置文件名

# 修改[Service]区块中的Restart字段
Restart=always

#重载修改过的配置文件
sudo systemctl daemon-reload

#重启相关服务
sudo systemctl restart 服务名
```

## 参考资料
* [Systemd 入门教程：命令篇 by 阮一峰的网络日志](www.ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html)
* [Systemd 入门教程：实战篇 by 阮一峰的网络日志](http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-part-two.html)
* [第三章课件](https://c4pr1c3.github.io/LinuxSysAdmin/chap0x03.md.html#/title-slide)
* [自动挂载共享文件夹](https://www.cnblogs.com/djzny/p/4881521.html)
* [逻辑卷增加，扩容，缩小，删除步骤](https://blog.csdn.net/j_ychen/article/details/79404197?depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-3&utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-3)