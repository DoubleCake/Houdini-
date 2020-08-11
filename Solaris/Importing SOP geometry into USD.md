# Importing SOP geometry into USD

 Houdini如何将SOP几何转换为USD的详细信息，以及如何控制流程。 

## Overview

* SOP Import LOP将SOP geometry到LOP网络的USD阶段。它有可能设置如何转换geometry。

* USD Configure SOP 在 SOP 几何图形中创建对应于 SOP 导入 LOP 设置的属性。您可以设置 LOP 使用每个属性（如果存在），和/或在 LOP 上明确设置参数，覆盖相应的属性。

除了SOP导入LOP和USD配置SOP上的参数外，您还可以使用各种SOP属性来影响导入器转换geometry的方式，如下文所述。



## Hierarchy

在SOP层面上，Houdini几何体从根本上不存在层次关系（在Houdini中，模型之间的层次关系是在对象层面上定义的）。

在没有路径定义属性的情况下。

* 所有多边形面都包含在一个名为 mesh_0 的单一多边形网格。

* 任何具有等价 USD  prim的 SOP prim（如 Sphere 和 Volume）导入将自动生成同级名称（如 sphere_0、volume_0）。

某些几geometry（如 packed primitives 或 Alembic primitives）可能具有指定其在层次结构中位置的属性。如果存在这些属性，导入器将使用它们。

** 您还可以在 SOP 中添加属性，专门用于控制几何体导入 USD 时的层次关系。路径属性参数可让您指定包含路径信息的 SOP 基元属性列表。

如果一个被导入的 prim 有一个自动生成的名称（如 mesh_0），因为它没有路径基元，或者如果它有一个路径基元，但路径是相对的（不以 / 开头），节点会自动在 Import path prefix 中把名称/路径片段与路径前缀起来。这是将 "非路径 "基元组织在一个分支下的一种方式。

例如，如果您将其设置为/world/geo，下表显示了具有不同名称/属性值的 prims 将如何映射到场景图树中。