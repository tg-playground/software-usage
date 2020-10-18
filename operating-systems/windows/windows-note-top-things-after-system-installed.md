# Top Things After Windows System Installed

Content

- System Settings
  - Backup
  - Using English Language Package
  - Update System Driver
  - Update hosts
- Over GFW
- Installing Office Software
- Installing Professional Software
  - Tools
  - Service
- Active Windows System and Software



## System Settings

### Updating and Installing System Driver

- Using `DriverGenius` or 联想驱动管家 / 联想电脑管家 to install drivers.
- Directly installing downloaded drivers exe.

### Add OS language

Installing English Language Package

Win + x --> settings --> Time & Language --> left panel: Language --> Add preferred language --> English (United States)

### Add OS keyboard

Win + x --> settings --> Time & Language --> left panel: Language --> Preferred language --> Add a language: select Chinese --> Install language

### Setting OS Time Zone

Win + x --> settings --> Time & Language --> left panel: Date & Time --> Time Zone: selected UTC+8:00 Beijing

### Setting OS Character Encoding

Win + x --> settings --> Time & Language --> left panel: Region --> Related Setting (Additional date,time & regional settings) --> Region --> Administrative --> Language for non-Unicode programs --> Change system locale -->  Current system locale: select Chinese (Simplified, China) and checked Use Unicode UTF-8 for worldwide language support --> Restart OS

### Setting Taskbar

Unpin from taskbar
Unchecked: show task view button, show cortana button
Search: Show search icon

### Setting File Explorer

View --> checked: file name extensions, hidden items

### Setting Windows Colors

Windows mode and app mode

Win + x --> settings --> Personalization --> Colors --> Choose your color: Dark

### Setting Desktop Icons

Right Click --> View --> Small icons

### Setting Power Options

Win + X --> Power Options --> Sleep

On battery power: 1 hour
On Plugged in: Never

Additional power settings --> Choose what closing the lid does --> When I close the lid: Do nothing --> Save changes


### Windows Update

Win + X --> settings --> Update & Security --> Windows Update --> Check Windows Update

### To disable Intel Graphics shortcuts

Open "Intel Graphics Command Center" or "Intel HD Graphics Control Panel" by Windows + S

System --> HotKeys

- Ctrl + Alt + Left => Ctrl + Alt + F2
- Ctrl + Alt + Right => Ctrl + Alt + F3


### Backup system in external disk

Win + x --> settings --> update and security --> backup --> Go to Backup and Restore(Windows7) --> Set up backup --> Let me choose


### Update hosts

`C:\Windows\System32\drivers\etc\hosts`

To see hosts.md example

### Setting Pin to Quick Access

- <Taogen>(User Dir)
- GitRepositories
- Software Resource
- Pro
- etc
- Download
- blog/my-draft (git repository)
- software-usage (git repository)

### Move User Dir Backup to Current User Dir

- .m2
- .ssh
- .gitconfig
- AppData/Roaming
  - JetBrains
  - npm-cache.7z

## Installing Office Software

**Over GFW**

- v2ray

Web Browser

- [x] Chrome
  - Sign in & sync.
- [x] Firefox

IM

- WeChat
  - Update file save path
- [x] QQ
  - Update file save path
- Dingtalk

File Viewer

- Sumatra PDF

File Handler

- [x] 7zip

Download

- Thunder
  - Update download path
  - Unchecked 接管所有浏览器

Office

- [x] Microsoft Office
- [x] QTTabBar
  - Setting: Open File Explorer -> menu: View -> Option -> QTTabBar

Work

- Pomotodo
  - Unchecked: play working sound
  - Checked: Start on system startup

## Installing Professional Software

### Tools

Editor

- Sublime Text
- [x] Typora

languages 

- [x] JDK
  - Add JAVA_HOME system variable to path
  - Verify by `java -version`
- [x] Python
  - Verify by `python -V`
- [x] Node.js
  - Verify by `node -v`
  - Update `npm` mirror: 
    - Open cmd with administrator
    - Setting: `npm config set registry https://registry.npm.taobao.org`
    - Verify: `npm config get registry`
    - Setting: `npm config set cache D:\$UserData\AppData\Roaming\npm-cache --global`
    - Verify: `npm config list`
  - Install Hexo
    - Installing: `npm install hexo-cli -g`
    - Verify by `hexo -v`

project Management

- apache maven
  - Add M2_HOME system variable to path
  - Verify by `mvn -version`
  - Config `/conf/settings.xml`, set `<mirror>` to Aliyun mirror , set `<localRepository>` to `D:\$UserData\.m2\repository`.
- [x] git
  - generate key in ~/.ssh/id_rsa, id_rsa_pub
  - Add public key to GitHub
  - Verify by `ssh -T git@github.com`. Result `Hi tagnja! You've successfully authenticated, but GitHub does not provide shell access.`

IDE

- Intellij IDEA
  - Setting refer to software usage idea folder
- [x] WebStorm
  - Installing WebStorm.exe
  - Delete AppData/Roaming/JetBrains/WebStorm
  - Running WebStorm
  - Active WebStorm 
- Eclipse
- MyEclipse

Database Client

- Heidisql
- FastoRedis

Design

- XMind
- Project
- PowerDesigner

Others

- [x] Postman
- [x] Xshell
- [x] Xftp
- TeamViewer

ELK

- elasticsearch
- kibana
- logstash

Others

- Sandboxie

### Service

Web Server

- Apache Tomcat

Database Systems

- MySQL
  - MySQL Server, MySQL Workbench, Connector/J
- Redis


## Active Windows System and Software

- Windows
- Microsoft Office
- Intellij IDEA. active by 挑粪王子公众号
- Sublime Text search from cn.bing.com



## More Software

Office Software

- Microsoft Visio
- Microsoft Project

--END--