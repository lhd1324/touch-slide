####在移动端判断滑动方向
再我们组内看博客的时候，不小心看到了这么一个相关的标题，一看原来是个草稿，所以自己就利用该标题对其做一个简单的内容补充。(主要是自己好久没更新文章了，所以在这里小小的装一下&&》00《&&)
据自己了解，在移动端判断滑动方向，主要是根据触屏的坐标位置来计算的，在触屏开始时记录此时的坐标位置，在触屏结束时再次记录坐标位置，通过计算可以知道滑动的方向。
这里自己利用了触屏事件 touchs.
可以开始了吧，首先创建个元素，用于绑定触屏的事件
	
	<div class="slide" id="slide">
	</div>
这里给这个元素绑定两个事件触屏开始，触屏结束
		
	function selele(obj){
		return document.getElementById(obj)
	}
	selele("slide").ontouchstart=function(e){//绑定触屏开始事件
	    ....
    }
    selele("slide").ontouchend=function(e){//绑定触屏结束事件
	    ....
    }
 在绑定完成后，就需要记录触屏开始和结束的位置
		 
	var startx=0;//记录触屏开始x轴向的位置坐标
	var starty=0;//记录触屏开始y轴向的位置坐标
	var endx=0;//记录触屏结束x轴向的位置坐标
	var endy=0;//记录触屏结束y轴向的位置坐标
	function slidestart(e){
          startx=e.touches[0].pageX;
          starty=e.touches[0].pageY;
    }
	function slideend(e){
	      endx=e.changedTouches[0].pageX;
          endy=e.changedTouches[0].pageY;
    }
   记录结果之后，同时也是触屏结束时进行位置坐标的计算从而确定滑动方向
   
	function dirresult(){
	      var x=endx-startx;
          var y=endy-starty;
	      alert("在x轴向滑动:"+x+" || "+"在y轴向滑动:"+y);
    }
  从而就确定了滑动的方向。
  
 在slide.html包含完整的demo,其中也包含了移动端的拖动小案例，可供大家参考，望大家多多建议，有更好的方法》-00-《呵呵，望透漏一下。
