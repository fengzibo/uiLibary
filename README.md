#   HTML/CSS开发规范指南
##  规范目的:
    *   降低每个组员介入项目的门槛成本；
    *   提高工作效率及协同开发的便捷性；
    *   高度统一的代码风格；
    *   提供一整套HTML、CSS解决方案，来帮助开发人员快速做出高质量的符合要求的页面；
    
---
##  html书写规范

为每个HTML页面的第一行添加标准模式（standardmode）的声明，确保在每个浏览器中拥有一致的展现。

    <!DOCTYPE html>

文档类型声明统一为HTML5声明类型，编码统一为UTF-8。

    <meta charset="UTF-8">

head中添加信息。

    <meta name="author" content="smile@kang.cool">//作者
    <meta name="description" content="hello">//网页描述
    <meta name="keywords" content="a,b,c">//关键字,“，”分隔
    <meta http-equiv="expires" content="Wed, 26 Feb 1997 08：21：57 GMT">//设定网页的到期时间。一旦网页过期，必须到服务器上重新调阅
    <meta http-equiv="Pragma" content="no-cache">//禁止浏览器从本地机的缓存中调阅页面内容
    <meta http-equiv="Window-target" content="_top">//用来防止别人在框架里调用你的页面
    <meta http-equiv="Refresh" content="5;URL=http://kahn1990.com/">//跳转页面，5指时间停留5秒 网页搜索机器人向导。用来告诉搜索机器人哪些页面需要索引，哪些页面不需要索引
    <meta name="robots" content="none">//content的参数有all,none,index,noindex,follow,nofollow，默认是all
    <link rel="Shortcut Icon" href="favicon.ico">//收藏图标
    <meta http-equiv="Cache-Control" content="no-cache, must-revalidate">//网页不会被缓存
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">//调节浏览器的渲染方式,强制IE8使用最新的内核渲染页面
    
非特殊情况下CSS样式文件外链至HEAD之间，JAVASCRIPT文件外链至页面底部。

    <!DOCTYPE html>
    <html>
    <head>
        <link rel="stylesheet" type="text/css" href="../css/style-index.css" />
    </head>
    <body>
        <!-- 逻辑代码 -->
        <!-- 逻辑代码底部 -->
        <script src="lib/jquery/jquery1.11.3.min.js"></script>
    </body>
    </html>
   
为了在ie8和低版本浏览器上使用html5标签及css3个别属性需要做些兼容

    <script src="lib/jquery/jquery1.11.3.min.js"></script>
    <!--[if lt IE 9]>
          <script src="html5.min.js"></script>
          <script type="text/javascript" src="selectivizr.js"></script>
          <noscript><link rel="stylesheet" href="[fallback css]" /></noscript>  //个人觉得可有可无
    <![endif]- ->
    
大致的html模板如下

    <!DOCTYPE HTML>
    <html lang="zh-CN">
    <head>
        <meta charset="UTF-8">
        <title>Hello Ued!</title>
        <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
        <link rel="stylesheet" type="text/css" href="../css/style-index.css" />
        <script src="../js/jquery1.11.3.min.js"></script>
        <!--[if lt IE 9]>
        <script src="html5.min.js"></script>
        <script type="text/javascript" src="selectivizr.js"></script>
        <![endif]-->
    </head>
    <body>
    <article>
        <h1>Hello Ued!</h1>
    </article>
    </body>
    </html>

嵌套
*    所有元素必须正确嵌套
*    避免冗余标签。
*    不允许交叉；
*    不允许非法的子元素嵌套。：
    
        <ul>
            <h3>xx列表</h3>
            <li>asdasdsdasd</li>
            <li>asdasdsdasd</li>
        </ul>        
   应该

    <div>
        <h3>xx列表</h3>
        <ul>
            <li>asdasdsdasd</li>
            <li>asdasdsdasd</li>
        </ul>
    </div>
    
