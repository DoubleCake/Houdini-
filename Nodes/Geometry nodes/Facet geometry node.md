# Facet geometry no

控制表面的光滑度.

这个节点还可以用来合并点或曲面法线.

Facet和Divide一样，作为pipeline来分阶段改变几何体。出于这个原因，计算两次法线。例如，在不同geometry的共享点成为唯一之前计算表面法线，这将为您提供smooth shading和唯一point的不寻常结果，因为法线在点仍然共享时得到计算。

这个工具对于清理geometry很有用。你可以调整背向的geometry方向，删除degenerative polygons，合并或者生成唯一点，或基于edge的cusp polygon。

>这个操作是清理从.dxf文件中读入的geometry的好帮手，它可以纠正一些.dxf文件中存在的翻转法线。

## Using Facet

1. 选择你需要进行Facet操作的faces、edges、points
2. 点击位于多边形栏 (Polygon tab)的Fact,你可以在parameter editer中改变 