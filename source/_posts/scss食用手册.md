---
title: scss食用手册
author: 猪皮
avatar: >-
  https://cdn.jsdelivr.net/gh/wudalei/static@1.1/avatar/avator.jpg
authorAbout: 一个兴趣使然的猿
authorDesc: 一个兴趣使然的猿
categories: 随想
comments: false
keywords: Sakura
date: 2019-08-11 22:35:03
authorLink:
tags:
description:
photos: https://cdn.jsdelivr.net/gh/wudalei/static@1.1/image/2.jpg
---
# 总结下scss的食用规则
**希望能坚持一周写一篇博客ヽ(✿ﾟ▽ﾟ)ノ**

**********

## 变量的定义
**通过$符号去声明一个变量！**
```实例(☄⊙ω⊙)☄
$color-black:#333
.btn{
  color:$color-black;
}
```
**嵌套**
提高代码可读性！
```实例(☄⊙ω⊙)☄
.title{
  span{
    color:$color-black;
  }
  div{
    display:flex;
  }
}
```
**引入**
再@important指令的位置导入代码片段并合并到当前css文本!
```实例(☄⊙ω⊙)☄
//home.scss
page{
  background-color:black;
}

//my.scss
@import 'home';
box{
  display:block
}
```
**混合器**
@mixin+name来定义混合操作，可减少复用的代码，可以灵活的向Mixin传递变量和参数!多用于浏览器兼容前缀
```实例(☄⊙ω⊙)☄
@Mixin btn-style($param){
          border-radius: $radius;
      -ms-border-radius: $radius;
     -moz-border-radius: $radius;
  -webkit-border-radius: $radius;
}
.box-btn{
  @include btn-style(10px);
}
```
**继承**
@extend可继承设置的固定样式，减少冗余代码,
```实例(☄⊙ω⊙)☄
//如果没有被继承则无法输出到css文件。
%btn-style{
  border-radius:20rpx;
  color:white;
  background:#777777;
}
.box-btn{
  @extend %btn-style;
}
```
**操作符**
scss中可以用标砖的算术运算符运算！
```实例(☄⊙ω⊙)☄
image{
  height:100px*5;
  width:50px*300%;
}
```
**父级选择器**
"&"关键字可在嵌套使用伪类选择器或是跟后缀
```实例(☄⊙ω⊙)☄
a{
  color:black;
  &:hover{
    color:red;
  }
  &-a1{
    border:1px soild white;
  }
}
```
**属性嵌套**
css属性也是可以嵌套的！
```实例(☄⊙ω⊙)☄
.title{
 font:{
   size:30px;
   weight:500;
   stylt:normal;
 }
}
```