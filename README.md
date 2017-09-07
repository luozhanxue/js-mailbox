# js-mailbox
js原生写的邮箱

<html>
	<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title></title>
    </head>
    <style>
    	#word{
			width:1000px;
			height:310px;
			position:absolute;
			border:1px solid gray;
			left:0px;
			top:0px;
		}
		#word1{
			width:200px;
			height:310px;
			float:left;	
		}
		#word2{
			width:800px;
			height:310px;
			float:left;
		}
		#one{
			width:200px;
			height:100px;
			background:#336;	
		}
		#one a{
			background:#336;
			color:white;
			margin-left:20px;
			text-decoration:none;
			line-height:30px;
		}
		#one1{
			width:200px;
			height:200px;
			background:#336;
			margin-top:5px;		
		}
		#one1 a{
			background:#336;
			color:white;
			margin-left:20px;
			text-decoration:none;
			line-height:30px;
		}
		#two{
			width:800px;
			height:50px;
			background:#ccc;
		}
		#two1{
			width:800px;
			height:200px;
		}
		#lay{
			width:300px;
			margin-top:10px;
			float:right;	
		}
		#lay a{
			text-decoration:none;
		}
		
		
		
		
    </style>
    <script src="run.js"></script>
    <script>
    	window.onload = function(){
			
			var oTable = document.getElementById('tabl');
			var oTB= oTable.tBodies[0];
			var oA = document.getElementById('lay');
			var aA = oA.getElementsByTagName('a');
			var oDivSta = document.getElementById('sta');
			var oChk = document.getElementById('che'); //全选
			var oDel = document.getElementById('del'); //删除
			var aChk;
			var arr = [
			["李四1","王者归来....","2017-3-13"],
			["李四2","王者归来....","2017-3-13"],
			["李四3","王者归来....","2017-3-13"],
			["李四4","王者归来....","2017-3-13"],
			["李四5","王者归来....","2017-3-13"],
			["李四6","王者归来....","2017-3-13"],
			["李四7","王者归来....","2017-3-13"],
			["李四8","王者归来....","2017-3-13"],
			["李四9","王者归来....","2017-3-13"],
			["李四10","王者归来....","2017-3-13"],
			["李四11","王者归来....","2017-3-13"],
			["李四12","王者归来....","2017-3-13"],
			["李四13","王者归来....","2017-3-13"],
			["李四14","王者归来....","2017-3-13"],
			["李四15","王者归来....","2017-3-13"],
			["李四16","王者归来....","2017-3-13"],
			["李四17","王者归来....","2017-3-13"],
			["李四18","王者归来....","2017-3-13"],
			["李四19","王者归来....","2017-3-13"],
			["李四21","王者归来....","2017-3-13"],
			["李四22","王者归来....","2017-3-13"],
			["李四23","王者归来....","2017-3-13"],
			["李四24","王者归来....","2017-3-13"],
			["李四25","王者归来....","2017-3-13"]
			
			];
			
			var pageNum = 0;
			var otBody = document.getElementById('tbody');
			
			oChk.onclick = function() { //全选
				for(var i=0; i<aChk.length; i++) {
					aChk[i].checked = oChk.checked; 
				}
			}
			
			oDel.onclick = function(){ //删除
				//alert(aChk.length);
				for(var i=aChk.length-1;i>=0;i--){
					if(aChk[i].checked == true){
						arr.splice(pageNum*5+i,1);	
					}	
				}	
				show();
			}
			
			
			function show(){
				oTB.innerHTML = "";
				var num = 0;
				var aleft = (pageNum+1)*5;
				if(aleft<= arr.length){
					num = 5;
				} else {
					num = arr.length - pageNum*5;
				}
				for(var i=0; i<num;i++){
					var newTr = document.createElement('tr');
					var newTh = document.createElement('th');
					newTh.innerHTML = "<input type = 'checkbox'>";
					
					newTr.appendChild(newTh);
					for(var j = 0;j<3; j++){   
						newTD = document.createElement('td');
						newTD.innerHTML = arr[pageNum*5+i][j];
						newTr.appendChild(newTD);
					}
					oTB.appendChild(newTr);	
				}
				aChk = otBody.getElementsByTagName('input');
				
				oDivSta.innerHTML = "第"+(pageNum+1)+"页/共"+Math.ceil(arr.length/5)+"页";
			}
			show();
			aA[0].onclick = function(){//首页
				if(pageNum =0){
					pageNum =0;
				}
				show();	
			}
			aA[1].onclick = function(){//上一页
				pageNum--;
				if(pageNum <=0){
					pageNum =0;
				}
				show();	
			}
			aA[2].onclick = function(){//下一页
				pageNum++;
				if(pageNum >=parseInt(arr.length/5)){
					pageNum = parseInt(arr.length/5);
				}
				show();	
			}
			aA[3].onclick = function(){ //尾页
				pageNum =parseInt(arr.length/5)
				show();	
			}
			
			
		}
    </script>
    <body>
    	<div id="word">
        	<div id="word1">
            	<div id="one">
                	<a href="##">写信</a><br />
                    <a href="##">收信</a><br />
                    <a href="##">通讯录</a><br />
                </div>
                <div id="one1">
                	<a href="##">收信箱</a><br />
                    <a href="##">星际邮箱</a><br />
                    <a href="##">草稿箱</a><br />
                    <a href="##">己发送</a><br />
                    <a href="##">垃圾箱</a><br />
                    <a href="##">QQ邮件订阅</a><br />
                </div>
            </div>
            <div id="word2">
            	<div id="two">
                	<input type="button" value="删除" id="del">
                    <input type="button" value="转发" id="de2">
                    <input type="button" value="举报" id="de3">
                    
                </div>
                 <div id="two1">
                    <table width= "800" height="200" border="1" cellspacing="0" id="tabl">
                        <thead>
                            <tr>
                                <th width="50"><input type="checkbox" id="che"></th>
                                <th width="120">发件人</th>
                                <th width="500">主题</th>
                                <th width="130">时间</th>
                            </tr>
                        </thead>
                        <tbody id = "tbody">
                          
                        </tbody>
                    </table>
                    <div id="lay">
                   	    <div style=" float:left;" id="sta">第几页/共几页</div>
                        <a href="#">首页</a>
                        <a href="#">上一页</a>
                        <a href="#">下一页</a>
                        <a href="#">尾页</a>
                        
                    </div>
                 </div>
            </div>
        </div>
       
    </body>
