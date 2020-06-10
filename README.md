# wbxtjc
外部系统集成_点击跳转第三方网站（跳转到ie浏览器）


1、在数据库中配置相关的登陆信息【网站，用户框，密码框，下拉框，登陆按钮，用户名，密码】。
2、网页使用<a harf exe ：参数>标签
3、把wbxt.py代码使用pyinstaller打包成exe文件  pyinstaller -F -w file_path/file.py --nosonsole
4、跳转谷歌需要 selenium 对应的谷歌浏览器版本与驱动。
5、跳转ie 对应ie版本的驱动；ie不同版本的设置（缩放100%，安全4个配置相同，ie11以上还有其他设置）自行百度；写注册表，以及调用wbxt.exe的bat

注册表：


        Windows Registry Editor Version 5.00

        [HKEY_CLASSES_ROOT\alert]
        @="URL:Alert Protocol"
        "URL Protocol"=""

        [HKEY_CLASSES_ROOT\alert\DefaultIcon]
        @="C:\\zhsw\\wbxt\\wbxt.exe"

        [HKEY_CLASSES_ROOT\alert\shell]

        [HKEY_CLASSES_ROOT\alert\shell\open]

        [HKEY_CLASSES_ROOT\alert\shell\open\command]
        @="cmd /c set m=%l & \"C:\\zhsw\\wbxt\\openIE.bat\" %m% & exit"
        
        
打开exe的bat：



        @echo off
        set m=%m:alert:=%
        set m="%m:separator=&%"
        start "" "C:\\zhsw\\wbxt\\wbxt.exe" %m%
        exit


