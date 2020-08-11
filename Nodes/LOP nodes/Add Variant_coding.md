# Add Variant

将一个或多个变体添加到primitive的变体集。如果primitive不存在，该节点会创建primitive.

## Over view

USD 允许在primitive上存储一个primitive的多个命名变体。每个变体可以有不同的属性、关系和子代。您可以在不同层的不同变体之间切换primitive。每个primitive可以在命名变体集中存储多组变体。

以下是变体的一些常见用例。

* 不同geometry的家族（例如，可以在不同类型的树之间切换的primitive）。

* 细节级别（将同一几何体的分辨率逐渐降低的版本存储为变体，并根据与摄像机的距离进行切换）。

* Houdini 包括创建 LOD 和自动选择 LOD 节点，用于自动化该工作流程。

* 材质分配（存储具有不同材质分配的变体，以允许轻松切换primitive的外观）。

这里是一个图层的例子，它包含一个名为所有者的变体集，其中每个变体的颜色对应于故事中哪个角色拥有该球。

> #usda 1.0
> ()
>
> def Sphere "toyBall" (
>     variants = {
>         string owner = "blake"
>     }
>     append variantSets = "owner"
> )
> {
>     double radius = 1
>     variantSet "owner" = {
>         "andy" (
>         ) {
>             color3f[] primvars:displayColor = [(1, 0, 0)] (
>                 interpolation = "constant"
>             )    }
>     "blake" (
>     ) {
>         color3f[] primvars:displayColor = [(0, 0, 1)] (
>             interpolation = "constant"
>         )   }
>     "sally" (
>     ) {
>         color3f[] primvars:displayColor = [(0, 1, 0)] (
>             interpolation = "constant"
>         )
>
> ​		}
>
> ​	}
>
> }

