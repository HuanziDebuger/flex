# flex 弹性布局的理解 

//A.容器上的属性，即父级元素或者根元素
  1.flex-direction 定义项目的排列方向
    row(从左边开始) row-reverse(从右边开始) 
    column(从顶端边开始) column-reverse(从底端开始)

  2.flex-wrap 定义是否换行
  	nowrap(不换行) wrap(向下换行) wrap-reverse(向上换行)

  3.flex-flow:row nowrap（默认值） 排列方向和换行的简写

  4.justify-content  定义水平对齐的方式 
    flex-start(左对齐)、flex-end(右对齐) center(居中对齐)
    flex-between(两端对齐) flex-around(边框对齐，且项目之间的间隔是边框的一倍)

  5.align-items     定于垂直对齐的方式
  	flex-start(顶端对齐) flex-end(底部对齐) center(垂直居中对齐)
  	baseline (项目的第一行文字基线对齐) stretch(如果项目未设置高度，将占满容器的高度)
  
  6.align-content   定义了多根轴线的对齐方式
    flex-start(左对齐)、flex-end(右对齐) center(居中对齐)
    flex-between(两端对齐) flex-around(边框对齐，且项目之间的间隔是边框的一倍)
    stretch(沾满整个交叉轴)

//B.项目上的属性，即子元素
  1.order  定义项目的排列顺序，
     整数允许负值，数值越小，排列越靠前，默认为0

  2.flex-grow   定义项目的放大比例
  	整数不允许负值 默认0，不放大

  3.flex-shrink 定义项目的缩小比例
    整数不允许负值 默认1，空间不足是都缩小，值为0时，不缩小

  4.flex-basis  定义项目占据的主轴空间
  	默认值auto，即项目的本来大消息
  5.flex   flex-grow|flex-shrink|flex-basis 的简写

  6.align-self  区别于其他项目的对齐方式，可以覆盖align-items
  	默认值auto，继承父级的对齐方式，没有父级等同于stretch,充满整个交叉轴
  	允许单个项目跟其他项目对齐方式不同

//
//
//
//
//
//
/*****************以下是详解*******************************************/

1.flex容器：采用flex布局的元素或者页面
  flex项目：flex容器里的所有子元素
  主轴：水平的排列的（main axis）   //其实就是父元素的宽
  交叉轴：垂直分布的 （cross axis） //其实就是父元素的高
  main start：主轴开始的位置与边框的交叉点   //左边起点
  mian end  : 主轴结束的位置与边框的交叉点   //右边起点
  cross start: 交叉轴开始的位置
  cross end  : 交叉轴结束的位置
  main  size : 单个项目占据的主轴空间
  cross size : 单个项目占据交叉轴的空间
2.容器的属性
  
  //flex-direction 决定主轴的方向，也是项目的排列方向
  
  flex-direction:row | row-reverse|colum|colum-reverse
	row（默认值）：主轴为水平方向，起点在左端。
	row-reverse：主轴为水平方向，起点在右端。
	column：主轴为垂直方向，起点在上沿。
	column-reverse：主轴为垂直方向，起点在下沿。

  //flex-wrap 定义换行属性
  
  flex-wrap: nowrap | wrap | wrap-reverse;
   nowrap(默认值)：不换行
   wrap: 换行，从左边开始向下换行
   wrap-reverse: 换行，第一行在下方，也就是向上换行

  //flex-flow 是项目排列方向（flex-direction）和换行(flex-wrap)的简写
    flex-flow: row nowrap(默认值); 

  //justify-content 项目在主轴上的对齐方式，也就是横向对齐方式
  justify-content: flex-start | flex-end | center | space-between | space-around;

  flex-start(默认值):左对齐
  flex-end:右对齐
  center:居中对齐
  space-between:两端对齐,项目之前的间隔都相等
  space-around:每个项目的两侧都相等，项目之间的间隔比边框间隔大一倍

  //align-items 项目在交叉轴上的对齐方式，即纵向对齐方式
  //
   align-items: flex-start | flex-end | center | baseline | stretch;
    flex-start：交叉轴的起点对齐。上对齐
    flex-end：交叉轴的终点对齐。  下对齐
    center：交叉轴的中点对齐。    居中对齐
    baseline: 项目的第一行文字的基线对齐。
    stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。

  //align-content 多跟轴线的纵向对齐方式，如果项目只有一根轴线，该属性不起作用。
  
   align-content: flex-start | flex-end | center | space-between | space-around | stretch;
	flex-start：与交叉轴的起点对齐。
    flex-end：与交叉轴的终点对齐。
    center：与交叉轴的中点对齐。
    space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
    space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
    stretch（默认值）：轴线占满整个交叉轴。


 3.项目上的属性（容器里的元素）

  //order 定义项目的排列顺序，数值越小，排列越靠前，默认为0
   order：0（默认值，此处可为负数，且必须是整数）

  //flex-grow 定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。
  //如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话）。
  //如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。
    flex-grow: 数字且为整数

  //flex-shrink 定义项目的缩小比例，默认为1，即如果空间不足，该项目将缩小
  //如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。
  //如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小。
    flex-shrink：number (默认值1，整数)

  //flex-basis 定义项目的大小，从而计算出主轴的剩余空间
  //属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。
  //浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小
    flex-basis:长度|auto (默认值)

 //flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。
 //该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)。
 flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]

 //align-self 定义跟其他项目不一样的对齐方式，可覆盖已经定义的align-items的属性
 //默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。
 //
 align-self: auto | flex-start | flex-end | center | baseline | stretch;
  





