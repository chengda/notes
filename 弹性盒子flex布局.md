# 弹性盒子布局
## 1. 概念

* 主轴（main axis）： 盒子内子元素的排列轴线  
* 交叉轴（cross axis）：与主轴垂直方向的轴线  

## 2. 盒子样式
* display: flex;  
  必须为flex，表示应用弹性盒子布局。
  
* flex-direction: row | row-reverse | column | column-reverse;    
  表示主轴方向。
  
    * row（默认） 横向从左到右  
    * row-reverse 横向从右到左  
    * column 纵向从上到下  
    * column-reverse 纵向从下到上  

* flex-wrap: nowrap | wrap | wrap-reverse;  
    主轴方向上换行属性
    
    * nowrap（默认） 不换行，元素多了会被压缩
    * wrap 自动换行，元素多了会自动换到下一行
    * wrap-reverse 自动换行，，元素多了会自动换到上一行
    
* justify-content: flex-start | flex-end | center | space-between | space-around;
    元素在主轴上的对齐方式
    
    * flex-start（默认） 向主轴开始的方向靠拢
    * flex-end 向主轴结束的方向靠拢
    * center 向主轴中间位置靠拢
    * space-between 在主轴上平均分布，元素之间间隔相等。
    * space-around 在主轴上平均分布，元素两侧空间相等。

* align-items: flex-start | flex-end | center | baseline | stretch;
    元素在交叉轴方向的对齐方式
    
    * flex-start 向交叉轴开始的方向对齐。
    * flex-end 向交叉轴结束的方向对齐。
    * center 在交叉轴方向居中对齐。
    * baseline 各元素第一行文字的基线对齐。
    * stretch (默认) 如果元素未设置高度或设为auto，将被拉伸占满整个盒子在交叉轴方向上的空间。

* align-content: flex-start | flex-end | center | space-between | space-around | stretch;
    多行元素，各行在交叉轴方向上的对齐方式。
    
    * flex-start 向交叉轴开始方向靠拢。
    * flex-end 向交叉轴结束方向靠拢。
    * center 向交叉轴中间靠拢。
    * space-between 各行在交叉轴方向平均分布，行间保持间隔相等。
    * space-around 各行在交叉轴方向平均分布，行两侧保持相同大小的空间。
    * stretch（默认值） 各行在交叉轴方向上被拉伸成相等大小，占满整个交叉轴空间。
    
## 3. 盒内元素样式
六个属性（order、flex-grow、flex-shrink、flex-basis、flex、align-self），介绍常用的两个：

* flex: none | [<flex-grow> <flex-shrink> ?|| flex-basis]   
    flex是flex-grow，flex-shrink和flex-basis三个属性的合并写法。
    
    一般常用的值有：
    
    * flex: 1;   在主轴上所有设置这个值的元素降自动平分主轴方向上剩余的空间。

* align-self: auto | flex-start | flex-end | center | baseline | stretch;

    * 这个属性会覆盖盒子样式中的align-items样式，让该元素不服从外层盒子设置的统一样式。

## 4. 案例

[flex-playground](./_v_files/html/flex-playground.html)


