# raspberrypi-3
远程SSH登录及VNC外网连接RASPBERRYPI 3
## 由于现在软件更新换代太快，网上的教程都不适用了，经过查找及摸索终完成了目标，故做下笔记
**如何用SSH远程登录**
  * 输入命令 
    `sudo apt-get update`
    `sudo raspi-config`
 > 选择Iterfacing Option->SSH,选择打开，安装完之后，重启(sudo reboot)
 > 然后打开处于同个局域网的另一台终端输入:`ssh@你的树莓派内网的IP地址`
 ***外网连接***
   设置静态IP
   `sudo nano /etc/dhcpcd.conf`
  > 打开文件修改里面注释的部分，跟下面设置的差不多，改下IP，及路由就行,另外eth0为网线连接的，wlan0为无线连接，看个人需要
   * interface eth0
   * static ip_address=192.168.31.8/24
   * static routers=192.168.31.1
   * static domain_name_servers=192.168.0.1 8.8.8.8 fd51:42f8:caae:d92e::1
  > 重启
 ***家里有路由接外网的，要设置端口映射（端口转发)***
  > 例如：外网端口设置8080，内网即树莓派设置的静态IP:192.168.31.8：22
 ***自此就可以外网连接了，输入：`ssh 主机名@外网IP：8080`或`ssh 主机名@外网ip -p 8080`***
  > 输入密码就成功了
## VNC外网连接的方式
   > `sudo raspi-config`
   * 选择Iterfacing Option->vnc,装完重启
   * 看到右上角多出一个应用，点示后找到窗口有个sign in 然后注册或官网注册，登录之后，在同个界面下会多个XXX 's Team(Home)
   * 说明成功了
   * 以后在任何外网环境都可以登录注册的VNC用户密码后，点击Team(Home)那个连接就可以远程桌面了
   参考：(https://www.realvnc.com/en/connect/docs/raspberry-pi.html?_ga=2.106301190.402018933.1565580426-440758524.1564401303#raspberry-pi-connect-cloud)
   * 最后总结：由于我还不会截图，加上这个软件版本更新也快，放图到时也会无效了，以上是raspberrypi 3b+比较容易的设置文案，其他版本会有差异，如有不明白    * 的地方与我联系，一起学习
