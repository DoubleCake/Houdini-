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

* 将一个 LOP 网络中的有用位打包成可复用的数字资产。
## Ways of working with USD

你可以用不同的方式使用USD Solaris，这决定于你工作室以USD的中心都，以及在整个pipeline中的位置。例如，在下列工作流程中以不同方式使用HIP文件和USD文件

* 从一个空白的HIP文件开始，建立一个LOP网络，在最后写出USD(如，烘焙出的模拟geometry)供其他人使用
* 从一个USD文件开始，将其摄入LOP网络，修改、添加到LOP网络中，最后写出修改后的USD
* 创建HIP文件，在LOP网络中生成USD资产。然后有 "更高级别的 "HIP文件，使用LOP来加载这些资产，并将它们组合成一个更大的场景/镜头。

* 使用 USD 时要记住的一件重要事情是，"一个资产 "并不只是指一块几何图形，或一个贴图。一个 USD 资产可能代表了几个层的创建和修改，并与其他文件（如纹理或导入的几何体）有关系。

## Layers

