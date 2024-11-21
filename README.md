
大家好，我是程序员鱼皮。


大家如果平时使用网站或产品时出现了问题，一般都会去寻找 “联系客服” 的位置，从而获得人工的帮助。我们团队的面试刷题产品 \- 面试鸭最近就遇到了这样一个难题：明明我们网站右下角就有联系客服按钮、而且我们每道面试题目下方都有反馈按钮，但是很多用户还是不知道怎么给我们反馈问题。


我们利用第三方网站统计工具进行分析，发现整整一个月客服按钮的点击数竟然才 20 多？！感觉毛用没有啊！


![](https://pic.yupi.icu/1/image-20241119093835528.png)


于是，我就拉着开发同学一起开会讨论，希望解决这个问题。


我说：作为良心产品，我要让用户都知道怎么找我们反馈问题！怎么实现我不管，明天上线！


![](https://pic.yupi.icu/1/image-20241119094234164.png)


开发小 A 当时就这个表情：


![](https://pic.yupi.icu/1/image-20241119094208170.png)


结果，一天后，小 A 竟然真的拿电脑来给我看效果了。我一看，立刻就红温了，就跟刚煮熟的螃蟹似的：


![](https://pic.yupi.icu/1/image-20241119094949383.png)


这。。这 \*\* 是客服？我们这可是一个正经网站啊！


不过仔细想一想，感觉还挺不错的，这下网站可真是充满了吸引力啊！应该会有很多同学点击了（狗头）。


![](https://pic.yupi.icu/1/image-20241119095152261.png)


我本来以为这个客服形象需要花费很长时间开发，结果小 A 跟我说：可简单了，一会儿就搞定了\~


于是，我也去学习了解了一下，确实简单，这篇文章就分享给大家。


⭐️ 喜欢看视频的同学，更推荐看视频教程哦：[https://bilibili.com/video/BV1FeUaYDEKr/](https://github.com)


 


## 网站看板娘教程


其实前面我们看到的动漫看板娘，是运用了 Live2D 技术实现的。


Live2D 是一种将 2D 图像转换为各种动画效果的技术。通过骨骼动画和物理引擎等技术，能够实现类似 3D 的立体动画效果，但实际仍然是 2D 图像的变形和运动。


相比于 GIF 图片，Live2D 模型可以实时和用户进行互动，更加吸引用户。


![](https://pic.yupi.icu/1/image-20241119095926908.png)


怎么样，是不是迫不及待也想给自己的网站整一个呢？


下面只用 1 分钟，手把手教你怎么给网站快速添加一个可爱的 Live2D 看板娘。对于提高网页点击率和用户访问时长来说，应该还是很有帮助的。


![](https://pic.yupi.icu/1/image-20241119100202122.png)


来不及学的朋友，记得点个收藏，以后说不定用得上。


### 一、准备工作


首先，我们需要准备 2 样东西：一套 Live2D 模型文件，和让网站加载模型的 JS 脚本。


#### 1、模型文件


每个 Live2D 模型都对应了一组文件，定义了模型信息、物理效果、姿势动作、图片资源等，结构十分复杂：


![模型文件结构](https://pic.yupi.icu/1/image-20241119100301098.png)


而且模型文件格式又分为 MOC 和 MOC3 两个版本，MOC3 的模型不仅视觉效果更好，还支持更复杂、更自然流畅的动作，但相应的文件结构会更复杂。我们开头看到的网站中的二次元红衣子女，就是用的 MOC3 的模型。


虽然模型复杂，不过别担心，我们可以通过 Live2D 官网和 GitHub 的开源项目搜到现成的模型文件：


* Live2D 官方：[https://www.live2d.com/zh\-CHS/learn/sample](https://github.com)
* ⭐️ 有很多模型和示例站点：[https://github.com/imuncle/live2d](https://github.com)
* 模型收集：[https://github.com/Eikanya/Live2d\-model](https://github.com)


友情提示，由于 Live2D 的开发是需要大量时间精力的， **一般高质量的模型都有版权保护，所以请大家谨慎使用** 。


 


#### 2、JS 脚本


有了模型文件，我们怎么让它出现在网站上呢？这就需要 JS 脚本。


我们可以利用 WebGL 这一主流的图形渲染技术来编写 JS 脚本。但这个技术有一定的复杂度和学习成本，我想哪怕你是一个经验丰富的网站开发者，也不会想要自己写 WebGL 代码去加载 Live2D 模型的。


![](https://pic.yupi.icu/1/image-20241119100541203.png)


我们可以使用一些现成的库来简化编码，比如 2D 渲染引擎 pixi.js，或者使用 Live2D 官方提供的 Web SDK。 


![Live2D 官方文档](https://pic.yupi.icu/1/image-20241119100632302.png)


但是，如果你没有两把刷子，估计看不懂那破朔迷离的官方文档。所以呢，要说贴心，还得是咱广大网友，在 GitHub 上开源了不少开箱即用的 Live2D 加载库。


经过我的一番对比，还是 star 数高的这个库最好用。使用它，不用自己写一行代码，就能给网站增加看板娘！下面来试一试。



> 开源仓库：[https://github.com/stevenjoezhang/live2d\-widget](https://github.com)（不包含模型）


![](https://pic.yupi.icu/1/image-20241119100713548.png)


 


### 二、快速接入看板娘


如果你是小白，只需要复制下面这一行自动加载脚本的代码， 放到你网站 html 页面的 `head` 或 `body` 中，就可以加载看板娘：



```
<script src="https://fastly.jsdelivr.net/gh/stevenjoezhang/live2d-widget@latest/autoload.js"></script>
```

来，运行网页看下效果，看板娘直接就出来了有没有！还支持对话、换模型、换衣服、截图功能：


![](https://pic.yupi.icu/1/image-20241119100912867.png)


哎呀，突然感觉自己成为前端大佬了，好有成就感啊！


![](https://pic.yupi.icu/1/image-20241119094234164.png)


为什么只用这一行代码，就实现了呢？


其实，我们刚刚是加载了项目作者在远程服务器上为我们提供的 JS 脚本，这个脚本会帮我们从远程服务器下载模型文件。


这就意味着什么呢？如果你想要自己定义加载哪些模型、以及对话的内容，就不是很方便，因为你无法登录到别人的服务器去修改脚本。


作者虽然也考虑到了这一点，但他的做法是搞了个 PHP 的后端项目，通过接口的方式来动态获取要加载的模型列表和对话信息。


![](https://pic.yupi.icu/1/image-20241119101049101.png)


我就给网站加个看板娘，你还让我去搭一个后端？还让我去搞 PHP？那我必然是不会这么干的！


下面鱼皮教大家一种更简单的方式，来自定义看板娘。


 


### 三、自定义


#### 1、改造项目


首先，将上述开源项目完整下载到本地，用一个编辑器打开。


找到 `autoload.js` 文件，这是整个 Live2D 加载的入口，我们可以看到默认情况下是从远程地址加载的模型列表和对话信息。


![](https://pic.yupi.icu/1/image-20241119101325713.png)


其中，initWidget 方法非常关键，顾名思义，作用是初始化组件。点进去，可以看到加载组件的方法（loadWidget），这里新建了一个模型对象。


![](https://pic.yupi.icu/1/image-20241119101433879.png)


再点进去，就进入了模型定义文件，默认情况下，是通过网络请求从远程服务器上加载的模型列表配置。


![](https://pic.yupi.icu/1/image-20241119101458720.png)


那我们只要把这段逻辑改为从本地加载我自己写的模型列表配置，就可以了呀\~


没错，想到这里，可能有些同学就直接去爆改这个源文件了，但这是很不优雅的！


我们可以复制该模型定义文件，得到一个新的 `本地模型定义文件` ，保证函数和大多数代码不变，只需要将部分代码修改为加载本地特定位置下的模型文件和模型配置文件。



> 这段代码大家暂时不用关注，文末我会分享源码


![](https://pic.yupi.icu/1/image-20241119101619777.png)


然后，修改加载组件的方法，根据开发者传入的配置信息，决定是否从本地加载模型，不就可以了么？


![](https://pic.yupi.icu/1/image-20241119101701097.png)


做完这些之后，你需要重新打包一下修改完的文件。由于项目用了 npm 进行管理，你需要先安装 Node.js 服务，然后在项目内安装依赖、再执行 build 打包，就得到了新的加载文件（waifu\-tips.js）。


![](https://pic.yupi.icu/1/image-20241119101757748.png)


 


#### 2、效果展示


改造完毕，下面我们来使用一下改造后的项目吧\~


先随便写一个小网站：



```
<html lang="en"> <head>   <meta charset="UTF-8">   <meta name="viewport" content="width=device-width, initial-scale=1.0">   <title>Live2D 看板娘title> head> <body>   <script src="./autoload.js">script> body>html>
```

将模型文件和模型列表配置文件放到项目根目录中：


![](https://pic.yupi.icu/1/1731048732077-38143a8e-d453-4189-857a-d95cea7d6053.png)


大家可以自行修改模型列表配置文件 `model_list.json` （数组的每个元素都是一个模型、二维数组的每个元素是不同的皮肤）：


![](https://pic.yupi.icu/1/1731048995743-7aa835a0-7cf6-409e-8005-9a212e0ab767.png)


最后，修改 autoload.js 加载文件的配置，包括将 live2d 路径改为当前路径，修改初始化组件配置为本地（使用本地模型、指定模型文件路径、模型列表配置文件的路径），还可以自定义要使用的工具：



```
// 改为相对路径const live2d_path = "./";// ...// 初始化组件initWidget({ isLocalModel: true, // 使用本地模型 waifuPath: live2d_path + "waifu-tips.json", modelsPath: live2d_path + "model", modelListPath: live2d_path + "model/model_list.json", tools: ["hitokoto", "asteroids", "switch-model", "switch-texture", "photo", "info", "quit"]});
```

大功告成，我们来双击文件运行一下\~


结果，运行失败啦！不是哥们，你人呢？


![](https://pic.yupi.icu/1/image-20241119102044510.png)


为什么模型没加载出来呢，看下 F12 控制台的报错就知道了：


![](https://pic.yupi.icu/1/image-20241119102129790.png)


这是因为浏览器为了安全，限制了从本地文件系统直接加载资源的能力。所以我们需要在本地启动一个服务器来运行网页，这一步难不倒大家。可以直接用开发工具自带的服务器，点一下图标就能正确运行了，也可以自己安装一个 serve 工具。


![](https://pic.yupi.icu/1/image-20241119102233022.png)


这样，我们的 Live2D 看板娘，就完美加载出来啦\~


![](https://pic.yupi.icu/1/image-20241119102313486.png)


 


### 四、更多操作


接下来你还可以通过修改配置文件（waifu\-tips.json）来自定义对话，通过修改工具文件 `tools.js` 来自定义点击模型旁边图标时执行的操作，通过加一些 CSS 代码来调整模型的位置等等。



> 改完后不要忘记重新 build 打包哦


还可以通过 F12 查看到对应的元素，修改样式文件调整位置，比如：



```
<style> #waifu {   right: 40px !important;   left: unset !important;}style>
```

 




---


 


以上就是本期分享，我把魔改后的代码开源到了 [自己的 GitHub 仓库](https://github.com) ，大家可以直接使用，让你的网站魅力无穷！


![](https://pic.yupi.icu/1/image-20241119102500765.png)


不过代价就是模型文件比较大，可能会消耗大量的带宽和流量。我们也在纠结是否真的要给网站应用这个功能，欢迎大家给我们一些建议吧\~


## 更多编程学习资源


* [Java前端程序员必做项目实战教程\+毕设网站](https://github.com)
* [程序员免费编程学习交流社区（自学必备）](https://github.com)
* [程序员保姆级求职写简历指南（找工作必备）](https://github.com)
* [程序员免费面试刷题网站工具（找工作必备）](https://github.com)
* [最新Java零基础入门学习路线 \+ Java教程](https://github.com)
* [最新Python零基础入门学习路线 \+ Python教程](https://github.com)
* [最新前端零基础入门学习路线 \+ 前端教程](https://github.com)
* [最新数据结构和算法零基础入门学习路线 \+ 算法教程](https://github.com):[slower加速器](https://chundaotian.com)
* [最新C\+\+零基础入门学习路线、C\+\+教程](https://github.com)
* [最新数据库零基础入门学习路线 \+ 数据库教程](https://github.com)
* [最新Redis零基础入门学习路线 \+ Redis教程](https://github.com)
* [最新计算机基础入门学习路线 \+ 计算机基础教程](https://github.com)
* [最新小程序入门学习路线 \+ 小程序开发教程](https://github.com)
* [最新SQL零基础入门学习路线 \+ SQL教程](https://github.com)
* [最新Linux零基础入门学习路线 \+ Linux教程](https://github.com)
* [最新Git/GitHub零基础入门学习路线 \+ Git教程](https://github.com)
* [最新操作系统零基础入门学习路线 \+ 操作系统教程](https://github.com)
* [最新计算机网络零基础入门学习路线 \+ 计算机网络教程](https://github.com)
* [最新设计模式零基础入门学习路线 \+ 设计模式教程](https://github.com)
* [最新软件工程零基础入门学习路线 \+ 软件工程教程](https://github.com)


