webpack 笔记

webpack是文件打包工具

webpack代表文件的合成

webpack 本质上是一种事件流的机制，他的工作流程是将各个插件串联起来，而实现这一切的核心是tapable;

tapable 有点类似于nodejs里的events库，核心原理也是依赖发布订阅模式

webpack 当中负责编译的compiler 和负责创建bundle的compilation 都是tapable的实例，采用tapable的实例去实现事件

webpack 对入口文件（entry）递归解析生成依赖关系图，然后将所有依赖打包在一起，在打包之前会将所有依赖转译成可打包的 js 模块

通过事件的注册和监听，触发webpack生命周期中的函数方法

创建 webpack在其内部对象上创建的各种钩子

注册 插件将自己的方法注册到对应的钩子上，交给webpack

调用 webpack编译过程中，会适时地触发相应的钩子，因此也就触发了插件的方法

webpack 不仅搭了个台子，然后把很多公用集成在自己身上了，不用再去装插件，特别的可以继续装插件

webpack 模块化是强，但是他胖啊，不是所有人都抱得动，主要是他为了提供更多的功能封装进了太多东西，所以选择上还是需要因地制宜
