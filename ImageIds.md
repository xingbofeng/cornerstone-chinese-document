`cornerstone ImageId`确定了`cornerstone`的单个影像的`URL`。`ImageId`中的`URL scheme`被`cornerstone`用来定义使用哪一个`ImageLoader`插件来加载`dicom`图像。这个策略允许`cornerstone`同时使用不同协议从不同的服务器获得的多个图像。例如，`cornerstone`可以通过`WADO`获得的`DICOM CT`图像和存储在文件系统中的由数码相机拍摄的`JPEG`皮肤病图像的同时展示出来。

`cornerstone`没有指定`URL`的内容，而是由`ImageLoader`来定义`URL`的内容，针对不同的`ImageLoader`有不同的`URL`。 例如，可以专门编写一个`ImageLoader`插件来与私有服务器通信，并使用`GUID`，`filename`或`database row id`来查找图像。

对于不同的`ImageLoader`插件，有不同的`imageId`，看下面的例子：

## WADO
```
http://www.medical-webservice.st/RetrieveDocument?
requestType=WADO&studyUID=1.2.250.1.59.40211.12345678.678910
&seriesUID=1.2.250.1.59.40211.789001276.14556172.67789
&objectUID=1.2.250.1.59.40211.2678810.87991027.899772.2
&contentType=application%2Fdicom&transferSyntax=1.2.840.10008.1.2.4.50
```

## DICOM CGET
`dicomcget image loader`通过向服务器发出一个`DICOM CGET`请求来获取`DICOM`图像，然后将其返回到`cornerstone`：

```
dicomcget://www.medical-webservice.st/RetrieveDocument?
requestType=WADO&studyUID=1.2.250.1.59.40211.12345678.678910
&seriesUID=1.2.250.1.59.40211.789001276.14556172.67789
&objectUID=1.2.250.1.59.40211.2678810.87991027.899772.2
&contentType=application%2Fdicom&transferSyntax=1.2.840.10008.1.2.4.50
```

## DICOM CMOVE
`dicomcmove image loader`通过向服务器发出一个`DICOM CMOVE`请求来获取`DICOM`图像，然后将其返回到`cornerstone`：

```
dicomcmove://www.medical-webservice.st/RetrieveDocument?
requestType=WADO&studyUID=1.2.250.1.59.40211.12345678.678910
&seriesUID=1.2.250.1.59.40211.789001276.14556172.67789
&objectUID=1.2.250.1.59.40211.2678810.87991027.899772.2
&contentType=application%2Fdicom&transferSyntax=1.2.840.10008.1.2.4.50
```

## 根据`GUID`（`imageId`）查找
`image loader`可以把`GUID`作为参数，请求服务器，在数据库中查找到这一章图片存储在磁盘的路径，然后将`dicom`像素点上的数据返回给`cornerstone`：

```
custom1://server?imageId=38120cae-bdcd-4102-b799-c8b9965d3421
```

## 根据`database rowid`查找
`image loader`可以把`database rowid`作为参数，请求服务器，在数据库中查找到这一章图片存储在磁盘的路径，然后将`dicom`像素点上的数据返回给`cornerstone`：

```
custom2://server/1353056
```

## 在文件系统中查找
`image loader`根据`dicom`文件在文件系统的路径来请求服务器，然后将`dicom`像素点上的数据返回给`cornerstone`：

```
custom3://server/dermataologyImages/room10/12345.jpg
```