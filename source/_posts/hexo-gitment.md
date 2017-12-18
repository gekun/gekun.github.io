---
title: hexo添加gitment评论
date: 2017-12-04 21:26:44
tags:
- hexo
- gitment
---

参考了网上一些的教程，配置了gitment，记录一下。

## 注册 OAuth Application
到[这里](https://github.com/settings/applications/new)注册一个新的OAuth Application。Authorization callback URL 回调网址填我自己的网址：[http://wxmng.com](http://wxmng.com)。
成功之后会得到一个 client ID 和一个 client secret。

## 修改next主题下_config.yml
以下是我的成功的配置：
```
# Gitment
# Introduction: https://imsun.net/posts/gitment-introduction/
# You can get your Github ID from https://api.github.com/users/<Github username>
gitment:
  enable: true
  mint: true # RECOMMEND, A mint on Gitment, to support count, language and proxy_gateway
  count: true # Show comments count in post meta area
  lazy: false # Comments lazy loading with a button
  cleanly: false # Hide 'Powered by ...' on footer, and more
  language: # Force language, or auto switch by theme
  github_user: myname #这里替换自己的名字
  # 这里有点奇怪，上面备注说的Github ID查询出来是一串数字id值，但是用了就不管用，换名字反而成功了。
  # MUST HAVE, Your Github ID
  github_repo: myname.github.io #这里替换自己的名字
  # MUST HAVE, The repo you use to store Gitment comments
  client_id: 1234567890 #这里填入申请到的client_id
  client_secret: 123abc123abc #这里也是填入申请到的client_secret
  # EITHER this or proxy_gateway, Github access secret token for the Gitment
  proxy_gateway: # Address of api proxy, See: https://github.com/aimingoo/intersect
  redirect_protocol: # Protocol of redirect_uri with force_redirect_protocol when mint enabled

```

对了，这就可以了。
