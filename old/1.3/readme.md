1.3 模块化--编写通用模块
---
##### 预定义变量
###### require
> require函数可以引入模块与json文件 —— 1.3.1  

###### exports
> exports导出函数 —— 1.3.1  

###### module
> module.exports导出json对象与函数 —— 1.3.1  

##### 模块初始化
> 一个模块中的JS代码仅在模块第一次被使用时执行一次，并在执行过程中初始化模块的导出对象。之后，缓存起来的导出对象被重复利用。 —— 1.3.2  
自我理解：多次require依然是指向同一个对象。既require引入模块的时候就是初始化模块，后续引入依然指向的是第一次引入时初始化的对象。  

##### 主模块
> 程序启动时首先加载的程序。例如 1.3.2 的index.js  

##### 二进制模块
> 除了js编写模块以外，还能使用c/c++编写.node模块。

##### 总结
1. Nodejs是一个JS脚本解析器。跨平台是因为复制了Nodejs到各个平台下，然后添加路径到系统变量中，即可在命令行使用```node```命令  
2. 尽量只使用js编写模块。连C语言都不会人也只能如此了。  

##### 代码的组织和部署
NodeJS编写程序前，为了有个良好的开端，首先需要准备好代码的目录结构和部署方式，就如同修房子要先搭脚手架。  

###### 模块路径解析规则
require支持```/```和盘符绝对路径，也支持```./```的相对路径。但是路径如果一变化，整过过程就折腾的够呛，php也有类似的经历。  
**内置模块**
> 直接传递模块名
```
var fs = require('fs');
```

**自定义模块（node_modules）**
> node自定义了一个node_modules模块来存放模块信息，安装模块后存放模块的位置。模块名/文件名，不指定文件名的情况下默认index.js，指定文件名调用指定的文件（unofficial/main）。
```
var unofficial = rquire('unofficial');
```

##### package
> 上文已经涉及到了  

##### npm
> npm作为nodejs的生态圈，这个包管理的使用也很重要
```
npm install unofficial
npm install unofficial@0.0.1 //安装包0.0.1版本的unofficial
npm install //按照package.json安装
npm help //查看更多命令
```

##### 文件操作
```
/**
 * 文件复制
 * copy()
 **/
node fs a.txt b.txt
/**
 * 文件夹遍历
 * showAllFiles()
 **/
node fs ./
```

##### 批量替换文件--
有一个这样的需求，在工作中有一项工作是必须的。批量处理压缩包，有手动操作过百多个文件的，也有找同事帮忙写c#，然后自己学习更改的，也有bat的。方式多种多样，nodejs或许也是一种很好方法。如此我不妨试试写一写。  
1. 文件到文件夹（文件a.txt替换文件夹A,B,C下的a.txt）  
2. 利用path模块优化文件遍历函数traversal.js   
3. 文件压缩，压缩单个文件a.txt到a.zip（使用外部模块node-archiver）```npm install archiver --save```这个外部模块可以根据实际情况使用，可以简化一下。具体这里不细说。  
4. 文件夹压缩
5. 优化（moment.js）

##### 参考资料
1. [七天学会NodeJS](http://nqdeng.github.io/7-days-nodejs)
2. [nodejs api module](https://nodejs.org/api/modules.html)
3. [模块的初始化](http://www.ituring.com.cn/article/177569)
4. [nodejs api fs](https://nodejs.org/api/fs.html)
5. [nodejs api stream](https://nodejs.org/api/stream.html)
6. [node-archiver](https://github.com/archiverjs/node-archiver)
7. [zip解压压缩的其他方案](http://www.html-js.com/article/Nodejs-study-notes-something-about-archive-and-unarchive-in-nodejs)  
8. [时间格式化方法](https://github.com/moment/moment)