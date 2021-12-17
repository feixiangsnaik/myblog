---
title: js数组
date: 2021-11-25 17:22:55
tags:
---
## splice 
### 删除某个数组元素,原数组改变，返回被删除或者被替换的哪个。
```
let a = [1,2,3,4,5]
let b = [1,2,3,4,5]
//如果想删除3，就找到第三项，删除1个（下标，个数），如果想替换，那么第三个参数是添加到删除的位置处
let aa = a.splice(2,1) //删除3
let bb = b.splice(2,1,'hello') //把3换成hello
console.log(a,b,aa,bb)
```
## slice 
### 原数组不变，返回数组为截取的
```
let a = [1,2,3,4,5]
let b = a.slice(1,-1)
console.log(a,b,'ab')
//a=[1,2,3,4,5] b=[2,3,4]
```
## map
### 返回一个新数组，内容只包括返回的值。
    var nn = [ { a: 'ss',b:'b1' },{ a: 'aa',b:'b2' },{ a : '11',b:'b3'} ] 
    var index = nn.map(item =>{ return {d:item.a,b:item.b}})
    console.log(index) [{d:'ss',b:'b1'},...]
    //返回指定某个元素的下标
    var nn = [ { a: 'ss' },{ a: 'aa' },{ a : '11'},{ a: '33' },{ a: '88' } ] 
    var index = nn.map(item => item.a).indexOf(33)
    console.log(index)
## findIndexOf
  1. 查找对象数组，然后返回指定内容的对象所在的索引。
## every
  1. 如果每个都满足，那么就返回true