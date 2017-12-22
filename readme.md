## 1.创建package.json文件  
  
  
  
cmd>npm init  
  
按照提示输入package名，description，email，版本等信息，就会自动生成  
```
{
  "name": "npmdemo001",
  "version": "1.0.3",
  "description": "demo",
  "main": "./lib/module.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/ccq18/npmdemo.git"
  },
  "keywords": [
    "demo"
  ],
  "author": "ccq18",
  "license": "ISC",
  "bugs": {
    "url": "https://github.com/ccq18/npmdemo/issues"
  },
  "homepage": "https://github.com/ccq18/npmdemo#readme"
}
```

  
   
  
## 2.编写你的module  
  
创建lib目录，创建module.js文件，内容：  
  
var A = "value A";  
var B = "value B";  
exports.values = function() {  
return { A: A, B: B };  
}  
  
   
  
## 3.添加用户  
  
cmd>npm adduser  
  
按照提示输入用户名，密码和邮箱  
  
   
  
## 4.发布  
  
cmd>npm publish  
  
如果不带参数，会查找当前目录下的package.json文件，按照该文件描述信息发布module    
  
如果指定目录，就在这个目录下查找package.json文件    
  
 Ps：
 1.包名不能喝目前已有的包冲突   
 2.记得去网站上验证邮箱
 3.记得添加.gitignore
 ```
/node_modules
/.idea
.DS_Store
```
 4.注意package.json的main 是默认执行的文件名
## 5.验证  
  
在http://search.npmjs.org/可以查询刚刚发布的module    
  
   
## 6.下载使用  
  
cmd>yarn add npmdemo001  
  
可以看到在node_modules目录下载了yypi模块  
  
在node.exe目录新建test.js文件：  
  
var util = require('util');  
var A = "a different value A";  
var B = "a different value B";  
//var m1 = require('npmdemo001/lib/module');
var m1 = require('npmdemo001');

util.log('A='+A+' B='+B+' values='+util.inspect(m1.values()));
  
   
  
cmd>node test.js  
  
得到输出：  
  
30 Dec 23:48:44 - A=a different value A B=a different value B values={ A: 'value  
  
A', B: 'value B' }  
  
   
  
## 7.多版本发布  
  
修改package.json里的版本号，重新npm publish即可  
  
   
  
## 8.取消发布  
  
cmd>npm unpublish