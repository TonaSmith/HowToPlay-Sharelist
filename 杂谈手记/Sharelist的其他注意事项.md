## 目录加密

可以在需要加密的目录下新建`.passwd`文件，文件内容如下：

```yaml
type: basic 
data: 
  - user1:password1 
  - user2:aaaaaa 
```

**YAML格式请勿胡乱修改空格**，data中为用户名:密码

## 流量中转

通过中转方式下载网盘内容，在后台管理中可以通过`中转（包括预览）`项开关`中转路径`可指定中转生效的路径（含子路径），如只中转Onedrive，留空则全局生效

**注意，由于功能限制，以下方式强制使用中转模式：**

`OneDrive For Business`、`GoogleDriveAPI`、`Google Drive`

## 忽略文件类型

后台管理，常规设置，`忽略文件类型`可定义忽略的文件类型。例如忽略图片：`jpg,png,gif,webp,bmp,jpeg`。

## 显示README

后台管理，常规设置，将`显示README.md内容`设为启用，当前目录包含`README.md`时，将自动显示在页面。

## 文件预览

后台管理，常规设置，将`详情预览`设为启用即可对特定文件进行预览。目前支持：

### 文档类

由[preview.document](https://blog.xqh.ma/_posts/2020-03-24-%E6%8C%82%E8%BD%BD%E5%90%84%E7%B1%BB%E7%BD%91%E7%9B%98-Sharelist%E7%9A%84%E4%BB%8B%E7%BB%8D%E4%B8%8E%E4%BD%BF%E7%94%A8/plugins/drive.document.js)插件实现，可预览md、word、ppt、excel。

### 多媒体

由[preview.media](https://blog.xqh.ma/_posts/2020-03-24-%E6%8C%82%E8%BD%BD%E5%90%84%E7%B1%BB%E7%BD%91%E7%9B%98-Sharelist%E7%9A%84%E4%BB%8B%E7%BB%8D%E4%B8%8E%E4%BD%BF%E7%94%A8/plugins/drive.media.js)插件实现，可预览图片、音频、视频提供。



后台管理，插件设置，`支持预览的视频后缀`可定义可预览视频类型。

### Torrent

由[preview.torrent](https://blog.xqh.ma/_posts/2020-03-24-%E6%8C%82%E8%BD%BD%E5%90%84%E7%B1%BB%E7%BD%91%E7%9B%98-Sharelist%E7%9A%84%E4%BB%8B%E7%BB%8D%E4%B8%8E%E4%BD%BF%E7%94%A8/plugins/drive.torrent.js)插件实现，为种子文件提供在线预览。

## 文件目录上传

在登录状态（页面顶部会出现上传按钮），可向 本地磁盘(fs)、OneDriveAPI(oda)、GoogleDriveAPI(gda) 上传文件/目录。



目前处于实验性阶段，可能出现各类异常。

## WebDAV导出

可将挂载源以WebDAV方式转出，目前支持列表、下载功能。可在 后台管理->常规设置里 设置webDAV路径。

## 下载链接有效期

后台管理，常规设置，设置`下载链接有效期`后，下载链接将在此时间段内有效。若要关闭此功能，请设置为0。

## Nginx(Caddy)反代注意事项

使用反代时，请添加以下配置。



Nginx

```ini
  proxy_set_header Host  $host;
  proxy_set_header X-Real-IP $remote_addr;
  proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  proxy_set_header X-Forwarded-Proto $scheme;

  proxy_set_header Range $http_range;
  proxy_set_header If-Range $http_if_range;
  proxy_no_cache $http_range $http_if_range;
```

如果使用上传功能，请调整 nginx 上传文件大小限制。

```ini
  client_max_body_size 8000m;
```

Caddy

```ini
  header_upstream Host {host}
  header_upstream X-Real-IP {remote}
  header_upstream X-Forwarded-For {remote}
  header_upstream X-Forwarded-Proto {scheme}
```

