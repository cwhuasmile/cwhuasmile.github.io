# Windows 2012使用IIS发布网站设置方法

1. 打开IIS，右键点击网站--添加网站，然后进入配置

2. 网站的基本设置，首选选择网站所在目录的路径，然后给网站起个名字（名字可以任意起），最后是应用程序池的选择，也可以用自动生成的新的，也可以用配置过的，一般用新生成的，各个网站之间就不会相互影响了。

3. 右键网站(刚才新建的站点)--编辑权限，这里可以设置该网站的端口和绑定的域名，我们这里是内网设置，只用设置端口。默认80端口已经被默认的Default Web Site站点使用，可将Default Web Site站点的端口设置为其它的。

4. 网站一般要添加IIS_USER权限，右键网站(刚才新建的站点)--编辑权限，添加需要的权限，如果有写入文件操作，需要给与写入权限。

5. 应用程序池的设置，如果是.net程序，需要在应用程序池设置.net版本。点击应用程序池(在‘网站’的上面)，把右侧的DefaultAppPool停用，否则会跟刚才新建的站点默认主页冲突。

6. 设置网站的默认页，即启动默认打开的页面(点击刚才新建的网站，右侧的‘默认文档’)。

7. 可以右键(刚才新建的网站)--管理网站--浏览，地址栏会显示您配置的端口，到这里网站已经发布完成了。

   链接地址：https://jingyan.baidu.com/album/6dad5075031a16a123e36ee5.html

