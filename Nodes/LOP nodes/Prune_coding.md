# Prune ：剪枝

隐藏或停用primitives和point 实例

## Overview

因为 USD 只允许非破坏性编辑，所以从场景中 "移除 "某物的两种方法是隐藏它或停用它。

* **停用** ：停用primitives及其子代不会被 USD 函数或 LOP 节点遍历或处理。停用primitives的子代也不会出现在场景图树(Scene Graph Tree)中。

* **隐藏**: 隐藏的primitives及其子代仍由 USD 函数和 LOP 节点处理，但不会显示在视口中或渲染。

您可以将一个prim的激活/可见性数据覆盖写入活动层中，因此当它与下层组成时，在输出阶段，该prim被停用或不可见。

例如，照明部门可能会停用他们从布局部门收到的图层中的划痕照明。

您可以在场景图树窗格中看到prims的可见性和激活状态

## How to

1.  使用 "目标规则(Target Rules) "相应的方法选择primitives。使用添加排除项(Add exclusions)将特定primitives从目标primitives中排除
2. 将方法设置为 "Make Invisible (使不可见)"或 "Deactivate(停用)"，具体取决于您想要 "remove(移除)"所选primitives的方式。
3. 通过打开 "Prun selected  "并针对不应剪枝的primitives执行隔离操作。

