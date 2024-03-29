此版本是原始版本，客户端是Qt5.15.2，服务器是centos7。

Qt6版本地址（有时间持续更新代码|优化代码|重构代码|重写代码...）：https://github.com/swansfought/EChat-Qt6

---
- [EChat概述](#echat--)
  * [应用技术](#----)
  * [代码结构](#----)
  * [重点待改进点](#----)
- [功能模块（图片形式展示）](#------------)
  * [1. 登录注册模块](#1-------)
  * [2.消息收发模块](#2------)
  * [3.联系人管理模块](#3-------)
  * [4.文件管理模块](#4------)
  * [5.用户配置模块](#5------)
  * [6.用户反馈模块](#6------)
- [部分截图](#----)
  * [系统登录界面效果图](#---------)
  * [好友消息收发界面效果图](#-----------)
  * [好友申请列表效果图](#---------)
  * [个人和好友信息展示效果图](#------------)
  * [发送图片效果图](#-------)
  * [创建群聊效果图](#-------)
  * [用户配置界面图](#-------)
 
## EChat概述
​	Qt即时通讯软件EChat（Qt版本是5.15.2）。23年大四下毕业设计，本项目主要提供稳定且支持多平台的通讯软件，以提升用户体验。至于代码方面也存在很多问题的，很多其实需要重写和优化的。
 
### 应用技术
  Linux 、 C/C++ 、 QT 、 Socket 、 epoll 、 CMake 、 QSS 、 JSON 、jsoncpp 、 HTML 、 MySQL 、 SQLite 。

### 代码结构
  服务器代码：epoll+多线程实现高并发，数据存储使用MySQL
  
  客户端代码：qt编写，数据本地存储使用SQLite
  
### 重点待改进点
  列举服务器的一些主要问题，客户端的以及服务器其他的问题可以自行进行完善和补充哈！
  
  1、多线程方面：使用线程池去管理线程的创建和销毁，提高服务器处理效率；
  
  2、内存管理方面：对于请求报文(json)这种大小相对固定的数据不必每次读取申请内存，一定程度上有助于提高服务器处理效率；
  
  3、文件收发方面：先说结论，正常都是支持10M以内的文件收发，10M以上的服务器端的程序容易崩。文件就txt，图片应该都是可以的，主要是像docx、pdf和zip等这些编码没研究明白。至于程序崩溃了怎么办，我这里恰好这里采用了systemd去管理服务端程序，一定程度上缓解了此问题🥲。

  4、数据安全方面：消息收发都是明文发的哈，没有使用加密机制（如SSL）去确保消息的私密性；用户密码方面数据库中使用MD5加密，本地如果勾选保存密码，则采用的是字符密钥加密算法存储在配置文件中。
  
## 功能模块（图片形式展示）

### 1. 登录注册模块

![image](https://github.com/swansfought/EChat/blob/main/%E9%83%A8%E5%88%86%E6%88%AA%E5%9B%BE/md/%E7%99%BB%E5%BD%95%E6%B3%A8%E5%86%8C%E6%A8%A1%E5%9D%97%E5%A4%84%E7%90%86%E6%B5%81%E7%A8%8B%E5%9B%BE.png)


### 2.消息收发模块

![image](https://github.com/swansfought/EChat/blob/main/%E9%83%A8%E5%88%86%E6%88%AA%E5%9B%BE/md/%E6%B6%88%E6%81%AF%E6%94%B6%E5%8F%91%E5%8A%9F%E8%83%BD%E6%A8%A1%E5%9D%97%E5%9B%BE.png)


### 3.联系人管理模块

![image](https://github.com/swansfought/EChat/blob/main/%E9%83%A8%E5%88%86%E6%88%AA%E5%9B%BE/md/%E8%81%94%E7%B3%BB%E4%BA%BA%E7%AE%A1%E7%90%86%E6%A8%A1%E5%9D%97%E5%9B%BE.png)


### 4.文件管理模块

只列出已实现的

![image](https://github.com/swansfought/EChat/blob/main/%E9%83%A8%E5%88%86%E6%88%AA%E5%9B%BE/md/%E6%96%87%E4%BB%B6%E7%AE%A1%E7%90%86%E6%A8%A1%E5%9D%97%E5%9B%BE.png)


### 5.用户配置模块

只列出已实现的

![image](https://github.com/swansfought/EChat/blob/main/%E9%83%A8%E5%88%86%E6%88%AA%E5%9B%BE/md/%E7%94%A8%E6%88%B7%E9%85%8D%E7%BD%AE%E5%8A%9F%E8%83%BD%E6%A8%A1%E5%9D%97%E5%9B%BE(%E5%9B%BE%E4%B8%AD%E4%B8%BA%E5%B7%B2%E5%AE%9E%E7%8E%B0%E7%9A%84).png)


### 6.用户反馈模块


## 部分截图
### 系统登录界面效果图

![image](https://github.com/swansfought/EChat/blob/main/%E9%83%A8%E5%88%86%E6%88%AA%E5%9B%BE/%E7%B3%BB%E7%BB%9F%E7%99%BB%E5%BD%95%E7%95%8C%E9%9D%A2%E6%95%88%E6%9E%9C%E5%9B%BE.png)


### 好友消息收发界面效果图

![image](https://github.com/swansfought/EChat/blob/main/%E9%83%A8%E5%88%86%E6%88%AA%E5%9B%BE/%E5%A5%BD%E5%8F%8B%E6%B6%88%E6%81%AF%E6%94%B6%E5%8F%91%E7%95%8C%E9%9D%A2%E6%95%88%E6%9E%9C%E5%9B%BE.png)


### 好友申请列表效果图

![image](https://github.com/swansfought/EChat/blob/main/%E9%83%A8%E5%88%86%E6%88%AA%E5%9B%BE/%E5%A5%BD%E5%8F%8B%E7%94%B3%E8%AF%B7%E5%88%97%E8%A1%A8%E6%95%88%E6%9E%9C%E5%9B%BE.png)


### 个人和好友信息展示效果图

![image](https://github.com/swansfought/EChat/blob/main/%E9%83%A8%E5%88%86%E6%88%AA%E5%9B%BE/%E4%B8%AA%E4%BA%BA%E5%92%8C%E5%A5%BD%E5%8F%8B%E4%BF%A1%E6%81%AF%E5%B1%95%E7%A4%BA%E6%95%88%E6%9E%9C%E5%9B%BE.png)


### 发送图片效果图

![image](https://github.com/swansfought/EChat/blob/main/%E9%83%A8%E5%88%86%E6%88%AA%E5%9B%BE/%E5%8F%91%E9%80%81%E5%9B%BE%E7%89%87%E6%95%88%E6%9E%9C%E5%9B%BE.png)


### 创建群聊效果图

![image](https://github.com/swansfought/EChat/blob/main/%E9%83%A8%E5%88%86%E6%88%AA%E5%9B%BE/%E5%88%9B%E5%BB%BA%E7%BE%A4%E8%81%8A%E6%95%88%E6%9E%9C%E5%9B%BE.png)


### 用户配置界面图

![image](https://github.com/swansfought/EChat/blob/main/%E9%83%A8%E5%88%86%E6%88%AA%E5%9B%BE/%E7%94%A8%E6%88%B7%E9%85%8D%E7%BD%AE%E7%95%8C%E9%9D%A2%E5%9B%BE.png)


