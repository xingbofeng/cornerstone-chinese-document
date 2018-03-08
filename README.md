# cornerstone中文文档
wiki的作用是帮助大家更好地理解cornerstone、查阅并参考cornerstone的API。如果你是新接触cornerstone，我们建议你首先理解下列的基础概念，然后去查看各种示例。

## 概念
* [Enabled Elements](./enabled-element.md)
* [ImageIds](./ImageIds.md)
* [ImageLoaders](./ImageLoader.md)
* [Image Object](./image.md)
* [Viewport](./viewport.md)
* [Pixel Coordinate System](./pixel-coordinate-system.md)
* [Architecture](./architecture.md)
* [Rendering loop](./Rendering-loop.md)

## API参考
### cornerstone事件（Events）

* [CornerstoneImageRendered Event](./CornerstoneImageRendered-Event.md)
* [CornerstoneNewImage Event](./CornerstoneNewImage-Event.md)
* [CornerstoneImageLoaded Event](./CornerstoneImageLoaded-Event.md)
* [CornerstoneImageLoadProgress Event](./CornerstoneImageLoadProgress-Event.md)
* [CornerstoneElementDisabled Event](./CornerstoneElementDisabled-Event.md)

### Enable/Disable

* [enable](enable-api)
* [disable](disable-api)

### 绘图（Drawing）
* [draw](draw-api)
* [invalidate](invalidate-api)
* [invalidateImageId](invalidateImageId-api)
* [drawInvalidated](drawInvalidated-api)

### 加载图片和缓存管理（Loading Images and Cache Management）

* [loadImage](loadImage-api)
* [loadAndCacheImage](loadAndCacheImage-api)
* [setMaximumSizeBytes](setMaximumSizeBytes-api)
* [getCacheInfo](getCacheInfo-api)
* [purgeCache](purgeCache-api)
* [removeImagePromise](removeImagePromise-api)
* [getImage](getImage-api)

### 视窗（Viewport）
* [displayImage](displayImage-api)
* [setViewport](setViewport-api)
* [getViewport](getViewport-api)
* [fitToWindow](fitToWindow-api)
* [updateImage](updateImage-api)
* [resize](resize-api)
* [getDefaultViewportForImage](getDefaultViewportForImage-api)

### 坐标（Coordinates）
* [pageToPixel](pageToPixel-api)
* [setToPixelCoordinateSystem](setToPixelCoordinateSystem-api)

### 像素点数据（Pixel Data）
* [getStoredPixels](getStoredPixels-api)

### DOM相关数据（Element Data (Tools)）
* [getElementData](getElementData-api)
* [removeElementData](removeElementData-api)

### 图片加载器（Image Loader） 
* [registerImageLoader](registerImageLoader-api)

### 内部API（Internal APIs）

这些API是在cornerstone内部使用的私有API，而不是提供给外部调用的公开方法。这些API在任何时候都可能发生变化，有被废弃的可能性。

* [getEnabledElement](getEnabledElement-api)
* [addEnabledElement](addEnabledElement-api)
* [putImagePromise](putImagePromise-api)
* [getImagePromise](getImagePromise-api)
* [storedPixelDataToCanvasImageData](storedPixelDataToCanvasImageData-api)
* [storedColorPixelDataToCanvasImageData](storedColorPixelDataToCanvasImageData-api)
* [generateLut](generateLut-api)
* [drawImage](drawImage-api)
* [event](event-api)
* [getDefaultViewport](getDefaultViewport-api)
* [registerUnknownImageLoader](registerUnknownImageLoader-api)