</html>

<script>
//下面是调用的js代码
// JavaScript Document

function onScrollInfo (){ //JSON鼠标移动
	var scrillTop = document.documentElement.scrpllTop || document.body.scrollTop; //上	
	var scrillLeft = document.documentElement.scrpllLeft || document.body.scrollLeft;//左
	
	var scrWidth = document.body.scrollWidth; //宽
	var scrHeight = document.body.scrollHeight;//高
	
	var pageWidth = window.innerWidth || document.documentElement.scrollWidth; //页面的宽
	var pageHeight = window.innerHeight || document.documentElement.scrollHeight; //页面的高
	
	return{t:scrillTop, l:scrillLeft, w:pageWidth, h:pageHeight, pw:scrWidth, ph:scrHeight}; //返回值
}


function css(obj,attr,value){
	if(arguments.length == 2){
		if(attr == "opacity"){
			if(obj.currentStyle){
				return parseInt(obj.currentStyle[attr]*100);
			} else {
				return parseInt(getComputedStyle(obj,false)[attr]*100);
			}
		} else {
			if(obj.currentStyle){
				return parseInt(obj.currentStyle[attr]);
			} else {
				return parseInt(getComputedStyle(obj,false)[attr]);
			}
		}
	} else {
		if(attr == "opacity"){
			obj.style.opacity = value/100;
			obj.style.filter = "alpha(opacity:"+value+")";
		} else {
			obj.style[attr] = value;
		}
	}
}

function run(obj,json,model,endFunction){               //运动框架
	
		//attr:属性的名称,一组属性
		//json[attr]:相当于原来的iTarget,一组目标值
	
	var speed = 5;    //确定方向，即确定speed的值
	
	
		function runOne(){   //单次运动的函数
			for(var attr in json){
			if(model == 0){ //匀速运动
				if(json[attr] > css(obj,attr)){
					speed = 5;
				} else if(json[attr] <css(obj,attr)){
					speed = -5;
				} else {
					speed = 0;
				}
			} else {  //缓冲运动
				speed = (json[attr] - css(obj,attr))/10;
				if(speed >0){
					speed = Math.ceil(speed);  //向上取整
				} else if(speed<0){
					speed = Math.floor(speed);  //向下取整
				}
			}
				
				//obj.style[attr] = css(obj,attr) + speed;  //走
			//alert(css(obj,attr) + ":" + speed);
			css(obj,attr,css(obj,attr)+speed);
			
			if(css(obj,attr) ==json[attr] ||  Math.abs(json[attr] - css(obj,attr))<Math.abs(speed) ){				//到目标点后，停
					//obj.style[attr] = iTarget;
				css(obj,attr,json[attr]);
				//clearInterval(obj.timer);
				if(endFunction){
					endFunction();
				}
			}
		}
	}
	
	var flag = true; //假设所有要改变的属性，都达到目标值了
	
	for(var attr in json){
		if(css(obj,attr) != json[attr]){
			flag = false;
		}
	}
	
	if(flag){
		clearInterval(obj.timer);
	}
	
	
	clearInterval(obj.timer);       //开启之前先关闭，避免重复开启
	obj.timer = setInterval(runOne,30);  //重复执行单次运动，以达到运动效果
	
}
</script>

