杜蕾斯的广告文案一直是业界翘楚，尤其是用诙谐的语句描写不可描述之事时的那种会心一笑，于是我就想知道，杜蕾斯这些年发了哪些有趣的广告。

先将目光瞄准了杜蕾斯的微博，因为大部分的文案也是从微博流传出来。

最近在期中考，加上大数据的作业，_(:з」∠)_我就直接按照「没人给他写信的程序员」的思路来爬杜蕾斯的微博。

讲讲爬虫的大概思路（具体看原文代码）：
使用Chrome模拟手机登录微博，登录之后从Network中复制下自己的cookie
获得想要爬取对象的User ID
先从源码中找出该User的微博有多少页（H5没有页码的概念了，动态加载，爬起来会比较困难，但是我也没有搞清楚手机浏览微博页面的页码是如何存在的，再留个坑/(ㄒoㄒ)/~~）
为了防止被服务器拒绝爬虫，可以设定每爬取一部分页面，就休眠一分钟之类
用requests爬下每一页的源码，然后用BeatifulSoup来保存html并匹配关键标签如[href][a]等
文字部分可以直接保存为文档，而图片则可以先将图片的连接都存进文档中，然后再来下载其中的每一张图片
图片经常会有下载失败的情况，可以从日志或者自己再将失败的连接存下来继续下载

# Python-知乎連接https://zhuanlan.zhihu.com/p/35920573
