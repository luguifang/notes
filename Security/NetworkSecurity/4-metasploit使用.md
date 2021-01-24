# 4.1 metasploit 渗透测试框架介绍
## 4.1.1 metasploit 简介
    Metasploit是一个渗透测试平台，使您能够查找，利用和验证漏洞。该平台包括Metasploit框架及其商业对手，如Metasploit Pro。
    Metasploit是一个免费的、可下载的框架，通过它可以很容易对计算机软件漏洞实施攻击。它本身附带数百个已知软件漏洞的专业级漏洞攻击工具。。当H.D. Moore在2003年发布Metasploit时，计算机安全状况也被永久性地改变了。仿佛一夜之间，任何人都可以成为黑客，每个人都可以使用攻击工具来攻击那些未打过补丁或者刚刚打过补丁的漏洞。软件厂商再也不能推迟发布针对已公布漏洞的补丁了,这是因为Metasploit团队一直都在努力开发各种攻击工具，并将它们贡献给所有Metasploit用户。

## 4.1.2 metasploit 体系框架
![image](https://github.com/luguifang/notes/blob/main/Security/NetworkSecurity/image/6.png)
  * 基础库: 
    metasploit基础库文件位于源码根目录路径下的libraries目录中，包括Rex,framework-core和framework-base三部分。
    Rex是整个框架所依赖的最基础的一些组件，如包装的网络套接字、网络应用协议客户端与服务端实现、日志子系统、渗透攻击支持例程、PostgreSQL以及 MySQL数据库支持等;
    framework-core库负责实现所有与各种类型的上层模块及插件的交互接口;
    framework-base库扩展了framework-core，提供更加简单的包装例程，并为处理框架各个方面的功能提供了一些功能类，用于支持用户接口与功能程序调用框架本身功能及框架集成模块;
  * 模块:
    模块组织按照不同的用途分为6种类型的模块(Modules):分为辅助模块(Aux)、渗透攻击模块(Exploits).后渗透攻击模块(Post)、攻击载荷模块(payloads).编码器模块(Encoders)、空指令模块(Nops)。
    注: payload 又称为攻击载荷，主要是用来建立目标机与攻击机稳定连接的，可返回shell，也可以进行程序注入等。
  * 插件:
    插件能够扩充框架的功能，或者组装已有功能构成高级特性的组件。插件可以集成现有的一些外部安全工具，如Nessus、OpenVAS漏洞扫描器等，为用户接口提供一些新的功能。
  * 接口:
    包括msfconsole控制终端、msfcli命令行、msfgui图形化界面、armitage图形化界面以及msfapi远程调用接口。
  * 功能程序: 
    metasploit还提供了一系列可直接运行的功能程序，支持渗透测试者与安全人员快速地利用metasploit框架内部能力完成一些特定任务。比如msfpayload、msfencode和msfvenom可以将攻击载荷封装为可执行文件、C语言、JavaScript语言等多种形式，并可以进行各种类型的编码
# 4.2 Metasploitable2靶机
## 4.2.1 Metasploitable2 靶机系统介绍
    Metasploitable2虚拟系统是一个特别制作的ubuntu 操作系统，本身设计作为安全工具测试和演示常见漏洞攻击。版本2已经可以下载，并且比上一个版本包含更多可利用的安全漏洞。这个版本的虚拟系统兼容VMware，VirtualBox和其他虚拟平台。
    默认用户名密码：msfadmin msfadmin
# 4.3 metasploit 基本命令
    * 依赖于postgresql 数据库，通过命令行启动时需要先启动数据库
## 4.3.1 命令分类
    通过help查看帮助，可以对msf有个整体认识，可以看到msf相关命令可以分成以下类型:
    * Core Commands  核心命令
    * Module Commands  模块命令
    * Job Commands  后台任务命令
    * Resource Script Commands  资源脚本命令
    * Database Backend Commands  数据库后端命令
    * Credentials Backend Commands  证书/凭证后端命令
    * Developer Commands  开发人员命令
    
## 4.3.2 常用命令

# 4.4 攻击步骤
    * use exploit ->  set option(端口、ip地址等) -> set payload ->  set payload的监听地址和端口 -> run
![image](https://github.com/luguifang/notes/blob/main/Security/NetworkSecurity/image/7.png)
    


