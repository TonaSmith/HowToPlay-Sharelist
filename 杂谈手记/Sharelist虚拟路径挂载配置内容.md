挂载Onedrive

Onedrive有很多的挂载形式

### 1、使用分享ID挂载

- 标识：od

- 内容：分享的文件ID

- 示例：od:s!Apo33BTbGqqHhx3q6Gtb62WI6p59

**使用分享ID挂载的形式最多只支持30条显示结果**

### 2、使用API挂载

- 标识：oda

- 内容：

    - 完整：OneDrive路径->应用ID|应用机钥|回调地址|refresh_token

    - 指定目录向导：OneDrive路径

    - 向导模式：/

- 示例：oda:/

建议使用向导模式，需要注意的是，由于微软的新的安全策略，无HTTPS的网站无法直接被指定为回调地址，因此回调地址可使用中转地址：

[https://reruin.github.io/redirect/onedrive.html](https://reruin.github.io/redirect/onedrive.html)

### 3、链接挂载OneDrive For Business

- 标识：odb

- 内容：分享链接

- 示例：odb:https://caomsacid0-my.sharepoint.com/:f:/g/personal/sunziyang97_caoms_ac_id/Eq3WZR7u8q1LnIDa3miPQOoB1yqrkZEwBjYYcRsS8dGgtg?e=t4MufS

### 4、挂载世纪互联版Onedrive

- 标识：odc

- 内容：

    - 完整：//应用ID/路径?client_secret=应用机钥&redirect_uri=回调地址&refresh_token=refresh_token&tenant=组织名

    - 向导模式：/

- 示例：odc:/

回调地址同样应使用中转地址，组织名为https://***-my.sharepoint.cn/的***部分

## 挂载Google Drive

### 1、通过分享ID挂载

- 标识：gd

- 内容：分享的ID

- 示例：gd:1cEA4umECe_-7aqBvq44AiPYxQ95zP8jr

### 2、通过API挂载

- 标识：gda

- 内容：

    - 完整：//应用ID/root?client_secret=应用机钥&redirect_uri=回调地址&refresh_token=refresh_token

    - 向导模式：/

- 示例：gda:/

建议使用向导模式

## 挂载蓝奏云

- 标识：lanzou

- 内容：密码@分享目录ID

- 示例：

    - lanzou:b471209

    - lanzou:b0bw9myva@9234

## 挂载天翼云盘

### 账号密码挂载（推荐）

- 标识：ctcc

- 内容：

    - 完整：//用户名/文件夹ID?password=密码

    - 向导模式：/

- 示例：ctcc:/

### API挂载

- 标识：ctc

- 内容：

    - 完整：//应用ID/初始文件夹ID?app_secret=应用机钥&redirect_uri=回调地址&access_token=access_token

    - 向导模式：/

- 示例：ctc:/

均建议使用向导模式进行操作

## 挂载本地文件

- 标识：fs

- 内容：文件路径

- 示例：fs:/mnt/video2

这里可以套娃，可以做虚拟目录里的虚拟目录

## 挂载Github

这是个新加的功能，目前只能浏览

- 标识：github

- 内容：

    - 用户名

    - 用户名/Repo

- 示例：

    - github:L-Trump

    - github:L-Trump/scoop-raresoft

## 挂载h5ai

h5ai是另一个轻型个人网盘，套娃开始了

- 标识：h5ai

- 内容：地址

- 示例：h5ai:https://larsjung.de/h5ai/demo/

## 挂载WebDAV

- 标识：webdav

- 内容：http://用户名:密码@地址:端口/路径?参数

- 示例：

    - https://webdavserver.com:1222/path

    - https://username:password@webdavserver.com:1222/path

    - https://username:password@webdavserver.com:1222/?acceptRanges=none

