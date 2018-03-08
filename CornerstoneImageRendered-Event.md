# CornerstoneImageRendered-Event
每当图像被cornerstone重新绘制时，都会发出CornerstoneImageRendered事件调用。 该事件包含可用于使用HTML5 canvas context（例如geometry或text）在图像上绘制的信息。您还可以使用各种viewport属性（如窗宽，窗位和zoom属性）更新HTML。

事件属性：

* canvasContext - 此图像的canvas context。请注意，在绘制context属性之前，应该重置context属性
* renderTimeInMs - 渲染图像所用的时间（以毫秒为单位）。用此属性可以设定阈值，超时关闭图像功能
* viewport - 此图像的当前视口属性
* element - 为此图像启用的DOM元素
* image - 图像的image对象
* enabledElement - cornerstone内部使用的一个数据结构

注意：cornerstone使用通用的DOM事件机制来发出此事件。由于canvas context作为此事件的一部分提供，并且可能有多个事件监听器，因此事件监听器可能会将canvas context的状态置于意外状态（例如scale, translation, line colors等）。因此，谨慎地在您的事件处理程序中显式设置canvas context状态。一种方法是在绘制画布上下文之前调用setToPixelCoordinateSystem()来重置canvas context。

