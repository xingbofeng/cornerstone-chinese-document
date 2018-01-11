在cornerstone，一个`enabled element`就是一个`HTML DOM`节点（例如，一个`div`），cornerstone会在其中展示一些交互式的医学影像。为了展示这些影像，开发者需要做以下事情：

1. 将cornerstone库通过`script`标签引入你的`web`页面中。
2. 将cornerstone的图片加载器（[image loaders](./ImageLoader.md)）引入你的`web`页面中，图片加载器会使用`WADO`、`WADO-RS`或`custom`协议加载医学影像图片并提供给`web`页面使用。
3. 把`enabled element`这个`DOM`节点加入到你的页面中去，在这个`DOM`节点内会展示医学影像。
4. 使用`CSS`为这个`element`固定好宽度和高度。（切记一定要固定宽高）
5. 调用[enable()](./enable-api.md)，准备在节点内展示影像。
6. 调用[loadImage()](./loadImage-api.md)加载影像。
7. 调用[displayImage()](./displayImage-api.md)展示影像。

可以看这个最简单的[例子](https://rawgit.com/chafey/cornerstone/master/example/jsminimal/index.html)，它使用cornerstone在`web`页面中展示了一个最简单的医学影像。在这之上，一个`web`开发者可以选择做以下事情：

1. 指定[Viewport](./viewport.md)参数，例如窗宽窗位（`window width/window center`），放大比例（`zoom`），图像平移（`pan`）。在调用`displayImage()`方法之后，`viewport`就会被指定，之后若想更改`viewport`参数，可以通过调用[setViewport api](./setViewport-api.md)来更改。
2. 监听[CornerstoneImageRendered](./CornerstoneImageRendered-Event.md)事件，这个事件会在每次cornerstone影像重绘时触发。
3. 监听[CornerstoneViewportUpdated](./CornerstoneViewportUpdated-Event.md)事件，这个事件会在每次cornerstone影像的[Viewport](./viewport.md)更新之后触发。
4. 实现一个自定义的[image loaders](./ImageLoader.md)，它可以加载存储在存储器中的图像或通过非标准的网络协议加载图片。
5. 当`element`的宽高改变时，调用[resize()](./resize-api.md)方法通知cornerstone知晓这一改变。

你也可以通过引入[cornerstoneTools](https://github.com/cornerstonejs/cornerstoneTools)获取一些诸如更改窗宽窗位、平移、放大缩小等功能的工具库。