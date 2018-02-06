关于`cornerstone`结构的几点思考:
* 尽可能利用其他库来减少维护和调试的代码量
* 不应当依赖`Web`应用框架，例如`backbone`，`angular.js`，`ember`，`meteor`或`Knockout.js`。`cornerstone`不需要你依赖于这些框架。虽然我们在实际的应用开发中使用这些框架，但需要我们自己引入适配器，使其更易于在这些框架中使用
* 与大型库相比，更喜欢小型简单库。(例如，`jQuery`太大了) 
* 不要使用依赖于其它库的库。例如，一个应用程序使用了不同版本的库，这时可能导致`cornerstone`无法正常工作。
* 应用程序和`cornerstone`应该可以共享相同的库(只要版本与`cornerstone`依赖的版本统一)
* 异步`API`应该利用异步的方式来返回调用者，例如使用`Promise`及其类库。如[when](https://github.com/cujojs/when)，可以到[这里](https://github.com/cujojs/when/wiki)查看关于它的文档，(并且可能会与其他`cujo.js`库(如[REST](https://github.com/cujojs/rest)和[curl](https://github.com/cujojs/curl)一起使用) 
* `API`应该提供医学影像的简化视图数据，使开发人员更容易使用。例如，像素数据可以以模态单元(例如，`Hounsfield`表示`ct`)返回，这样开发人员就不必处理`rescale slope/intercept`等医学影像相关数据，这些总被`cornerstone`预先处理了。对于彩色图像，总是以`RGB`的形式返回。
* `Cornerstone`应该避免通过正确使用[javascript module pattern](http://www.adequatelygood.com/JavaScript-Module-Pattern-In-Depth.html)来避免污染全局名称空间。与其他javascript模块设计(如[AMD](https://en.wikipedia.org/wiki/Asynchronous_module_definition)和[CommonJS](http://wiki.commonjs.org/wiki/CommonJS))的集成应该是可能的，但不是必需的。