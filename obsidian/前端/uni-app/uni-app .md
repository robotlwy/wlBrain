# 组件/标签对比h5的变化
以前是html标签，比如`<div>`，现在是小程序组件，比如`<view>`。 那么`标签`和`组件`有什么区别，不都是用尖括号包围起来一段英文吗？ 其实标签是老的概念，标签属于浏览器内置的东西。但组件，是可以自由扩展的。 类似你可以把一段js封装成函数或模块，你也可以把一个ui控件封装成一个组件。

`uni-app`参考小程序规范，提供了一批内置组件。

下为html标签和uni-app内置组件的映射表：

- div 改成 [view](https://uniapp.dcloud.io/component/view)
- span、font 改成 [text](https://uniapp.dcloud.io/component/text)
- a 改成 [navigator](https://uniapp.dcloud.io/component/navigator)
- img 改成 [image](https://uniapp.dcloud.io/component/image)
- [input](https://uniapp.dcloud.io/component/input) 仅仅是输入框。 原html规范中input不仅是输入框，还有radio、checkbox、时间、日期、文件选择功能。在uni-app和小程序规范中，input仅仅是输入框。其他功能uni-app有单独的组件或API：[radio组件](https://uniapp.dcloud.io/component/radio)、[checkbox组件](https://uniapp.dcloud.io/component/checkbox)、[时间选择](https://uniapp.dcloud.io/component/picker?id=%e6%97%b6%e9%97%b4%e9%80%89%e6%8b%a9%e5%99%a8)、[日期选择](https://uniapp.dcloud.io/component/picker?id=%e6%97%a5%e6%9c%9f%e9%80%89%e6%8b%a9%e5%99%a8)、[图片选择](https://uniapp.dcloud.io/api/media/image?id=chooseimage)、[视频选择](https://uniapp.dcloud.io/api/media/video?id=choosevideo)、[多媒体文件选择(含图片视频)](https://uniapp.dcloud.io/api/media/video?id=choosemedia)、[通用文件选择](https://uniapp.dcloud.io/api/media/file?id=choosefile)。
- [form](https://uniapp.dcloud.io/component/form)、[button](https://uniapp.dcloud.io/component/button)、[label](https://uniapp.dcloud.io/component/label)、[textarea](https://uniapp.dcloud.io/component/textarea)、[canvas](https://uniapp.dcloud.io/component/canvas)、[video](https://uniapp.dcloud.io/component/video) 这些还在。
- select 改成 [picker](https://uniapp.dcloud.io/component/picker)
- iframe 改成 [web-view](https://uniapp.dcloud.io/component/web-view)
- ul、li没有了，都用view替代。做列表一般使用[uList组件](https://ext.dcloud.net.cn/plugin?id=24)
- audio 不再推荐使用，改成api方式，[背景音频api文档](https://uniapp.dcloud.io/api/media/background-audio-manager?id=getbackgroundaudiomanager) 其实老的HTML标签也可以在uni-app里使用，uni-app编译器会在编译时把老标签转为新标签，比如把div编译成view。但不推荐这种用法，调试H5端时容易混乱。

**除了改动外，新增了一批手机端常用的新组件**

- scroll-view [可区域滚动视图容器](https://uniapp.dcloud.io/component/scroll-view)
    
- swiper [可滑动区域视图容器](https://uniapp.dcloud.io/component/swiper)
    
- icon [图标](https://uniapp.dcloud.io/component/icon)
    
- rich-text [富文本（不可执行js，但可渲染各种文字格式和图片）](https://uniapp.dcloud.io/component/rich-text)
    
- progress [进度条](https://uniapp.dcloud.io/component/progress)
    
- slider [滑块指示器](https://uniapp.dcloud.io/component/slider)
    
- switch [开关选择器](https://uniapp.dcloud.io/component/switch)
    
- camera [相机](https://uniapp.dcloud.io/component/camera)
    
- live-player [直播](https://uniapp.dcloud.io/component/live-player)
    
- map [地图](https://uniapp.dcloud.io/component/map)
    
- cover-view [可覆盖原生组件的视图容器](https://uniapp.dcloud.io/component/cover-view?id=cover-view)
    
    cover-view需要多强调几句，uni-app的非h5端的video、map、canvas、textarea是原生组件，层级高于其他组件。如需覆盖原生组件，则需要使用cover-view组件。详见[层级介绍](https://uniapp.dcloud.net.cn/component/native-component)
    

除了内置组件，还有很多开源的扩展组件，把常用操作都进行封装，DCloud建立了插件市场收录这些扩展组件，详见[插件市场](https://ext.dcloud.net.cn/)

# 目录结构
一个uni-app工程，默认包含如下目录及文件：
<div style="line-height: 1.4;padding: 1.25rem 1.5rem;margin: .85rem 0;background-color: #282c34;border-radius: 6px;overflow: auto;color:#fff;font-family: source-code-pro, Menlo, Monaco, Consolas, Courier New, monospace;">
┌─uniCloud              云空间目录，支付宝小程序云为uniCloud-alipay，阿里云为uniCloud-aliyun，腾讯云为uniCloud-tcb（详见<a style='color: #42b983;' href="https://doc.dcloud.net.cn/uniCloud/quickstart?structure&id=structure">uniCloud</a>）<br>
│─components            符合vue组件规范的uni-app组件目录<br>
│  └─comp-a.vue         可复用的a组件<br>
├─utssdk                存放uts文件<br>
├─pages                 业务页面文件存放的目录<br>
│  ├─index<br>
│  │  └─index.vue       index页面<br>
│  └─list<br>
│     └─list.vue        list页面<br>
├─static                存放应用引用的本地静态资源（如图片、视频等）的目录，注意：静态资源都应存放于此目录<br>
├─uni_modules           存放uni_module <a style='color: #42b983;' href="https://uniapp.dcloud.net.cn/plugin/uni_modules.html">详见</a><br>
├─platforms             存放各平台专用页面的目录，<a style='color: #42b983;' href="https://uniapp.dcloud.net.cn/tutorial/platform?id=%E6%95%B4%E4%BD%93%E7%9B%AE%E5%BD%95%E6%9D%A1%E4%BB%B6%E7%BC%96%E8%AF%91">详见</a><br>
├─nativeplugins         App原生语言插件 <a style='color: #42b983;' href="https://nativesupport.dcloud.net.cn/NativePlugin/README">详见</a><br>
├─nativeResources       App端原生资源目录<br>
│  ├─android            Android原生资源目录 <a style='color: #42b983;' href="https://uniapp.dcloud.net.cn/tutorial/app-nativeresource-android">详见</a><br>
|  └─ios                iOS原生资源目录 <a style='color: #42b983;' href="https://uniapp.dcloud.net.cn/tutorial/app-nativeresource-ios.html#%E8%B5%84%E6%BA%90%E6%96%87%E4%BB%B6-bundle-resources">详见</a><br>
├─hybrid                App端存放本地html文件的目录，<a style='color: #42b983;' href="https://uniapp.dcloud.net.cn/component/web-view">详见</a><br>
├─wxcomponents          存放小程序组件的目录，<a style='color: #42b983;' href="https://uniapp.dcloud.net.cn/tutorial/miniprogram-subject?id=%E5%B0%8F%E7%A8%8B%E5%BA%8F%E7%BB%84%E4%BB%B6%E6%94%AF%E6%8C%81">详见</a><br>
├─unpackage             非工程代码，一般存放运行或发行的编译结果<br>
├─main.js               Vue初始化入口文件<br>
├─App.vue               应用配置，用来配置App全局样式以及监听 <a style='color: #42b983;' href="https://uniapp.dcloud.net.cn/collocation/App#%E5%BA%94%E7%94%A8%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F">应用生命周期</a><br>
├─pages.json            配置页面路由、导航条、选项卡等页面类信息，<a style='color: #42b983;' href="https://uniapp.dcloud.net.cn/collocation/pages">详见</a><br>
├─manifest.json         配置应用名称、appid、logo、版本等打包信息，<a style='color: #42b983;' href="https://uniapp.dcloud.net.cn/collocation/manifest">详见</a><br>
├─AndroidManifest.xml   Android原生应用清单文件 <a style='color: #42b983;' href="https://uniapp.dcloud.net.cn/tutorial/app-nativeresource-android">详见</a><br>
├─Info.plist            iOS原生应用配置文件 <a style='color: #42b983;' href="https://uniapp.dcloud.net.cn/tutorial/app-nativeresource-ios">详见</a><br>
└─uni.scss              内置的常用样式变量<br>
</div>

# 怎么查看vue的版本
可以在 <span style=" background-color: rgba(27, 31, 35, .05);color:#e96900;border-radius: 3px;padding: .25rem .5rem;margin: 0;font-size: .85em;">manifest</span> 中切换使用 Vue2 还是 Vue3。
