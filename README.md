# Ubuntu_setting

#在windows上部署Ubuntu教程  

1.打开 PowerShell 以管理员身份运行。  

2.输入命令 wsl --install 来安装 WSL。  
```bash
wsl --install 
```  
3.安装完成后，您可以通过 Microsoft Store 下载所需的 Linux 发行版  如（Ubuntu）  

4.下载完成后，打开终端，确保使用的是 Windows Powershell 而不是 cmd，输入以下内容：  
```bash
Add-AppxPackage -Path <Ubuntu安装包路径> 
```  
   <Ubuntu安装包路径>请写上实际的文件路径。回车即可安装。(建议不要放在C盘，会爆满的）  
   
5.创建新用户和密码  
这一步需要输入用户名和密码，注意：输密码的界面是看不到的，不要认为是哪里出问题了。  
在输入完用户名称和密码之后，就代表安装成功了  
如示例： 
```bash
Installing, this may take a few minutes...
Please create a default UNIX user account. The username does not need to match your Windows username.
For more information visit: https://aka.ms/wslusers
Enter new UNIX username: dwei
New password:
Retype new password:
passwd: password updated successfully
Installation successful!
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

Welcome to Ubuntu 24.04.1 LTS (GNU/Linux 6.6.87.2-microsoft-standard-WSL2 x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Tue Jul 22 23:22:56 CST 2025

  System load:  0.08                Processes:             62
  Usage of /:   0.1% of 1006.85GB   Users logged in:       0
  Memory usage: 5%                  IPv4 address for eth0: 172.26.41.70
  Swap usage:   0%


This message is shown once a day. To disable it please create the
/home/dwei/.hushlogin file.
dwei@Dwei:~$
```
过程说明：  
UNIX 用户创建  
你创建了一个默认的 UNIX 用户，用户名为 dwei，并设置了密码（输入时不可见，需确保两次输入一致）。  
此用户是普通用户，拥有标准权限。需使用 sudo 执行管理员命令。  
安装成功提示  
Installation successful! 表示 Ubuntu 系统已正确部署到 WSL2 环境中。  

首次启动信息：  
系统基本信息：  
Ubuntu 版本: 24.04.1 LTS（长期支持版）  
Linux 内核: 6.6.87.2-microsoft-standard-WSL2  
存储空间: 系统根目录 (/) 占用 0.1%（总 1006.85GB，WSL2 动态分配）  
内存占用: 5%（轻量级）  
网络配置  
WSL2 分配的虚拟 IP: 172.26.41.70（仅主机内访问，无需手动配置）  

你现在可以做什么？  
基本操作：  
输入 Linux 命令（如 ls, cd, cat）直接与 Ubuntu 交互。  
示例：  
```bash
# 更新软件包列表
sudo apt update

# 安装工具（如 git）
sudo apt install git
```

注意事项：
密码安全：  
你设置的 UNIX 密码仅用于 WSL 内部（与 Windows 密码无关），建议记住它（sudo 操作时需要）。

数据持久性：
WSL2 的文件系统独立于 Windows，所有数据保存在虚拟磁盘中（路径为 ext4.vhdx）。注意在转换路径的时候一定要从命令行进行操作，不要擅自更改路径以及误删这个虚拟磁盘。

6.文件互操作  
Windows 上操作 Linux：在 Windows 文件资源管理器左侧可以找到 Linux 的标志，点击 Linux 就可以操作 Linux 文件。  
