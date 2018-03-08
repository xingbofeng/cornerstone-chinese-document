# CornerstoneNewImage-Event
每次在enable的element上显示新图像时，都会发出CornerstoneNewImage事件。 请注意，该事件后面总是跟着一个CornerstoneImageRendered事件。

事件属性：

frameRate - 基于自上次新图像渲染以来更新图像的帧率。
viewport - 此图像的当前视口属性
element - 为此图像启用的DOM元素
image - cornerstone影像的image对象
enabledElement - cornerstone内部使用的一个数据结构
