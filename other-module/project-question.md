...

## ElementUI-tree
点击属性icon也会触发接口调用，因此屏蔽icon点击，使用css解决

```
    cursor: default;
    pointer-events: none;

```



## 记录第N天日期

```  
    let timeDate = new Date(),
    day = 1;
    timeDate.setDate(timeDate.getDate() + day);

```


### 换算时、分、秒

``` parseInt(item.studyTime/3600) 时 parseInt(item.studyTime/60) 分 parseInt(item.studyTime%60) s ```



## 模拟form提交参数

为简化旧项目流程，缩短开发时间，在不重构界面情况下；上个界面保存的数据直接到当前界面；由于数据形式是数组不能使用url传参方式，因此编写form形式插件。

```
$.extend({
	StandardPost:function(url, args){
		var form = $("<form method='post' style='display:none'></form>"), input;
		form.attr({ "action":url });
		args=JSON.parse(args);
		$.each(args, function(key2, value2){
			$.each(value2,function(key, value){
				input = $("<input type='hidden'>");
				input.attr({ "name":'objectArray['+key2+']['+key+']'});
				input.val(value);
				form.append(input);
			});
		});
		form.appendTo($('body'));
		form.submit();
		form.remove();
	}
});

```


## UM编辑器过滤获取内容

```
s.push(item.getContent());
s = s.join("\n");
s = $('<div>'+s+'</div>').find('img').each(function(index, el) {
    $(this)[0].src = $(this)[0].src.split('/').reverse()[0];
}).end().html()

```