按模块添加注释
*    在每个模块开始和结束的地方添加注释

    <!-- 新闻列表模块 -->
    <div class="m-news g-mod"
    ...
    <!-- /新闻列表模块 -->
    
    <!-- 排行榜模块 -->
    <div class="m-topic g-mod"
    ...
    <!-- /排行榜模块 -->

模块化

*   每个模块必须有一个模块名
*   每个模块的基本组成部分应该一致
*   模块的子节点类名需带上模块名（防止模块间嵌套时产生不必要的覆盖）
*   孙辈节点无需再带模块名

代码如

    <section class="m-detail">
        <header class="m-detail-hd">
            <h1 class="title">模块标题</h1>
        </header>
        <div class="m-detail-bd">
            <p class="info">一些实际内容</p>
        </div>
        <footer class="m-detail-ft">
            <a href="#" class="more">更多</a>
        </footer>
    </section>
    
---
##  css书写规范
CSS样式新建或修改尽量遵循以下原则。

    根据新建样式的适用范围分为三级：全站级、产品级、页面级。
    尽量通过继承和层叠重用已有样式。
    不要轻易改动全站级CSS。改动后，要经过全面测试。
    
命名

*   命名必须由单词、中划线或数字组成；
*   不允许使用拼音（约定俗成的除外，如：youku, baidu），尤其是缩写的拼音、拼音与英文的混合。
*   不依据表现形式来命名。
*   可根据内容来命名。
*   可根据功能来命名。

不推荐:
    
    left, right, center, red, black
    
推荐:

    nav, aside, news, type, search, detail, news-list, topic
    
命名前缀规范

| 前缀           | 说明           | 示例  |
| ------------- |:-------------:| -----:|
| g-     | 全局通用样式命名，前缀g全称为global，一旦修改将影响全站样式 | g-mod |
| m-	     | 模块命名方式      |   m-detail |
| u- | 组件命名方式     |    u-selector |
| f- | 功能命名方式     |    f-fl |
| s- | 皮肤命名方式     |    s-fc |
| z- | 状态命名方式, 她只能组合使用或作为后代出现   |    .u-ipt.z-dis{}，.m-list li.z-sel{} |
| js- | 所有用于纯交互的命名，不涉及任何样式规则。JSer拥有全部定义权限      |    js-switch |

书写格式

*   选择器与大括号之间保留一个空格；
*   分号之后保留一个空格；
*   逗号之后保留一个空格；
*   所有规则需换行；
*   多组选择器之间需换行；
*   每条规则结束后都必须加上分号；
*   如果属性值为0，则不需要为0加单位；
*   如果是0开始的小数，前面的0可以省略不写；
*   不要在url()里对引用资源加引号；

推荐:

    main {
        display: inline-block;
    }
    h1,
    h2,
    h3 {
        margin: 0;
        background-color: rgba(0, 0, 0, .5);
    }
    body {
        background-image: url(sprites.png);
    }
    @import url(global.css);
    
>   任何超过3级的选择器，需要思考是否必要，是否有无歧义的，能唯一命中的更简短的写法

##图像规范

*   内容图片建议使用JPG，可以拥有更好地显示效果；
*   装饰性图片使用PNG；
*   内容图片建议使用JPG，可以拥有更好地显示效果；
*   CSS Sprite是一种将数个图片合成为一张大图的技术（既可以是背景图也可以是前景图），然后通过偏移来进行图像位置选取；
*   CSS Sprite可以减少http请求；

##LESS

详情请见[less](http://www.bootcss.com/p/lesscss/)

##前端流程工具

详情请见[weflow](https://github.com/weixin/tmt-workflow)

##最后说两句

坚持一致性的原则。

一个团队的代码风格如果统一了，首先可以培养良好的协同和编码习惯，其次可以减少无谓的思考，再次可以提升代码质量和可维护性。

统一的代码风格，团队内部阅读或编辑代码，将会变得非常轻松，因为所有组员都处在一致思维环境中。
