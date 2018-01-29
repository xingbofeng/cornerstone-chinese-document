`image object`对象描述要呈现的图像。
1. `imageId`-与此`image object`关联的`imageId` 
2. `minPixelValue`-图像中存储的最小像素值。
3. `maxPixelValue`-图像中存储的最大像素值。
4. `slope`-重新缩放坡度将存储的像素值转换为模态像素值,如果未指定则为`1`
5. `intercept`-用于将存储的像素值转换为情态值的`resrescale`截取，如果未指定则为`0`。
6. `windowCenter`-应用于图像的默认窗口中心。
7. `windowWidth`-应用于图像的默认窗口宽度。
8. `getPixelData`-返回基础像素数据的函数。灰度的整数数组和颜色的`RGBA`数组 
9. `getImageData`-返回图像的画布`ImageData`对象的函数。这只适用于彩色图像。
10. `getCanvas`-个函数，它返回一个画布元素，并将图像加载到其中。这是只需要彩色图像。
11. `getImage`-返回带有图像数据的  `javascript`图像对象的函数。这是可选的，通常用于标准`web JPEG`和`PNG`格式编码的图像。
12. `rows`-图像中的行数。这与高度相同，但为方便起重复
13. `columns`-图像中的列数。这与宽度相同，但为了方便复制
14. `height`-图像的高度。这与行相同，但为方便起了重复
15. `width`-图像的宽度。这与列相同，但为方便起了重复
16. `color`-如果像素数据为`RGB`，则为`true`，如果灰度则为`false`
17. `columnPixelSpacing`-每个像素的中间（或每个像素的宽度）之间的水平距离，以毫米为单位，如果未知则为`undefined`
18. `rowPixelSpacing`-每个像素中间(或每个像素的高度)之间的垂直距离，以毫米为单位，如果不知道，则`undefined` 
19. `invert`- 如果最初应该显示该图像，则为`true`，如果不是，则为`false`。这主要是为了支持双组分图像，并对单色进行光度解释。 
20. `sizeInBytes`-用于存储此图像像素的字节数。 