### webpack多页应用配置过程

1. 多个入口(entry),每个页面对应一个入口,理解为 js 资源.
2. 多个 html 实例,webpack 使用html-webpack-plugin 插件来生成 html 页面.
3. 每个页面需要对应的 css 文件.webpack 使用 extract-text-webpack-plugin 抽取 css.

``` js
npm install --save-dev html-webpack-plugin
````


### css3中-moz、-ms、-webkit,-o前缀分别表示：

//-ms代表【ie】内核识别码

//-moz代表火狐【firefox】内核识别码

//-webkit代表谷歌【chrome】/苹果【safari】内核识别码

//-o代表欧朋【opera】内核识别码



### 动画效果有三种实现形式
animation/transform/transition


#### 【transform 变换】

--属性：

（1）translate(x,y) 定义 2D 转换，移动x、y轴的位置

（2）translate3d(x,y,z)  定义 3D 转换，移动x、y、z轴的位置

（3）translateX(x) 定义转换，只是用 X 轴的值

（4）translateY(y) 定义转换，只是用 Y 轴的值

（5）translateZ(z) 定义 3D 转换，只是用 Z 轴的值

（6）scale(x,y) 定义 2D 缩放转换。

（7）scale3d(x,y,z) 定义 3D 缩放转换

（8）scaleX(x) 通过设置 X 轴的值来定义缩放转换

（9）scaleY(y) 通过设置 Y 轴的值来定义缩放转换

（10）scaleZ(z) 通过设置 Z 轴的值来定义 3D 缩放转换

（11）rotate(10deg) 2d旋转10度

（12）rotate3d(x,y,z,10deg)    3d旋转

（13）rotateX(10deg) 沿着X轴的3D旋转

（14）rotateY(10deg) 沿着Y轴的3D旋转

（15）rotateZ(10deg) 沿着Z轴的3D旋转

（16）skew(10deg,10deg) 定义沿着 X 和 Y 轴的 2D 倾斜转换

（17）skewX(angle) 定义沿着 X 轴的 2D 倾斜转换

（18）skewY(angle) 定义沿着 Y 轴的 2D 倾斜转换


#### 【transition】（运动属性 运动过渡时间 运动类型 延迟时间）

例如：

transition: width 1s linear 2s;

or还可以写成:

transition-property: width;//规定应用过渡的css属性的名称（必填）

transition-duration: 1s;//定义过渡效果花费的时间，默认是0（必填）

transition-timing-function: linear;//规定过渡次奥过的时间曲线，默认是ease

--有4个属性：

（1）transition-property 规定设置过渡效果的 CSS 属性的名称

（2）transition-duration 规定完成过渡效果需要多少秒或毫秒

（3）transition-timing-function 规定速度效果的速度曲线

 liner:匀速

 ease:缓冲，慢快慢

 ease-in:加速

 ease-out:减速

 ease-in-out:先加速再减速

（4）transition-delay 定义过渡效果何时开始

【注：】一般这两个属性是一起用的，来实现一次性的动画效果，例如下箭头展开旋转：

.icon-xiajiantou{ transition:all 0.4s;-webkit-transition:all 0.4s;}

.icon-xiajiantou.active{ transform: rotate(180deg);-webkit-transform:rotate(180deg);}


#### 【animation】

CSS3的animation属性可以像Flash制作动画一样，通过控制关键帧来控制动画的每一步，实现更为复杂的动画效果。ainimation实现动画效果主要由两部分组成： 

1）通过类似Flash动画中的帧来声明一个动画； 

2）在animation属性中调用关键帧声明的动画。

属性：

（1）animation-name：none为默认值，将没有任何动画效果，其可以用来覆盖任何动画 

（2）animation-duration：默认值为0，意味着动画周期为0，也就是没有任何动画效果 

（3）animation-timing-function：与transition-timing-function一样 

（4）animation-delay：在开始执行动画时需要等待的时间 

（5）animation-iteration-count：定义动画的播放次数，

默认为1，

如果为infinite，则无限次循环播放 

（6）animation-direction：默认为nomal，每次循环都是向前播放，（0-100），另一个值为alternate，动画播放为偶数次则向前播放，如果为基数词就反方向播放 

（7）animation-state：默认为running，播放，paused，暂停 

（8）animation-fill-mode：定义动画开始之前和结束之后发生的操作，

none默认值，动画结束时回到动画没开始时的状态；

forwards，动画结束后继续应用最后关键帧的位置，即保存在结束状态；

backwards，让动画回到第一帧的状态；

both：轮流应用forwards和backwards规则。

@keyframes

CSS3的animation制作动画效果主要包括两部分：

1. 用关键帧声明一个动画，

2.在animation调用关键帧声明的的动画。

@keyframes就是关键帧。这个帧与Flash里的帧类似，一个动画中可以有很多个帧。

一个@keyframes中的样式规则是由多个百分比构成的，可以在这个规则上创建多个百分比，从而达到一种不断变化的效果。另外，@keyframes必须要加webkit前缀。

例如下面公司项目中的loading加载旋转效果，页面没加载完成之前，会一直旋转

.loading{animation: rotate 1s linear infinite;}

@keyframes rotate {

   0% {transform: rotate(0deg);}

   25%{transform: rotate(90deg);}

   50%{transform: rotate(180deg);}

   75%{transform: rotate(270deg);}

   100% {transform: rotate(360deg);}

}

@-webkit-keyframes rotate {

   0% {-webkit-transform: rotate(0deg);}

   25%{-webkit-transform: rotate(90deg);}

   50%{-webkit-transform: rotate(180deg);}

   75%{-webkit-transform: rotate(270deg);}

   100% {-webkit-transform: rotate(360deg);}

}

@-moz-keyframes rotate {

   0% {-moz-transform: rotate(0deg);}

   25%{-moz-transform: rotate(90deg);}

   50%{-moz-transform: rotate(180deg);}

   75%{-moz-transform: rotate(270deg);}

   100% {-moz-transform: rotate(360deg);}

}

@-ms-keyframes rotate {

   0% {-ms-transform: rotate(0deg);}

   25%{-ms-transform: rotate(90deg);}

   50%{-ms-transform: rotate(180deg);}

   75%{-ms-transform: rotate(270deg);}

   100% {-ms-transform: rotate(360deg);}

}

@-o-keyframes rotate {

   0% {-o-transform: rotate(0deg);}

   25%{-o-transform: rotate(90deg);}

   50%{-o-transform: rotate(180deg);}

   75%{-o-transform: rotate(270deg);}

   100% {-o-transform: rotate(360deg);}

}


#### 【区别：】

transition的优点在于简单易用，但是它有几个很大的局限。 

（1）transition需要事件触发，所以没法在网页加载时自动发生。 

（2）transition是一次性的，不能重复发生，除非一再触发。 

（3）transition只能定义开始状态和结束状态，不能定义中间状态，也就是说只有两个状态。 

（4）一条transition规则，只能定义一个属性的变化，不能涉及多个属性。 

animation属性类似于transition，他们都是随着时间改变元素的属性值，其主要区别在于：transition需要触发一个事件才会随着时间改变其CSS属性；animation在不需要触发任何事件的情况下，也可以显式的随时间变化来改变元素CSS属性，达到一种动画的效果。



