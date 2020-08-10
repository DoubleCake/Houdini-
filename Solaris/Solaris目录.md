

# USD Basics

介绍一系列 USD的概念，以及他们如何与Houdini USD 关联

[TOC]



## Overview

USD(Universal)是一种通过组合图层用来描述3D场景的软件和文件格式系统。

>  如:一个描述厨房的USD文件(kitchen.usd)可能会包含道具(chair.usd, table.usd)、灯光(lighting)、角色(characters)等图层文件，将它们合成一个实例。

图层范式的主要功能是无损编辑。你可以从一个现有的场景开始，然后创建一个包含你自己的编辑的新图层。除非他们选择到了你的新图层，否则这些编辑不会影响使用同一场景的其他人。您也可以替换其中一个图层（例如，一个资产的较新版本或更新的灯光），并自动在其上重新应用所有现有的更改。这使得多个部门可以在不互相干扰的情况下进行协作、共享数据和更新资产。

Houdini 的工具和对 USD 的支持被统称为 Solaris。Solaris包括视图中的USD工具架和一种新的网络类型--LOPs（Light Operators）。LOP网络与SOP略有相似，每个节点接受传入的几何体，修改它，并输出新的几何体。在LOPs中，每个节点接受一个传入的USD场景，修改它，然后输出一个新的场景。

USD是一个复杂却非常全面的框架。LOPs的设计使你不需要了解底层的USD结构。然而，在可能的情况下，LOP参数使用了USD术语，有时也只是对USD内置功能的一个简单封装。对 USD 概念和特性的基本理解将使你更容易理解 LOPs。

下面的页面解释了 USD 的基础知识，并解释与 Solaris 如何支持在 Houdini 中使用 USD 。要了解 LOP 节点如何生成 USD，请参见 LOP 如何工作。

## Quick example

​		通常为了提高效率，.usd 或.usdc 文件是二进制编码(binary encoded).为了方便创作者阅读，USD场景描述格式有一个纯文本的等价格式(.usda).下面是一个非常简单的例子.

`box.usd`

```
#usda 1.0
def Cube "box" {
    double size = 4.0
}
```

 

def 定义一个prim关键字，类型味Cube，名字为box( (USD 也有一个类似 def 的 over 操作符，但定义了新 prim 如何覆盖现有 prim) 。这个prim以/box的形式出现在出场景树中(scence tree). Cube prim 是由内置的USD Geometryu模式定义的，有额外的内置模式用于体积、阴影、光照、骨骼动画和渲染(volumes、shading、lighting、skeletal animation、rendering)。你可以通过创建一个自定义模式来扩展USD定义自己的prim类型.

 大括号{ }内的代码定义了新的 prim 的子基元和属性（Cube 有许多属性，但那些我们没有指定的属性将用类型模式的默认值填充）。

在USD术语中，这段代码可以说是 "作者对/box大小的意见"。当组成图层时，如果一个图层包含了一个属性值的定义，那么如果有一个对同一属性更强烈的定义，它将被覆盖。

现在考虑第二个.usda文件。 

`two_box.usd`

```
#usda 1.0
def "box1" ( references = @box.usda@ ) {

}
def "box2" ( references = @box.usda@ ) {
    float size = 2.0
}
```

在这个文件中，我们将上述box.usda文件的内容作为两个prim引用两次。/box1和/box2。/box1将从引用的图层中继承其大小属性。/box2定义一个新的siize。

 在 Houdini 中，通常不会直接操作primitive上的属性值（尽管有一些节点可以进行低级编辑）。相反，LOP 节点会指定更高级别的操作（如 "引入此几何体"、"将此光指向此对象"、"将此道具含有物理学特性放置在此桌上"），LOP 会自动编写相应的 USD。

 实际上，您可以使用Inline USD LOP将纯文本USD代码注入到LOP网络构建中。这有时对调试很有用，但不是你正常工作的方式!

> Tip!
>
> 扩展名为.usd的文件可以是二进制格式或纯文本格式。这样可以方便地将文件从一种表现形式切换到另一种表现形式，而不影响资产跟踪或版本控制。扩展名为.usda的文件应始终为纯文本格式，而.usdc应始终为二进制格式。

