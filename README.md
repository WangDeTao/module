# 模块化


模块化是一种管理、生产方式，一种解决问题的方案


+ script标签
  1. 污染全局
  2. 按script顺序加载
  3. 文件依赖关系靠开发人员主观

+ Commonjs    
	
	require方法同步加载

+ AMD/CMD
	
	（1）AMD（异步模块定义）是Requirejs对模块的定义规范
	
	1. require([module],callback)
	2. define(id,[depends],callback)

	require接口加载一系列模块，define接口定义并暴露一个模块
	
```
	define(['./a','./b'],function(){
	//依赖一开始就写好
	a.add1()
	...
	b.add2()
	...
	})
``` 
	
	优点：适合浏览器异步加载模块； 可以并行加载多个模块。
	
	（2）CMD是SeaJS推广过程对模块定义的规范化。（Commonjs和AMD的基础上提出）
	
```
	define(function(require,exports,module){
		//依赖可以就近写
		var a  = require('./a');
		a.add1();
		...
		if(status){
			var b = require('./b');
			b.add2();
		}
	})
```

优点：依赖就近，延迟执行；很容易在服务器中运行。

（3）AMD和CMD区别

> 对于依赖模块，AMD是提前执行，CMD是延迟执行。
> AMD推崇依赖前置；CMD推崇依赖就近，在用到某个模块才require。
> AMD的API是默认一个当多个用；CMD的API严格区分，推崇职责单一

+ ES6模块化

import导入模块；export导出模块
```
	// a.js
	export var PI = 3.1415 ;
	export function sum(){
		console.log(PI+1);
	}
	
	//main.js
	import {PI,sum} from './a'
	var b = sum(PI);
```

目前js引擎较少支持es6模块化，babel做法转换成支持的require 


