# CornerstoneImageLoadProgress Event
CornerstoneImageLoadProgress事件会在加载图像时发出。对此事件的支持取决于正在使用的image loader，因此是可选的，不保证支持。

活动属性：

imageId - 正在加载的imageId
percentComplete - 加载的图像的百分比
loaded - 到目前为止加载的字节数
total - 要加载的总字节数

> 因此percentComplete = loaded / total