一、六种轮播图

    
    1、鼠标点击小圆点，图片移动，无动画
  
      表现：点击小圆点，小圆点变色，同时显示对应的图片
      前提：小圆点与轮播的图片一样多
     
      思路:
      css：
      （1）设父盒子宽为一张图片的大小，设置overflow：hidden；相对定位
      （2）用ul和li来放所有的图片，设置ul的宽度为所有图片和的宽度（大于父盒子），将li排成一行；ul绝对定位
      
      js：
      （1）循环小圆点，为每个小圆点添加鼠标经过（onmouseover）事件，循环小圆点；
      （2）采用排他思想，将所有小圆点上的变色样式去掉；
      （3）将当前的鼠标停留的小圆点加变色样式，再利用下标*每张图片的大小（730），更新ul位置；
      
      关键代码：
        this.className = 'hover';     //为当前鼠标停留的小圆点添加hover样式
	boximg.style.left =-this.index*730 + "px";// 利用下标更新boximg这个ul标签的left值
 

    2、鼠标点击小圆点，图片移动，带缓动动画效果
      表现：同上
      前提：同上
      思路: 
      css：同上
      
      js：
       缓动动画： leader：初始值 targer：目标值 
       步长计算公式：leader = leader + (targer - leader) / 10;
       需要使用setInterval定时器
       
      （1）循环小圆点，为每个小圆点添加鼠标经过（onmouseover）事件，循环小圆点；
      （2）采用排他思想，将所有小圆点上的变色样式去掉；
      （3）将当前的鼠标停留的小圆点加变色样式，用target记录当前下标*每张图片的大小的数值；
      （4）在setInterval中通过缓动动画公式，使leader一点一点接近target
 
      关键代码：
       leader = 0；
       target = -this.index*730;
       setInterval(function(){
		leader = leader + (target - leader) / 10; //有瑕疵，会有残差，leader最后不一定等于target
		boximg.style.left = leader + "px";
	},30);
	  
	  
    3、 左右焦点轮播图（缓动动画）
      表现：无小圆点，点击图片左右span，进行切换图片
      前提：无
      思路: 
      css：
      （1）在div里面添加两个span，定位定到图片两侧，设置为左右按钮；
      （2）当鼠标移动到图片上是，两个span按钮显示出来，鼠标离开，按钮隐藏；
      js：
      （1）为大盒子添加鼠标经过（onmouseover）和鼠标离开（onmouseout）离开事件，对应的事件处理程序函数为display：block/none；
      （2）左右span点击事件（onclick），左：target -=730；右：target +=730；
      （3）使用缓动动画和setInterval；
      （4）对于target，需要判断边界值，是否超出了图片范围
 
      关键代码：
      if(target>=0) target=0;//最左边第一张
      if(target<=-3650) target=-3650;//最右边最后一张
      
      
    4、 无缝轮播（循环），自动
      表现：无小圆点，无左右按钮，定时，自动循环轮播切换图片
      前提：无
      思路: 
      css：
      （1）因为是无缝循环轮播，所以需要将前两张图片复制一份，放到最后面；
      js：
      （1）使用一个变量num=0，在setInterval中，num做递减运算，然后更新imgli这个ul元素的left；
      （2）要对num进行判断，当num小于等于第一张图片副本位置的时候，要将num置为0（让ul快速的跳到第一张图片上，这样就实现了无缝）；
      （3）为大盒子添加鼠标经过（onmouseover）和鼠标离开（onmouseout）离开事件；
      （4）鼠标经过（onmouseover），关闭定时器：clearInterval，鼠标离开（onmouseout），开启定时器：setInterval；
 
      关键代码：
       timer = setInterval(auto,40);//开启定时器
       clearInterval(timer);//关闭定时器
      
    5、无缝轮播（循环），带左右按钮，带小圆点
    
    6、仿网易无缝轮播
    7、附加 css3 百叶窗轮播图
    
二、仿淘宝放大镜


三、立方体（3d tranform）
  1、正方体
  
  2、长方体
  
四、仿360动画界面（css3 动画）

五、webpack
六、git使用
七、项目

