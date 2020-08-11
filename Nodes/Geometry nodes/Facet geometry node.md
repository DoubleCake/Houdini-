# Facet geometry no

控制表面的光滑度.

这个节点还可以用来合并点或曲面法线.

Facet和Divide一样，作为pipeline来分阶段改变几何体。出于这个原因，计算两次法线。例如，在不同geometry的共享点成为唯一之前计算表面法线，这将为您提供smooth shading和唯一point的不寻常结果，因为法线在点仍然共享时得到计算。

这个工具对于清理geometry很有用。你可以调整背向的geometry方向，删除degenerative polygons，合并或者生成唯一点，或基于edge的cusp polygon。

小贴士

这个操作是清理从.dxf文件中读入的几何体的好帮手，它纠正了一些.dxf文件中存在的翻转法线。它可以修正一些.dxf文件中的翻转法线。