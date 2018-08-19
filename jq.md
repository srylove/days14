
通过 || && 等短路语句进行判断语句的书写
连贯接口： 链式调用 命令查询媒体 重载 参数映射 ？？？
实现链式调用需返回自身值，设置数据缓存区
命令查询媒体

重载
最简单的重载使用switch进行条件判断，然后执行代码块
function addMethod(object, name, fn) {
　　var old = object[name]; //把前一次添加的方法存在一个临时变量old里面
　　object[name] = function() { // 重写了object[name]的方法
　　　　// 如果调用object[name]方法时，传入的参数个数跟预期的一致，则直接调用
　　　　if(fn.length === arguments.length) {
　　　　　　return fn.apply(this, arguments);
　　　　// 否则，判断old是否是函数，如果是，就调用old
　　　　} else if(typeof old === "function") {
　　　　　　return old.apply(this, arguments);
　　　　}
　　}
}
var people = {
　　values: ["Dean Edwards", "Alex Russell", "Dean Tom"]
};
addMethod(people, "find", function() {
　　return this.values;
});
addMethod(people, "find", function(firstName) {
　　var ret = [];
　　for(var i = 0; i < this.values.length; i++) {
　　　　if(this.values[i].indexOf(firstName) === 0) {
　　　　　　ret.push(this.values[i]);
　　　　}
　　}
　　return ret;
});
addMethod(people, "find", function(firstName, lastName) {
　　var ret = [];
　　for(var i = 0; i < this.values.length; i++) {
　　　　if(this.values[i] === (firstName + " " + lastName)) {
　　　　　　ret.push(this.values[i]);
　　　　}
　　}
　　return ret;
});
console.log(people.find()); 
console.log(people.find("Dean")); 
console.log(people.find("Dean Edwards")); 

arguments 传入参数的值
arguments.length 为函数实参个数。
arguments.callee 引用函数自身。

jquery sizzle 嗯，准备开始读源码

document.addEventListener("DOMContentloaded") jq ready 实现