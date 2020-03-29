---
title: git的基本使用
date: 2020-03-26 18:54:00
tags:
---
### 基本概念
git:简单的来说就是一个版本控制系统，通过一系列的操作，将我们的项目代码放在git的服务器上面。
github：是基于B/S架构的版本控制系统，我们通过浏览器来展示和操作我们的项目数据，服务器还是git服务器。
git客户端，是基于C/S架构的版本控制系统，在安装git客户端后，通过命令行或者图形界面进行操作。
本文主要讲的是通过git客户端的命令行来操作。

### 准备阶段
1. 安装客户端

   * 百度搜素git，即可进入git官网，下载安装即可。
   * 只有安装了git客户端，才能够使用git命令。
   * git客户端提供三种操作工具
      * git bash 是基于linux命令的控制台
      * git cmd 是基于windows命令的控制台
      * git gui 是基于图像化界面的控制台
2. 命令操作

  * 使用命令将客户端和git账号关联

    * git config –global user.name “用户名”
    * git config –global user.email “邮箱”
    * 注意：以上使用global命令，表示是全局配置，该配置生效之后，以后就不需要手动关联了。
 * 然后让git服务器对该git客户端进行授权，该授权是基于ssh协议，在github上配置公用密匙。

    * ssh-keygen -t rsa -C “github邮箱地址”

    * 控制台会输出.ssh文件夹和id_rsa的位置（注意：.ssh是隐藏文件夹）
      * ![图片](https://github.com/yuwen1024/myImages/blob/master/ssh%E7%A0%81%E7%9A%84%E4%BD%8D%E7%BD%AE.jpg)

    * 将id_rsa中的内容全部复制到github上。具体设置如下

      * 打开setting
        * ![图片](https://github.com/yuwen1024/myImages/blob/master/%E8%AE%BE%E7%BD%AEssh1.jpg)
      * 打开SSH
        * ![图片](https://github.com/yuwen1024/myImages/blob/master/%E8%AE%BE%E7%BD%AEssh2.jpg)

      * 新建SSH key
        * ![图片](https://github.com/yuwen1024/myImages/blob/master/%E8%AE%BE%E7%BD%AEssh3.jpg)

      * title是说明这个密匙是干嘛用的，随便写。key里面放入id_rsa的数据
        * ![图片](https://github.com/yuwen1024/myImages/blob/master/%E8%AE%BE%E7%BD%AEssh4.jpg)

  * 这样，git客户端和服务器就关联上了，我们就可以使用git客户端来上传和克隆项目文件了

### 使用git来上传本地文件

#### 上传流程
* 先将要上传的文件放入缓存区中，然后从缓存区中上传到git仓库
* 流程图如下
  * ![图片](https://github.com/yuwen1024/myImages/blob/master/git%E4%B8%8A%E4%BC%A0%E6%B5%81%E7%A8%8B%E5%9B%BE.jpg)
* 先建立本地仓库，说白了就是磁盘里面的文件夹
* 然后使用git bash定位到该文件夹，最简单的方法就是在文件夹里面直接打开git bash
* 使用 git init命令建立缓存区
  * git init命令会在本地仓库中建立一个.git的文件夹，该文件夹里面存放着项目的所有版本信息
* 从本地仓库到缓存区
  * 使用 git add 文件名（单一文件）或者 git add * （所有文件）来将文件放入缓存区中
  * 使用 git commit -m “版本信息的解释”
* 从缓存区到git服务器
  * 需要在github上面建立一个仓库
  * 如果是第一次上传的话需要将本地仓库和git服务器仓库绑定起来
    * git remote add origin 仓库地址。这条指令会将本地仓库和git仓库绑定起来
    * git push -u origin master。将缓存区的文件上传到服务器仓库
  * 第二次以上上传就比较方便,直接使用 git push即可

### git其他基本命令
* 克隆文件
  * 使用 git clone 仓库地址，来克隆该仓库中的所有文件
* 更新项目
  * 使用 git pull命令来更新项目
* 恢复文件
  * 如果本地仓库中文件误删或者误操作了，可以从缓存区中恢复，前提是文件已经放入了缓存区了也就是git add *
  * 使用 git checkout命令即可
* 查看当前本地仓库和缓存区中文件的区别
  * 使用 git diff命令，控制台会展示出哪个文件被修改了，修改的地方是什么
* 查看已经提交到缓存区的历史版本
  * git log命令会展示出所有已经提交到缓存区的版本
* 恢复文件到指定的版本
  * git reset –hard + 版本号。版本号在git log中会有
* 其他命令
  * clear 清屏操作   

### 总结
* git是一个非常方便的代码托管平台，不管是个人还是公司团体，git都能有效的控制版本。github界面很漂亮，看的很舒服。熟悉了git的基本指令，我们就能很好的使用git工具了。
