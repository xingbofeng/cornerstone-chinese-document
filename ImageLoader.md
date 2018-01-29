`Imageloader`是一个`JavaScript`插件，负责获取图像的[ImageId](https://github.com/cornerstonejs/cornerstone/wiki/ImageIds)，并将该图像的相应像素数据返回到`cornerstone`。由于加载影像通常需要对服务器进行调用，所以用于图像加载的`API`需要是异步的。`JavaScript`处理异步操作的是通过[Promises/A+ Specification](https://promisesaplus.com/)多个库实现的。有关`Promises/A+ Specification`的一些信息，请参阅[此页面](https://developers.google.com/web/fundamentals/primers/promises)。因此，`cornerstone`将假设图像加载器返回一个`promise`，`cornerstone`将用于异步接收像素数据，如果出现错误，则`reject`该`promise`。`cornerstone`不需要任何特定的`Promise`库，它应该与任何符合`Promises/A+ Specification`(但它不兼容100%的`jQuery`)一起工作。下面是一个使用`XMLHttpRequest`获取像素数据并使用`jQuery`向`cornerstone`返回承诺的图像加载程序的示例：

```javascript
function loadImage(imageId) {
    // create a deferred object
    var deferred = $.Deferred();

    // Make the request for the DICOM data
    var oReq = new XMLHttpRequest();
    oReq.open("get", imageId, true);
    oReq.responseType = "arraybuffer";
    oReq.onreadystatechange = function(oEvent) {
        if (oReq.readyState === 4) {
            if (oReq.status == 200) {
                // request succeeded, create an image object and resolve the deferred
                // Code to parse the response and return an image object omitted.....
                var image = createImageObject(oReq.response);
                // return the image object by resolving the deferred
                deferred.resolve(image);
            } else {
                // an error occurred, return an object describing the error by rejecting
                // the deferred
                deferred.reject({
                    error: oReq.statusText
                });
            }
        }
    };
    oReq.send();

    // return the pending deferred object to cornerstone so it can setup callbacks to be 
    // invoked asynchronously for the success/resolve and failure/reject scenarios.
    return deferred;
}
```

`Imageloader`负责返回与[ImageId](https://github.com/cornerstonejs/cornerstone/wiki/ImageIds)相对应[的Image object]https://github.com/cornerstonejs/cornerstone/wiki/Image)，当它解析`promise`时，`imageloader` 将转到它的映像函数。映像加载程序使用`Registerimageloader()``API`为给定的`URL`方案注册它自己： 

```javascript
// register the url scheme 'myCustomLoader' with our loadImage function
cornerstone.registerImageLoader('myCustomLoader', loadImage);
```

* 一般流程：
1. `ImageLoaders`向`cornerstone`注册，以加载特定的[Imageid](https://github.com/cornerstonejs/cornerstone/wiki/ImageIds) `scheme`。
2. 应用程序请求使用`loadimage()` `API`加载图像。`cornerstone`代表加载图片的`URL scheme`的`imageloader` `imageid`通过`loadimage()`注册请求。 
3. 一旦获得像素数据，图像处理程序将返回`promise`，并与相应 [Image Object](https://github.com/cornerstonejs/cornerstone/wiki/Imagehttps://note.youdao.com/)进行解析。获取像素数据可能需要使用`XMLHttpRequest`调用远程服务器、解压缩像素数据(例如`jpeg 2000`)和将像素数据转换为`cornerstone`理解的格式(例如`rgb`和 `vsybr`)。 

虽然像素数据通常是从服务器获取的，但并不总是这样。例如使用了`Imageloader`插件来提供图像，而根本不需要服务器。在这种情况下，图像是`Base64`编码的，并存储在`Imageloader`插件本身中。插件简单地将`base64`像素数据转换为像素数组。或者，可以编写在客户端生成派生映像的图像加载程序。例如，您可以以这种方式实现`MPR`功能。

考虑使用[cornerstone WADO Image Loader](https://github.com/cornerstonejs/cornerstoneWADOImageLoader)或[cornerstone Web Image Loader](https://github.com/cornerstonejs/cornerstoneWebImageLoader)。预计不久的将来也会有一个`WADO-RS`图像加载程序。 

