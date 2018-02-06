`Rendering loop`一般利用现代浏览器中的`requestAnimationFrame`(`RAF`)方法。如果`RAF`不可用，则使用`16 ms`定时器。

`Rendering loop`是基于一个元素启用的，当`cornerstone.enable(element)`被调用时开启，并在`cornerstone.disable(element)`被调用时禁用。

执行情况如下：
* 在`RAF`中注册了`draw()`回调；
* `draw()`由浏览器只称后一帧显示在屏幕上； 
* 一旦被调用，
  * 如果该元素被计划`Rendering loop`，则呈现它，并在`RAF`中重新注册`draw()`；
  * 如果元素没有被重新渲染，则不执行任何工作，回调将重新注册到`RAF`；
  * 如果元素`disabled()`，则不会重新注册回调，从而结束`Rendering loop`。

这意味着：
* `cornerstone.draw()`和`cornerstone.invalidate()`不再触发视图的重新渲染，而是将图像标记为需要重新渲染的状态；
* 每个`cornerstone`元素注册自己的`RAF`循环；
* 如果在`60 Hz`系统上渲染时间超过`16 ms`，则跳过渲染帧； 
* 每个帧只渲染一次是可能的，即使渲染时间远低于`16 ms`；
* 所有的变化，例如，平移，缩放等操作，都在下一帧中重新渲染。