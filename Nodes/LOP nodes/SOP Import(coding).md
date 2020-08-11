# SOP Import

从SOP网络中导出geometry 到USD场景图(USD scene graph)



## Overview	

导入的geometry被转换为原始的USD 表示，它可能由许多不同的原始 USD primitive类型组成（您可以使用源 SOP geometry的属性来控制导入的 USD 的层次结构）。

有关导入器如何将 SOP 信息转换为 USD 的详细信息，请参见 SOP 导入的工作方式。

您可以通过分层(在场景树的当前内容上合成)或引用(将其附加在场景树的某个分支上)导入SOP几何体。(请参阅子层和引用。)

包含导入的几何体的图层有源元数据，其格式告诉 Houdini 的 USD 插件从一个 SOP 节点而不是磁盘上的文件获取几何体。

这个节点可以把导入的几何体放在活动层中，所以它可以被连接到这个节点的输出的LOP节点修改。

除了几何体本身，您还可以将几何体上的 Houdini 属性作为 USD primvars 导入。