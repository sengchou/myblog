---
title: hexo yilia下menu的自定义
date: 2019-10-28 20:37:25
categories: 编程笔记
tags: [hexo,yilia]
---
### 设置分类列表
打开根目录下的配置文件_config.yml，找到如下位置做更改：
```
default_category: uncategorized
category_map:
    编程笔记: programming
    生活随笔: life
    读书学习: learning
```
<!--more-->
category_map:是设置分类的地方，每行一个分类，冒号前面是分类名称，后面是访问路径。
可以提前在这里设置好一些分类，当编辑的文章填写了对应的分类名时，就会自动的按照对应的路径来访问。
---
### 设置主题yilia的导航菜单&绑定到分类目录
打开themes\yilia目录下的配置文件_config.yml，找到如下位置做更改：
```
menu:
  主页: /
  编程笔记: /categories/programming/
  生活随笔: /categories/life/
  读书学习: /categories/learning/
```
yilia主题配置文件_config.yml中的menu时左侧导航的配置，冒号左边的时导航显示文本，右边是分类文章的路径，注意冒号后面有空格。

---
### Cannot GET /categories/***/问题的解决
出现Cannot GET /categories/***/问题，是因为该目录下还没有新建 .md文件。
首先，我们通过hexo n "赤面恐惧症"命令来新建一个页面，在source/_posts目录下找到刚才新建的"赤面恐惧症.md"文件，用hbuilder x打开。

我们看到默认的页面是这样的：
```
---
title: 赤面恐惧症
date: 2019-10-28 20:37:25
tags:
---
```
可以编辑标题、日期、标签和内容，但是没有分类的选项。我们可以手动加入categories:项，或者打开scaffolds/post.md文件，加入categories:,保存后，重新执行hexo n "name"命令，会发现新建的页面里有categories:项了。
然后在categories: 项里输入生活随笔，如下:
```
---
title: 赤面恐惧症
date: 2019-10-28 20:37:25
categories: 生活随笔
tags:
---
```
---
### 生成静态文件
最后执行以下命令生成静态文件启动本地服务预览：
```
   hexo clean
   hexo g
   hexo s
```
打卡浏览器访问localhost:4000预览，Cannot GET /categories/***/问题消失了，界面出现一个标题文“吃面恐惧症” 内容为空的文章页。
其余俩个分类同理解决。