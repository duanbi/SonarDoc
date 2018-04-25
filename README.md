# SonarDoc

先看一下效果图
![Alt text](https://github.com/duanbi/SonarDoc/blob/master/效果图01.png)
![Alt text](https://github.com/duanbi/SonarDoc/blob/master/效果图01.png)
![Alt text](https://github.com/duanbi/SonarDoc/blob/master/效果图01.png)
![Alt text](https://github.com/duanbi/SonarDoc/blob/master/效果图01.png)

SonarQube安装和使用

下载地址：
SonarQube ：http://www.sonarqube.org/downloads/
sonar-scanner-msbuild：https://docs.sonarqube.org/display/SCAN/Analyzing+with+SonarQube+Scanner+for+MSBuild


参考：
https://www.cnblogs.com/qiaoyeye/p/5249786.html

http://www.cnblogs.com/jingridong/p/6513884.html

https://docs.sonarqube.org/display/SCAN/Analyzing+with+SonarQube+Scanner+for+MSBuild


安装前提：
1、必须安装JDK8+

2、俩个安装压缩包需要解除阻止


使用过程中遇到的问题：

1、在sonarqube-7.0\conf文件下，修改配置文件，端口（默认是9000，如果端口被占用则需要修改），地址，及数据库文件。
	遇到问题：本人使用的是Sql Server 2014，配置数据库采用的是sa账号，上传检测产物时总是失败，数据库中也没有任何数据。最后创建了一个新的账号，给了最高权限结果成功了。
	
2、在sonarqube-7.0\bin\windows-x86-64中有几个bat文件，InstallNTService，StartNTService，StartSonar，StopNTService，UninstallNTService和一个exe
	第一次我运行的是StartSonar.bat文件，一切完好， 没有任何问题， 成功的打开了：http://localhost:9800 页面，但看SonarQube服务的时候，未启动，就开始运行启动服务的bat文件， 启动失败，已被启动，
	重复关机重启尝试， 发现StartNTService，StartSonar好奇怪，如果有时候开机后SonarQube启动， 运行StartSonar 不报错， 有时候保存（被占用）。
	
	
3、	分析报告生成及上次传
	按照博客中提到的：使用SonarQube.Scanner.MSBuild.exe， 试了俩次发现都在 最后一步 end 失败，  不知道啥原因 就是 submint 失败。
	可能被误导了，最后在SonarQube.Scanner.MSBuild.exe begin 中提示使用SonarScanner.MSBuild.exe  结果竟然成功。
	
	

最后总结：

1、遇到问题，(前提)看日志，在网上找原因。
2、（个人）你遇到的问题，早有很多人遇到， 也有很多解决方案， 但是有些是你采用的老版本方法去实现新版本， 有可能会成功有可能不成功， 这是就要到官网对应的版本文档寻找答案， 有事也安装时有提出。


