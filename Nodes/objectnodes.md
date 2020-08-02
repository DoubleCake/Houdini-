对象网络

Object或 "Scene"级别(/obj/)包含了场景中的 顶级对象如:geometry(几何对象)、skeletons(骨骼)、lights(灯光)、cameras(摄像机)，并允许设置它们之间的空间和层次关系。

对象层是你在场景中放置角色、道具、摄像机和灯光的地方。您可以使用几何节点（SOP）在几何对象节点内为定义角色和道具的皮肤/形状的实际表面建模。

在对象层级将节点连接在一起，可以创建层次关系（"父子关系"）。

![image-20200802192556350](C:\Users\User\AppData\Roaming\Typora\typora-user-images\image-20200802192556350.png)

|图标( ICON)                                                         | 热键(KEY)  |      描述(Description)|
| ------------------------------------------------------------ | ---- | ---- |
| ![image-20200802192657566](C:\Users\User\AppData\Roaming\Typora\typora-user-images\image-20200802192657566.png) | E | 可选择。当此节点关闭时，它在查看器中不可选择。您可以使用这个功能，使您在处理其他对象时，无法意外地选择该对象。 |
| ![image-20200802192923993](C:\Users\User\AppData\Roaming\Typora\typora-user-images\image-20200802192923993.png) | R | 显示。如果此功能关闭，则对象不会出现在查看器中。当显示标志开启时，节点右边的标志会亮起蓝色。 |

## 其他对象标志

![image-20200802193228970](C:\Users\User\AppData\Roaming\Typora\typora-user-images\image-20200802193228970.png)

右键单击节点并打开 "标志 "子菜单来设置这些标志。

Display Origin:

​	在对象的原点显示一个插孔。关闭显示标志也会隐藏千斤顶。

X-Ray

​	使物体在其他几何体后面可见。这用于使人物皮肤内的骨骼可见。