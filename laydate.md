#laydate - 日历插件
## 1.引包(注意：目录need，skins，和laydate.js的层级关系是确定的，不能改变)
```html  
    <script src='laydate.js所在路径/laydate.min.js'></script>	
```
## 2.laydate的几种用法说明

+ 1.外部js调用

```js
	<!--嗨，客官，注意下面的class了，有了这个，也就有了输入框内部的日期图标了--!>
	<input id='start' type='text' class='laydate-icon'/>    
    <script>
    	laydate({
        	elem: '#start',	//这里只能用id选择器
            event: 'focus'	//触发事件
        });
    </script>
```
+ 2.图标触发日期

```js
	<input id='start2' />
    <span class='laydate-icon' onclick = "laydate({elem:'#start2'})"></span>
```
+ 3.自定义日期格式

```js
	<input id='start3' type='text' class='laydate-icon'/>    
    <script>
    	laydate({
        	elem: '#start3',	//这里只能用id选择器
            format: 'YYYY-MM_DD', //显示的日期格式
            festival: true, //是否显示节日           
            choose: function() {	//选择成功后的回调
            	alert('hello laydate');
            },
        });
    </script>
```
+ 4.日期范围限定在昨天到明天

```js
	<input id='start4' type='text' class='laydate-icon' />   
    <script>
    	laydate({
        	elem: '#start3',	//这里只能用id选择器
            min: laydate.now(-1),	//-1表示昨天，-2表示前天，以此类推。。。
            max: laydate.now(1)	//1表示明天，2表示后天，以此类推。。。
        });
    </script>
```
+ 5.日期范围限制

```js
	<!--注意： laydate可不仅仅使用于input输入框，其他元素标签当然也也不在话下，就比如下面的li--!>
	开始日：<li class="laydate-icon" id="startDate" style="width:200px; margin-right:10px;"></li>
    结束日：<li class="laydate-icon" id="endDate" style="width:200px;"></li>
    <script>
      var start = {
        elem: '#startDate',
        format: 'YYYY/MM/DD hh:mm:ss',
        min: laydate.now(), //设定最小日期为当前日期
        max: '2099-06-16 23:59:59', //最大日期
        istime: true,	//是否显示时分秒
        istoday: false,	//是否突出今天
        choose: function(datas){
           end.min = datas; //开始日选好后，重置结束日的最小日期
           end.start = datas //将结束日的初始值设定为开始日
        }
      };
      var end = {
        elem: '#end',
        format: 'YYYY/MM/DD hh:mm:ss',
        min: laydate.now(),
        max: '2099-06-16 23:59:59',
        istime: true,
        istoday: false,
        choose: function(datas){
          start.max = datas; //结束日选好后，重置开始日的最大日期
        }
      };
      //最后当然要记得调用了、、、
      laydate(start);
      laydate(end);
    </script>
```
## 3.最后再简单过一下laydate的全部参数
+ laydate(options)

```js
//options是一个对象，它包含了以下的key值和‘默认值’
{
	elem: '#idName', //需要显示日期的元素选择器，仅限与id
    event: 'click', //触发事件
    format: 'YYYY-MM-DD hh:mm:ss', //日期的显示格式
    istime: false, //是否显示时分秒
    isclear: true, //是否显示清空键
    istoday: true,	//是否显示今天
    issure: true,	//是否显示确认
    festival: true, //是否显示节日
    min: '1900-01-01 00:00:00', // 最小日期
    max: '2099-12-31 23:59:59', //最大日期
    start: '2014-6-15 23:00:00',  //开始日期
    fixed: false, //是否固定在可视区域
    zIndex: 99999999, //css z-index
    choose: function(dates){ //选择好日期的回调}
}
```
