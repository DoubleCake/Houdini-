# How LOPs work

Solaris LOP(lighting operator) 节点是如何生成 /modify USD.

[TOC]




## Procedural USD

编辑 USD 涉及到对 prims 和 prims 上的属性树进行更改。一个能让您在树上选择primitivees并直接编辑参数的程序可能比Houdini更容易理解，因为houdini的生成/编辑树是生成一个程序化的节点网络。然而，程序化范式对于处理 USD 有几个引人注目的优势。

* 动态地生成USD。

USD本质上不是动态的。Solaris 可以作为 USD 上面的一个动态层，根据表达式、全局变量、脚本、数据库查询或其他任何你需要的输入，生成不同的 USD 输出。

* 程序化地生成USD。

例如，如果你想要一个灯的100个实例，你不需要写100个引用，只需要使用for-each循环创建它们。

* 在更高的层次上工作。

例如，USD目前没有约束。Solaris 提供了 Look At 等约束，这些约束在 LOP 网络中是 "活的"，但当你输出 USD 时会被baked out。

将 LOP 网络中有用的位子捆绑成一个可重用的数字资产。