# WechatOnLinux
分享一个在linux使用微信的方法。
需要用到的工具，包括kvm windows虚拟机或任何能远程的windows机器，freerdp。

先上demo
![image](https://user-images.githubusercontent.com/10022333/114804770-6ea70800-9dd4-11eb-9db4-17ec21a1cf4a.png)
发送截图
![image](https://user-images.githubusercontent.com/10022333/114804900-a8780e80-9dd4-11eb-8869-f2809e82af0a.png)

使用步骤
1. 使用到的 freerdp 连接命令 
   xfreerdp /drive:/data /u:pcl /p:pcl /size:1440x1100 /scale:180 /scale-desktop:200 /v:192.168.137.200
   根据自己电脑的分辨率设置远程windows的分辨率，我自己电脑的分辨率是3840x2160，所以设置远程分辨率1440x1100。然后将微信窗口最大化，隐藏Windows任务栏，达到demo图中效果。
   /drive:/data 将本地目录映射到远程windows目录，方便发送截图。
   
2. 在linux本机设置一个截图保存的快捷键，以ubuntu为例。
   ![image](https://user-images.githubusercontent.com/10022333/114805648-f04b6580-9dd5-11eb-84b6-3c0b131d1415.png)
   在本机用快捷键截图保存之后，在微信里用发送文件的方式发送截图。
   ![image](https://user-images.githubusercontent.com/10022333/114804900-a8780e80-9dd4-11eb-8869-f2809e82af0a.png)
   
   freerdp本身可以复制剪贴板文字，可以复制文件，但是不能复制剪贴板的截图。所以以上算是目前能想到的解决办法。
   
3. 设置一个桌面快捷方式或者任务栏快捷方式
   ![image](https://user-images.githubusercontent.com/10022333/114804900-a8780e80-9dd4-11eb-8869-f2809e82af0a.png)
   在桌面创建文件 ~/Desktop/wechat.desktop 
   重复点击桌面图标会重复进行远程连接，点一次就可以了。
   
 一些优化的可能性
 1. freerdp 可以使用 -decorations 参数去掉标题栏的显示
    xfreerdp -decorations /u:pcl /p:pcl /size:1440x1100 /scale:180 /scale-desktop:200 /v:192.168.137.200
    ![image](https://user-images.githubusercontent.com/10022333/114807613-4bcb2280-9dd9-11eb-85ac-160e2113f9da.png)
    但是去掉标题栏之后，不方便窗口拉动控制，其实没必要。
 2. freerdp 的 /app 参数可以直接打开远程机器上的软件
    xfreerdp /app:"C:\Program Files\WeChat\WeChat.exe" /u:pcl /p:pcl /size:2880x1620 /scale:180 /scale-desktop:200 /v:192.168.137.200
    但是这个功能bug很多，比如窗口控制的各种bug，只能输入字母，不能输中文。谁用谁知道。

   
   
