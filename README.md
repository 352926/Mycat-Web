# mycat-web

官方说明请看： [https://github.com/MyCATApache/Mycat-Web/blob/master/README.md](https://github.com/MyCATApache/Mycat-Web/blob/master/README.md)

因为官方已经长时间没有维护，所以我fork下来单独修改几个目前我碰到的bug

1. SQL-监控 - SQL表分析 读写数量不准确的问题 我稍微做了简单的修复，原作者每次把通过show @@sql.sum.table 命令取出来的读写累加了，实际上应该取MAX-MIN。
2. SQL-监控 - SQL解析 当要解析的sql中包含单引号等特殊字符时，因为作者将sql存入button onclick事件属性里，导致解析错误而无法触发事件
3. 打开chrome控制台，发现报了一些前端上的错误，顺便修了
4. TaskStartupLister所启动的所有任务中的execute写成excute，这个不是bug，单词错误只是自己看着不舒服，顺便改掉了
5. SQL-上线 中的语法检测和SQL备份，调整了页面样式，同时做了友善提示，必须安装sqlwatch才能使用

既然已经入了Java的坑，那以后有需求就顺手完善mycat-web！

注意：如果有发现装了Mycat-Server-1.6.1-RELEASE.tar.gz 然后发现没有SQL表分析里只有读次数，写次数永远为0的朋友，这个不是mycat-web的问题
（当时我也以为是mycat-web的问题而找了很久，问了很多地方，后面在一个朋友@高山举目 的帮助下发现mycat-1.6.5BETA版已经修复此问题）。

由于之前觉得mycat-web的统计一直有问题，后来做了测试，发现数据偏差的离谱，因为问了很多地方，找了很久很久。
当时就怀着“再不济自己看源码找问题”的想法，最后果然实现了看源码找到问题并修复了。