`Pixel Coordinate System`则是`cornerstone`显示区的坐标系，例如`0.0, 0.0`代表左上角。

注意：
1. 函数`pagetopxel()`可用于将从浏览器事件获得的坐标转换为像素坐标系中的坐标
2. 函数`setopxelcoaratessystem()`可以用来将`canvas context`设置为坐标系。这在处理`CornerstoneImageRendered`事件时非常有用，可以在图像的顶部绘制几何图形
3. 此坐标系统与`dicom`灰度值相匹配
4. 使用`math.ceil()`将像素坐标系转换为整数像素数(用于查找像素数据中的像素值)