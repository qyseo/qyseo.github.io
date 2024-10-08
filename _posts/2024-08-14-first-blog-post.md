---
layout: post
categories: write
title: "Github Page搭建时遇到的坑"
author: 青衣
date: 2024-08-14 13:28:01 +0800
tags: blog seo
---

### 准备好了

> 头篇文章，接下来我可能会写很多有意思的东西，希望你也有这样的感觉！
>
> by 青衣2024年8月14日

#### 问题记录：

星期三 08:00

写本地 markdown 的时候需要在头部定义如上，但是是 markdown 的源模式还是啥，如果是源模式切换到预览的时候，马上就变了啊，而且变得很难看，我不知道github page的自动部署能不能成功。



星期三 14:09

根据步骤安装好jekyll，配置完`_config.yaml`普遍都不会有什么问题。

但特别需要留意的是之后写的每篇文章，都需要在markdown的源模式（如果你也是使用typora）下贴上如下所谓的`front matter`。

经过数次测试，才摸索出来这几个字段都是需要填写的，而根据原主题作者的写法，是错误的，搜索时发现错误老早就存在，但人没更新！

所以这就是最后终的一套流程，终于完善。

```text
---
layout: post
categories: write
title: "Github Page搭建时遇到的坑"
author: 青衣
date: 2024-08-14 13:38:01 +0800
tags: blog seo
---
```



1. 后续更新：果然没成功
2. 测试了8次头部 front matter，首页总算是显示出文章并且可以正常访问
3. 统计一下：上传部署大约需耗时：1分钟左右，相应网站收到更新提示需耗时：13分钟左右

细小的问题上往往更容易出错，毕竟大问题普遍都是遇不到的。

> 更新：

2024年8月22日，为本地仓库新建了images图片文件夹，以方便存放图片，下面是测试

![测试图片](../images/cn_dmr_radio_banner.jpg_n.webp)