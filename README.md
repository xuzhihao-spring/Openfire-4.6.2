



Openfire/build -各种文件用于为不同平台创建安装程序
Openfire/distribution -用于将所有零件放在一起的Maven模块
Openfire/documentation-igniterealtime.org上托管的文档
Openfire/i18n -用于管理界面国际化的文件
Openfire/plugins-Maven配置文件，以允许构建各种可用插件
Openfire/starter -一个小模块，可让Openfire在不同平台上以一致的方式启动


构建包括插件的完整项目，请运行以下命令
./mvnw verify


但是，在大多数情况下，仅需要对核心XMPP服务器本身进行更改，在这种情况下，该命令
./mvnw verify -pl distribution -am 
将编译核心服务器及其任何依赖项，然后将其组装成可以运行的东西。

IntelliJ IDEA：


名称：Openfire
使用模块的类路径：启动器
主类：org.jivesoftware.openfire.starter.ServerStarter
VM选项（相应地进行调整）：
-DopenfireHome="E:\Openfire-4.6.2\distribution\target\distribution-base\distribution\target\distribution-base"
-Xverify:none
-server
-Dlog4j.configurationFile="E:\Openfire-4.6.2\distribution\target\distribution-base\lib\log4j2.xml"
-Dopenfire.lib.dir="E:\Openfire-4.6.2\distribution\target\distribution-base\lib"
-Dfile.encoding=UTF-8

您需要先执行mvnw verify才能启动openfire。

其他IDE：
尽管您的IDE可以愉快地编译项目，但是不幸的是，无法在IDE中运行Openfire-必须在命令行中完成。使用Maven构建项目后，只需运行shell脚本或批处理文件即可启动Openfire；
./distribution/target/distribution-base/bin/openfire.sh
.\distribution\target\distribution-base\bin\openfire.bat

将-debug第一个参数添加为脚本将以调试模式启动服务器，并且在必要时您的IDE应该能够连接远程调试器。