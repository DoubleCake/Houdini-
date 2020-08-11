#  Clip geometry node

移除或组合平面一侧的geometry，或沿平面折皱geometry.

[TOC]

当 Keep 不是 "All primitives "时，此运算符会尝试剪切平面上方或下方的所有输入基元，如果剪切会破坏基元的结构（geometry、particle system），则会直接删除primitive。

您可以将此运算符用作建模工具，或手动剪裁视场外的多边形，以降低场景复杂性。



> 距离参数的意义在Houdini 5中发生了变化。你可能需要在旧的 hip 文件中否定该值。

## Using Clip

1. 选择你想要clip的对象Select the object you want to to clip.

2. 按下polygon 中的 ![img](http://127.0.0.2:48625/icons/SOP/clip.svg)[Clip](http://127.0.0.2:48625/nodes/sop/clip.html) 工具.

3. 通过移动夹子手柄或在手柄单击`鼠标右键`，并在对齐手柄菜单中选择一个轴，指定您希望对象被裁剪的平面。

   这个工具会自动裁剪对象的一半。移动夹子手柄可以让改变对象被剪裁的程度。

![img](http://127.0.0.2:48625/images/shelf/clip.png)

## PARAMETERS

| Group(组)              | 输入geometry被裁剪的子集                                     |
| ---------------------- | ------------------------------------------------------------ |
| Keep(保留)             | **平面上的primitives**保留平面正侧的几何体，删除另一侧的几何体.<br>**平面下的primitives**保留平面负侧的几何体，删除另一侧的几何体.<br>**保留所有的primitives:**沿着平面在输入的几何体上切割新的边缘，但不删除几何体。这个操作只切割多边形和多条线。 |
| Origin(源)             | 剪切平面来源                                                 |
| Distance(距离)         | 沿着法线移动剪切平面的距离                                   |
| Direction(方向)        | 剪切平面的法向量方向                                         |
| 创建组(Create Groups)  | 为被裁剪的geometry生成组                                     |
| (平面以上）Above Plane | 为剪切平面以上命名                                           |
| (平面以下）Below Plane | 为剪切平面以下命名                                           |
| 删除没有连接的点       | 如果不属于任何primitive的点在剪接平面的错误一侧，它们将被删除。 |



















## EXAMPLES

Load Launch

[ClipParticle](http://127.0.0.2:48625/examples/nodes/sop/clip/ClipParticle.html)Example for [Clip](http://127.0.0.2:48625/nodes/sop/clip.html) geometry node

This is a very basic example of how the Clip SOP can be used to control particle flow by cutting it with an infinite plane.

Play animation to see the effects.

Load Launch

[ClipVariations](http://127.0.0.2:48625/examples/nodes/sop/clip/ClipVariations.html)Example for [Clip](http://127.0.0.2:48625/nodes/sop/clip.html) geometry node

This network compares the various ways in which the Clip SOP can be used with geometry. Depending on what parts of the clipped geometry we want to keep, different effects are achievable.

The Clip SOP can also be used as a grouping tool by specify group boundaries with clip planes.

Clip planes can be animated. Play the animation to view the results.

| See also | [/nodes/sop/cookie](http://127.0.0.2:48625/nodes/sop/cookie.html)[![img](http://127.0.0.2:48625/icons/SOP/polysplit.svg) PolySplit](http://127.0.0.2:48625/nodes/sop/polysplit.html)[![img](http://127.0.0.2:48625/icons/SOP/edgedivide.svg) Edge Divide](http://127.0.0.2:48625/nodes/sop/edgedivide.html)[![img](http://127.0.0.2:48625/icons/SOP/surfsect.svg) Surfsect](http://127.0.0.2:48625/nodes/sop/surfsect.html) |
| -------- | ------------------------------------------------------------ |
|          |                                                              |