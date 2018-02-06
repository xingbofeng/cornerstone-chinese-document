关于'architecture'的几点思考:
* 尽可能利用其他库来减少维护和调试的代码量
* 没有'Web'应用框架，应利用等为骨干，'angular.js'，灰烬，流星或'Knockout.js'。基石侧重于比这些框架低的层，不需要它们。虽然应该使用这些框架，但也可能包括适配器，使其更易于在这些框架中使用
* 与大型库相比，更喜欢小型简单库。(例如，'jQuery'太大了) 
* 不要使用对库用户强制依赖的库。例如，一个应用程序使用一个不同版本的库，而不是一个基石，就可以正常工作
* 应用程序和基石应该可以共享相同的库(只要版本得到基石的支持)
* 异步'API'应该利用延迟模式来返回调用者可以用来正确处理成功和失败条件的承诺。[Cujo.js when library](https://github.com/cujojs/when)中有关于此的[great documentation](https://github.com/cujojs/when/wiki)，(并且可能会与其他'cujo.js'库(如[REST](https://github.com/cujojs/rest)和[curl](https://github.com/cujojs/curl)一起使用) 
* 'API'应该提供医学成像域的简化视图，使开发人员更容易使用。例如，像素数据可以以模态单元(例如，'Hounsfield'表示'ct')返回，这样开发人员就不必处理应用渐升斜率/截取、掩蔽像素填充值、应用'LUTS'或处理像素上方比特的覆盖。彩色图像总是以'RGB'的形式返回
* 'Cornerstone'应该避免通过正确使用[javascript module pattern](http://www.adequatelygood.com/JavaScript-Module-Pattern-In-Depth.html)来污染全局名称空间。与其他javascript模块设计(如[AMD](https://en.wikipedia.org/wiki/Asynchronous_module_definition)和[CommonJS](http://wiki.commonjs.org/wiki/CommonJS))的集成应该是可能的，但不是必需的