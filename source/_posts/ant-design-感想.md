---
layout: posts
title: ant-design 感想
date: 2019-07-03 14:25:27
tags: ["react", "ant-design"]
---
在react框架下使用的ui框架并不多，曾经使用过bootstrap，但是bootstrap使用起来并不舒适，一方面是因为文档的关系，但是主要原因还是因为其样式不美观，到最后做出的成品还是需要经过大量的样式修改才可以，但是ant-design是没有这方面问题的，引入后所有组件自带的样式能应付大多数的需求。
不过有一句提一句，虽然阿里推出的是ant-design，但是在使用后就会渐渐发现，这个玩意竟然存在使用前提，react版本基本上需要相对比较新得版本才行，不然会导致部分组件完全无法使用（不过应该也是有绕行方案的）。另一点，ant-design的衍生产品ant-design-pro的确是很好的一个组件库，一方面阿里本身提供了一个已搭建完成的项目例子（不过这个也是仁者见仁，毕竟没有通过命令行去初始化项目），另一方面其中的组件也提供单独引用，且易用性上要远远超过了ant-design本身的一些组件。
然而比较痛苦的一点，无论是在何种ui框架下，react对于表单的不友好仍然是比较头疼的，毕竟相比vue来讲，其状态控制要更严格，这可能也与文化上的差异有点关系……毕竟vue是本土框架。

那么*如何在react下写出一个优雅的表单呢？*
