每个启用的元素都有一个`viewport`，它描述了图像应该如何呈现。可以通过`getviewport()`函数获得启用元素的`viewport`，并使用`setviewport()`函数设置`viewport`。`viewport`参数是： 
* `scale`-放大倍数。`1.0`的刻度将不显示缩放(一个图像像素占用一个屏幕像素)。如果设置为`2.0`则是双倍放大。
* `translation`-描述在像素坐标系中应用的转换的属性`x`和`y`的对象。注意，图像最初以启用元素为中心显示，`x`和`y`的转换分别为`0`和`0`
* `voi`-具有属性、窗口宽度和窗口中心的对象
* `invert`-如果图像应该倒置，则为`true`；如果不是，则为`false`
* `pixelReplication`-如果图像在显示区域被缩放，则为`true`；如果与原图等比例，则为`false`
* `hflip`-如果图像水平翻转，则为`true`,默认值为`false`
* `vflip`-如果图像垂直翻转，则为`true`,默认值为`false`
* `rotation`-图像的旋转（`90`度递增）,默认值是`0` 
* `modalityLUT`-`LUT`被调用的形式，如果没有，则为`undefined`
* `voiLUT`-`VOI LUT`是否将被调用，如果没有，则`undefined`

今后，将增加以下支持:
* 伪颜色表(用于`PET`/`MRI`) 