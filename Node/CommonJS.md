# CommonJS
* 概述
* AMD
* CMD
* CommonJS
* Node的require机制

## 概述
CommonJS规范的核心是允许通过require方法来<span style="color: red;">**同步**</span>的加载依赖模块,类似的标准还有AMD（Asynchronous Module Definition）和CMD(Common Module Definition)以及<a href="https://github.com/umdjs/umd">UMD（Universal Module Definition）</a>,UMD宣称可以兼容CommonJS和AMD,并且可以跨多平台。

## AMD
AMD规范正如其名，是通过<span style="color: red;">**异步**</span>加载，Open Ui5用的就是这种方式，该方式需要提前将依赖列出来如下:
	
    require(['module1', 'module2'], function('mod1', 'mod2'){
    	mod1.test();
    	mode2.test();
    })		
该方式的优势在于如果依赖组件的名字发生改变，只需要修改一个地方便可以。
## CMD
CMD规范是指就近异步加载依赖，在需要的时候加载，示例如下：
	
	define(function(require, exports, module) {
	   var mod1 = require('module1');//同步
	   mod1.start();
	   require.async('./b', function(b) {//异步
	   		b.doSomething();
	   }
  });
	});		
该方式的有点是比较符合开发习惯，需要的时候加载，但是不容易辨识依赖了哪些模块。
## CommonJS
### 概述
Node应用即采用CommonJS规范，CommonJS规范四个核心的词汇是module、exports、require、global，每个文件都是独立的模块，拥有独立的作用域，内部变量方法都是私有的，如果想要设置为公共的需要定义为global的属性。
	
	global.pubProperty= 'test';	
module对象代表当前模块，module对象的exports属性是对外的接口，使用require加载某个模块加载的正是exports属性。
	
	//test.js
	var testId= '123';
	var testFun= function(){
		return 1;
	}
	module.exports.id= testId;
	module.exports.fun= testFun;	
每个模块在第一次加载之后都会被缓存下来，下次加载会直接读取缓存，其加载顺序是按照在代码中的出现顺序。
### 模块的module对象
对于一个模块最核心的莫过于module对象，每个模块内部都有一个module对象，该对象包含以下属性：
	
	module.id 模块的识别符，一般指带有绝对路径的模块文件名
	module.filename 带有绝对路径的文件名
	module.loaded 返回布尔值，表示模块是否加载完成
	module.parent 返回一个对象，表示调用该模块的模块
	module.children 返回一个数组，表示该模块要用到的其它模块，即依赖
	module.exports 对外输出对象，require其实调用的就是该对象
module还有一个exports属性，其与module.exports的关联类似于
	
	var exports= module.exports;	
所以要避免下面的用法
	
	exports= function(){}	
这种写法会导致exports与module.exports的关联失效。

module.parent指调用的对象，如果直接通过命令行调用，该值为空。
## Node的require机制
### require命令加载规则
	
	//表示加载一个核心模块或者迭代寻找所有node_modules中的模块
	var mod1= require('mod');
	//表示加载一个绝对路径的模块
	var mod2= require('/path/mod');
	//表示加载一个相对路径的模块
	var mod3= require('./path/mod');
	//先找到moduleT的位置再基于该路径向下寻找
	var mod4= require('moduleT/path/mod');    
如果指定模块不加后缀，默认会按照.js、.json、.node的顺序去搜索，.node会以编译后的二进制文件进行解析。
### 对于目录的加载规则
如果require的是一个路径，那么node会自动查看该路径下面是否有package.json文件，并寻找main字段作为入口文件，如果没有则会加载该目录下面的index.js或index.node.
### 缓存
模块第一次加载某个模块时会进行缓存，后续重复加载时会读缓存，所有的缓存都存在require.cache中，如果需要删除缓存需要使用下面方式
	
	delete require.cache[moduleName];
缓存是以绝对路径作为识别符，如果绝对路径发生改变，会重新加载该模块。
### NODE_PATH
Node执行一个脚本时，会首先查看环境变量NODE_PATH,所以如果路径比较复杂，可以将文件加入node_modules或者NODE_PATH环境变量。
### 模块的循环加载
如果发生模块的循环加载，即A加载B，B又加载A，则B将加载A的不完整版本。
### require.main
require的main属性可以用来判断模块是直接执行还是调用执行，如果返回module则是直接执行。
## 模块加载机制
### 模块加载
CommonJS加载机制为：<span style="color: red;">输入时输出的拷贝</span>，一旦输出某个值，将不再受模块内部的改变影响。
	
	//test.js
	var counter= 1;
	module.exports.counter= counter;
	module.exports.incCounter= function(){
		counter++;
	}	
加载模块test.js:
	
	//main.js
	var counter= require('./test').counter;
	var incCounter= require('./test').incCounter;
	
	console.log(counter);//1
	incCounter();
	console.log(counter);//1	
### require
在模块中使用的require并非全局的require，而是指向当前模块的module.require命令，其又调用了Node内部命令Module._load.
	
	Module._load = function(request, parent, isMain) {
	  // 1. 检查 Module._cache，是否缓存之中有指定模块
	  // 2. 如果缓存之中没有，就创建一个新的Module实例
	  // 3. 将它保存到缓存
	  // 4. 使用 module.load() 加载指定的模块文件，
	  //    读取文件内容之后，使用 module.compile() 执行文件代码
	  // 5. 如果加载/解析过程报错，就从缓存删除该模块
	  // 6. 返回该模块的 module.exports
	};
上面的第4步，采用module.compile()执行指定模块的脚本，逻辑如下。
	
	Module.prototype._compile = function(content, filename) {
	  // 1. 生成一个require函数，指向module.require
	  // 2. 加载其他辅助方法到require
	  // 3. 将文件内容放到一个函数之中，该函数可调用 require
	  // 4. 执行该函数
	};	
上面的第1步和第2步，require函数及其辅助方法主要如下。
	
	require(): 加载外部模块
	require.resolve()：将模块名解析到一个绝对路径
	require.main：指向主模块
	require.cache：指向所有缓存的模块
	require.extensions：根据文件的后缀名，调用不同的执行函数		
一旦require函数准备完毕，整个所要加载的脚本内容，就被放到一个新的函数之中，这样可以避免污染全局环境。该函数的参数包括require、module、exports，以及其他一些参数。

Module._compile 方法是同步执行的，所以 Module._load 要等它执行完成，才会向用户返回 module.exports 的值。
<a href="http://javascript.ruanyifeng.com/nodejs/module.html">参考文档</a>

