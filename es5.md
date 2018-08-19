this apply try 原型链 作用于 闭包


this 
在一般函数方法中使用 this 指代全局对象
作为对象方法调用，this 指代上级对象
作为构造函数调用，this 指代new 出的对象
apply 调用 ，apply方法作用是改变函数的调用对象，此方法的第一个参数为改变后调用这个函数的对象，this指代第一个参数
1.全局作用域或者普通函数中this指向全局对象window。
//直接打印
console.log(this) //window

//function声明函数
function bar () {console.log(this)}
bar() //window

//function声明函数赋给变量
var bar = function () {console.log(this)}
bar() //window

//自执行函数
(function () {console.log(this)})(); //window
2.方法调用中谁调用this指向谁
//对象方法调用
var person = {
    run: function () {console.log(this)}
}
person.run() // person

//事件绑定
var btn = document.querySelector("button")
btn.onclick = function () {
    console.log(this) // btn
}
//事件监听
var btn = document.querySelector("button")
btn.addEventListener('click', function () {
   console.log(this) //btn
})
3.在构造函数或者构造函数原型对象中this指向构造函数的实例
//不使用new指向window
function Person (name) {
    console.log(this) // window
    this.name = name;
}
Person('inwe')
//使用new
function Person (name) {
      this.name = name
      console.log(this) //people
      self = this
  }
  var people = new Person('iwen')
  console.log(self === people) //true
//这里new改变了this指向，将this由window指向Person的实例对象people

apply call
 改变this的指向
 apply:方法能劫持另外一个对象的方法，继承另外一个对象的属性.
 Function.apply(obj,args)方法能接收两个参数
 obj：这个对象将代替Function类里this对象
 args：这个是数组，它将作为参数传给Function（args-->arguments）

call:和apply的意思一样,只不过是参数列表不一样.

 Function.call(obj,[param1[,param2[,…[,paramN]]]])
 obj：这个对象将代替Function类里this对象
 params：这个是一个参数列表

try catch
在JavaScript可以使用try...catch来进行异常处理
try {
     foo.bar();
} catch (e) {
     alert(e.name + ": " + e.message);
}
Error具有下面一些主要属性：

description: 错误描述 (仅IE可用).  
fileName: 出错的文件名 (仅Mozilla可用).  
lineNumber: 出错的行数 (仅Mozilla可用).  
message: 错误信息 (在IE下同description)  
name: 错误类型.  
number: 错误代码 (仅IE可用).  
stack: 像Java中的Stack Trace一样的错误堆栈信息 (仅Mozilla可用).  

原型链
每个对象都有 __proto__ 属性，但只有函数对象才有 prototype 属性
在默认情况下，所有的原型对象都会自动获得一个 constructor（构造函数）属性，这个属性（是一个指针）指向 prototype 属性所在的函数（Person）
所有函数对象的 __proto__ 都指向 Function.prototype，它是一个空函数（Empty function）
所有对象的 __proto__ 都指向其构造器的 prototype

作用域
浏览器引擎在程序运行的前一刻会进行预编译
生成 GO AO对象，会将函数声明提到最前，作用域提升，函数中未使用var声明的变量会提升到全局

闭包
个人理解 将函数变量封装到一个作用域中，只能通过唯一的接口进行访问
