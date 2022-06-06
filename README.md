
## IP看门狗

1. #### 介绍

   1. 这个小工具是一个练手的小项目,由Java代码实现.主要功能是在运行本程序的电脑IP地址发生变化的时候向指定邮箱发送最新的IP地址.

   2. 当程序检测到IP地址发生变动的时候会向指定邮箱发送最新的IP地址信息

2. #### 在哪使用

   如果运行此工具的计算机拥有自己的IPV6公网地址则可以在公网地址发生改变的时候对指定邮箱进行通知,配合淘宝上一二十块钱的远程开机硬件,可以直接访问家里的各种服务器.

   该工具由java编写.经测试在windows和Centos上表现良好.目前只测试了网易邮箱向QQ邮箱发送邮件.

3. #### 配置文件介绍

   ```properties
   #配置文件文件名为:config.properties
   #服务器名
   serviceName=computer1
   #发件人地址
   sendEmailAddress=xxxxxx@163.com
   #邮箱授权码
   AuthorizationCode=xxxxxxxxxxxxx
   #发件邮箱stmp服务器
   SMTPEmail=smtp.163.com
   #收件人地址
   harvestEmail=xxxxxxxxxx@qq.com
   
   #日志等级0,无屏幕输出日志,1,error;2,error,info;3,error,info,debug;大于4,全部显示
   logClass=2
   
   #守护线程检查周期(单位:毫秒),程序会定期检查线程是否运行,如果线程出现意外错误停止运行则会重新启动
   #在重复尝试响应的次数后,依然失败则关闭程序,-1则会一直尝试
   threadTryTimes=-1
   threadCheckTime=10000
   
   #IP监控线程检查时间(单位:毫秒)
   threadCheckIpTime=60000
   
   #ip文件存储路径
   ipFilePath=ips.txt
   
   ```

   1. 配置文件文件名和位置固定,需要放在jar包的同级目录下,如果程序没有找到配置文件就会生成一个名为"配置文件放在这里.jpg"的空文件.配置文件名为**config.properties**.默认编码是GBK编码,其中的中文在linux中打开可能出现乱码.

   2. 配置文件中除了**发送人地址(sendEmailAddress)**,**发送人邮箱授权码(AuthorizationCode),收件人邮箱地址(harvestEmail)**这三项其他可以不用修改直接默认使用

      但是**发送人邮箱stmp地址(SMTPEmail)**需要根据实际使用的发送邮箱来决定,默认为网易163邮箱.

      软件只测试过网易163邮箱向QQ邮箱发送邮件,其他的并未进行测试.

   3. 日志等级是程序向屏幕发送的日志,设置为0则不会向屏幕输出日志.设置为大于3的整数则会输出所有日志.

   4. ip文件存储是用来存储ip地址信息的文件.程序在运行时会获取当前ip地址并且和ip文件进行比对,如果相同则不会发送ip,如果不同则会发送ip地址并且更新ip存储文件.

   5. serviceName是用来区分服务器的

   

[IP看门狗软件介绍.pdf](https://github.com/w1597964734/ip_watch_dog/files/8845834/IP.pdf)
![IP看门狗软件介绍](https://user-images.githubusercontent.com/42634357/172201085-ac746b25-7eb3-409e-81ca-9fbb878aff91.png)
