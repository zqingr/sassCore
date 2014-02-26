t#sassCore 3.0——Just for Better

sassCore参考了[compass](http://compass-style.org/)和[bourbon](http://bourbon.io/)等众多优秀的sass库，根据项目实践，归纳总结而成，一直以来为了更好而不断完善。

##sassCore特点：

* 涵盖范围广，核心文件有setting，css3，media-queries，mixin，grid，reset；扩展文件有animate，font-face，btn，message，form，table，helps，typography；除此之外还有两个集合文件function和base。
* sassCore采用开关机制，让样式更可控。如对是否支持ie6/7等众多条件可以通过设置为true或false来搞定。
* sassCore采用了sass 3.2.0版本以后的重大更新技术，让开发者更加方便，同时解析的css文件更加优越。如sass默认变量机制（默认变量!default，在应用的时候只需在你引入sassCore文件之前，重新申明变量就ok，而不需要去修改sassCore文件），placeholder选择器（有调用才会解析出相应的组合申明样式，避免了先前的class申明不管是否调用都会有样式解析出来）等。
* sassCore借鉴优秀的作品，根据实战创造新的方法，紧跟前沿，每一个文件都是经过深思熟虑，几易其稿，在实用和卓越上狠下功夫。
* sassCore设计了两种调用方式，一种是只调用功能，不产生任何多余的css代码；另一种是包含了些重置样式，为团队的合作开发提供了良好的解决方案。

##sassCore文件简略说明

sassCore包括两个集合文件（base，function）和两个文件夹（core，ext）。其中core文件夹中为核心基础文件，包括setting，css3，media-queries，mixin，grid，reset；而ext文件夹中是一些扩展文件，包括animate，font-face，btn，message，form，table，typography，helper。

两个集合文件（base，function）导入的都是core中的文件，区别在于base除了提供基本功能之外还会生成一份reset样式，而function则只提供基本功能。至于ext中的文件则属于额外的一些模块扩展，可根据需求导入。

###core文件

####setting
负责基础变量的文件，如常用的颜色，字体等变量。

####css3
负责css3属性前缀的文件。参考了[bourbon](http://bourbon.io/)，然后进行一系列的扩展及优化，以使解析出来的代码更加合理。

####media-queries
负责响应式宽度判断的文件。主要是对响应式布局的一些宽度判断，来自paranoida的[sass-mediaqueries](https://github.com/paranoida/sass-mediaqueries)。

####mixin
负责功能方面的文件。这里我们大概分成三个部分，一个是混合部分即mixin，一个是placeholder选择器部分即%，最后就是我们的function函数部分。我们常用的include及extend当然就是来自于这里了。

####grid
负责网格系统的文件。默认为固定宽度布局（1000px），可以通过设置$gridPercentSwitch为true来切换为流体布局，也可以通过设置$gridSpanSwitch为true或false来控制是否输出各个网格的class。

###reset
在[normalize](http://necolas.github.io/normalize.css/)的基础上，根据目前我们大家的使用习惯进行了一些归零行动，及设置文字字体颜色，是否输出打印样式。

###ext文件

####animate
将[animate.css](http://daneden.github.io/animate.css/)转成scss版本，默认不输出任何样式，需要什么动画先导入对应的动画文件，然后include调用即可。

####font-face
来自[Font Awesome](http://fontawesome.io/)的字体图标，可以根据自己的需求使用其他字体图标，默认不输出任何class，可根据实际需求输出其中的某些icon。参考了大漠的[font-awesome](https://github.com/airen/w3cplusSass/tree/master/lib/module/font-awesome)模块

####btn
为按钮设计的文件，里面定义了一系列mixin，可用于自定义按钮，默认生成两种按钮

####message
交互提示信息，包括警告，错误，成功，提示四种状态的样式

####form
提供了表单元素样式及几种常见的表单组合样式，可通过变量控制输出

####table
提供几种常用的表格样式，可通过变量来控制输出

####helper
常用的几个class，可以根据自己的喜好定义。

####typography
负责文字排版的文件。这里主要考虑到文章详细页和其他页面的一些不同情况而给详细页加入了article这个class，里面的一些元素如ul，li，p给予一定的样式，而不是清零。

##使用说明

因为sass不能导入在线sass文件，而sassCore也没有提供安装版的使用，所以默认统一放在D盘进行调用，如导入base，`@import "D:/sassCore/base"`。

一般来说单人模式可直接调用base，团队多人多文件可由设计公用样式的人导入base，其余人员则导入function，以免重复申明样式。