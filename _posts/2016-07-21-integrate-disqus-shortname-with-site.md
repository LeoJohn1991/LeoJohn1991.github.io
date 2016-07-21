---

layout: post
title:  "博客评论插件 Disqus 的 shortname 相关"
data:   2016-07-21 12:30:00
categories:  Jekyll 杂感
tags: Blog Disqus 

---

* content
{:toc}

博客菜鸟，根据别人教程，用Jekyll框架搭建的博客，刚开始对于评论插件Disqus一直存在配置问题，刷不出来。查过资料，才知道Jekyll的_config.yml中的 disqus_shortname 并非是注册的 Disqus 用户名。本文记录配置评论插件Disqus碰到的问题，及其解决方法。




## Issues

```xml
#Blog-folder/_config.yml
# comments
# two ways to comment, only choose one, and use your own short name
# 两种评论插件，选一个就好了，使用自己的 short_name
duoshuo_shortname: #hygblog
disqus_shortname: xxx
```

disqus_shortname填写错误可能出现以下报错：
**We were unable to load Disqus. If you are a moderator please see our troubleshooting guide.**

此处的disqus_shortname并非是你的Disqus注册的username，Disqus的username和shortname是两个不同的东西。注册Disqus username之后，只能管理你自己账户的评论；而如果要后台管理博客中的评论，需要为Disuqs注册一个shortname，并绑定博客网站。

---

## What's a shortname?

A shortname is the unique identifier assigned to a [Disqus site][disqus-site]. All the comments posted to a site are referenced with the shortname. The shortname tells Disqus to load only your site's comments, as well as the settings specified in your Disqus admin.

### Do I need a shortname?

Yes. To manage comments in Disqus you will need to [register your site][register-site] and [install Disqus on your site][install-to-site] using the shortname registered.

[disqus-site]: http://help.disqus.com/customer/portal/articles/286833-what-is-a-forum-
[register-site]: http://disqus.com/register
[install-to-site]: http://disqus.com/admin/install

### Choosing a shortname

There are a few things to keep in mind when choosing a shortname:

- Your shortname cannot be changed once it is registered. Be sure it's the one you want. 
- Your shortname will not appear publicly. However, your website name will show up in a number of places including (but not limited to): email notifications, the My Disqus tab, the Community tab, and the Discovery box.

*Adjust your website name in forum Settings > General.*

---

## References

1. <https://help.disqus.com/customer/portal/articles/466208>
2. <https://learn.uberflip.com/h/i/135492527-how-to-get-a-disqus-shortname-for-your-hub-youll-need-it>



