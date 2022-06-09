一、什么是闭包？

声明一个变量，声明一个函数，在函数内部访问外部的变量，那么这个函数加这个变量叫做闭包。
如下代码：
```
var x='变量'
function f(){
    console.log(x)
}
```
二、闭包的用途是什么？

1.从外部读取内部的变量
```
function f1(){
    var n=666;
    function f2(){
        console.log(n);
    }
    return f2;
}
var resule=f1();
resule()  ///666
```
2.将创建的变量的值始终保持在内存中:
```
function f1(){
    var n=12;
    function f2(){
        console.log(++n);
        
    }
    return f2;
}
var result=f1();
result(); //13
```
函数f1中的局部变量n一直保存在内存中，并没有在f1调用后被自动清除。

3.封装对象的私有属性和私有方法。
```
function f1(n) {
  return function () {
    return n++;
  };
}
var a1 = f1(1);
a1() // 1
a1() // 2
a1() // 3
var a2 = f1(5);
a2() // 5
a2() // 6
a2() // 7
a1 和 a2 是相互独立的，各自返回自己的私有变量。
```
3、闭包的优缺点是什么？

优点：
闭包的优点是可以避免全局变量的污染；

缺点：
由于闭包会使得函数中的变量都被保存在内存中，内存消耗很大.

