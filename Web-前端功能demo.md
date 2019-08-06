



 一、六种轮播图
 1、鼠标点击小圆点，图片移动，无动画
   表现：点击小圆点，小圆点变色，同时显示对应的图片
   前提：小圆点与轮播的图片一样多
   思路：
      
      css：
      （1）设父盒子宽为一张图片的大小，设置overflow：hidden；相对定位
      （2）用ul和li来放所有的图片，设置ul的宽度为所有图片和的宽度（大于父盒子），将li排成一行；ul绝对定位
      
      js：
      （1）循环小圆点，为每个小圆点添加鼠标经过（onmouseover）事件，循环小圆点；
      （2）采用排他思想，将所有小圆点上的变色样式去掉；
      （3）将当前的鼠标停留的小圆点加变色样式，再利用下标*每张图片的大小，更新ul位置；
      
      关键代码：
        this.className = 'hover';     //为当前鼠标停留的小圆点添加hover样式
		  	boximg.style.left =-this.index*730 + "px";// 利用下标更新boximg这个ul标签的left值
 
 2、鼠标点击小圆点，图片移动，带缓动动画效果
   表现：同上
   前提：同上
   思路：
      
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
  
二、放大镜
三、立方体
四、仿360界面
五、webpack
六、git使用
七、项目

