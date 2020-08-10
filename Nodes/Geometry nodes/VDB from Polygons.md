# VDB from Polygons 

将多边形曲面或、曲面属性转换味VDB体积元对象



点击查看 标准体机(standard volumes) 与 OpenVDB 体积(OpenVDB volumes)

> 输入的几何体必须是四边形或三角形网格。否则此节点会从多边形中创建一个有符号的SDF场，或密度场.



# Adaptive Prune

此操作符根据摄像机距离修剪元素（点、曲线或打包基元）。

当元素变得更远时，它们会被缩小并最终被删除。

剩余的元素将被放大，以保持元素集合整体的视觉密度。



# Curvature

该VOP计算表面曲率的数量，凸面区域为白色，凹面区域为黑色，平坦区域为50%灰色。这对于掩盖划痕和凹痕等磨损非常有用，因为这些磨损经常发生在凸起的边缘。



# Measure

测量单个元素或较大几何体的面积(area)、体积(valume)或曲率(curvature)，并将结果放入属性中。

> 这个节点可以用来测量曲率，这在游戏开发工作流程中很有用，可以确定地形中类似于悬崖的尖锐区域，这样就可以在这些曲率较高的区域添加岩石或其他物品，使景观看起来更加自然。
>
> 测量面积在角色工作流程中很有用，因为艺术家可以在动画前后测量角色的多边形，以确定多边形网格高度变形的地方。然后，这些信息可以用来混合纹理贴图。
>
> 测量体积经常被用于破坏工作流程中，在破坏工作流程中，物体被击碎。通常很小的碎片可以被删除（体积在一定量以下），因为它们不会影响整体外观，可以加快模拟时间。同样，测量周长对于确定事物在二维空间中的大小也很有用。例如，这可以用于测量一个城市的二维足迹。

# Blast

删除你选择的primitive，points,edges 或 breakpoints.



# Clip

删除或打组平面一遍的几何体，或者沿着平面创建几合体

# Peak

沿着法线移动 primitives,points,edges 或者 breakpoints

> peak操作沿primitives、points、edges或breakpoints的每个法线进行移动。如果没有指定分组，则所有点都沿其法线进行移动。
>
> 使用primitives时，点会沿着primitives的平均法线进行平移。这与沿点的法线平移不同，因为只考虑组中指定的primitives，points的法线属性被忽略。

# Null

> 这个操作没有任何作用。它的作用仅仅是作为一个占位符，以使网络布线更容易，或者允许您引用一个单一的输出SOP，而不必在真正的输出SOP改变时更新对它的所有引用。
>
> 这个SOP通过它的输入不受影响，所以它不做任何处理。添加null不会增加内存使用量（除了 "Cache Input "开启时）。

# Ray

将一个物体的表面投射到另一个物体

> Ray节点从第一个输入的几何体的每个点向其法线方向投射射线，然后将该点移动到射线击中的从第二个输入任何几何体。
>
> 你可以使用这个节点将衣服披在表面上，将一个对象与另一个对象进行收缩包装，以及其他类似的效果。



# Add

创建points 或者polygons，或 将points、polygons 添加到输入

> If an input is specified, this OP adds points and polygons to it as specified below. If no input is specified, then it generates the points and polygons below as a new entity.

如果指定了一个输入，这个OP会按照规定添加点和多边形。如果没有指定输入，则将下面的点和多边形作为一个新实体生成。

* ### Extract points

  ​		与点表达式一起使用时，Add op可以用来从另一个 op 中提取一个特定的点。例如，从geo1的网格SOP中提取第五个点的X、Y和Z值。

  > point("geo1/grid1",5,"P",0),point("geo2/grid1",5,"P",1), point("geo3/grid1",5,"P",2)\

  ​		如果指定了源，以这种方式添加的点会被追加到点列表的最后。点击 op Tile 上的信息弹出窗口，可以了解有多少个点。例如，如果您添加了两个点，并且有347个点（从0到346），您已经添加了最后两个点号。345和346。

* ### Create a specific number of points

  ​		创建一个Add SOP，并将其设置为创建一个点，然后附加一个 copy SOP，并将其复制数量设置为你想要的（可能是动画）点的数量。

  这与其他一些方法不同，即使点的数量为0，也能正确工作。