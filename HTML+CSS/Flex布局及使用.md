手记（这次更多是尝试一下Markdown的语法，详细的知识我会附上参考链接）  
# 关于Flex布局（Flexible Box，弹性布局）
### 一、应用范围
    任何一个容器都可指定为flex布局，`display：flex`  
    行内元素也可以使用flex布局，`display：inline-flex`  
    注：webkit内核浏览器须 `-webkit -flex`，使用flex布局后，子元素的float、clear和vertical-align属性将失效      
### 二、基本概念
  采用Flex布局的元素，称为Flex容器（flex container），简称”容器”。    
  子元素成为容器成员，称为Flex项目（flex item），简称”项目”。  
  容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）。  
  主轴的开始位置（与边框的交叉点）叫做main start，结束位置叫做main end；交叉轴的开始位置叫做cross start，结束位置叫做cross end。  
  项目默认沿主轴排列。单个项目占据的主轴空间叫做main size，占据的交叉轴空间叫做cross size。  
### 三、容器属性
+ flex-direction（决定主轴方向，水平或垂直哪个为主轴，以及排列方向）
+ flex-wrap
+ flex-flow
+ justify-content（项目如何在主轴对齐）
+ align-items（项目如何在交叉轴对齐）
+ align-content（多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。）   
如果想实现水平和垂直居中，使用`justify-content:center`和`align-items:center`即可。  
默认水平方向为主轴，排列方向由左向右`---->`;垂直方向为交叉轴，排列方向由上向下`↓`。  
### 四、属性详解
#### 1.flex-direction  
    可能有四个取值，与下图对应。  
    column-reverse：主轴为垂直方向，起点在下沿。 
    column：主轴为垂直方向，起点在上沿。  
    row（默认）：主轴为水平方向，起点在左端。  
    row-reverse：主轴为水平方向，起点在右端。       
![](../pic/flex布局flex-direction.png)    
#### 2.flex-wrap
    可能取三个值
    nowrap（默认）：不换行，所有项目都排在一条轴线上。  
    wrap：轴线上排列不下项目时，第一行在上方，向下换行。  
    wrap-reverse：轴线上排列不下项目时，第一行在下方，向上换行。  
寝室熄灯了，待完成，等熟悉下markdown的语法。  
[Flex 布局语法教程](http://www.runoob.com/w3cnote/flex-grammar.html)。
