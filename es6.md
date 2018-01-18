1. 在let和const之间，建议优先使用const
```js
// bad
var a = 1, b = 2, c = 3;

// good
const a = 1;
const b = 2;
const c = 3;

// best
const [a, b, c] = [1, 2, 3];
```
2. 静态字符串一律使用单引号或反引号，不使用双引号。动态字符串使用反引号。

```js
// bad
const a = "foobar";
const b = 'foo' + a + 'bar';

// acceptable
const c = `foobar`;

// good
const a = 'foobar';
const b = `foo${a}bar`;
const c = 'foobar';
```
3. 使用数组成员对变量赋值时，优先使用解构赋值。
```js 
const arr = [1, 2, 3, 4];

// bad
const first = arr[0];
const second = arr[1];

// good
const [first, second] = arr;
```
* 3.1 函数的参数如果是对象的成员，优先使用解构赋值。
```js
// bad
function getFullName(user) {
const firstName = user.firstName;
const lastName = user.lastName;
}

// good
function getFullName(obj) {
const { firstName, lastName } = obj;
}

// best
function getFullName({ firstName, lastName }) {
}
```
* 3.2 如果函数返回多个值，优先使用对象的解构赋值，而不是数组的解构赋值。这样便于以后添加返回值，以及更改返回值的顺序。

```js
// bad
function processInput(input) {
return [left, right, top, bottom];
}

// good
function processInput(input) {
return { left, right, top, bottom };
}

const { left, right } = processInput(input);
```
4. 单行定义的对象，最后一个成员不以逗号结尾。多行定义的对象，最后一个成员以逗号结尾。
```js
// bad
const a = { k1: v1, k2: v2, };
const b = {
  k1: v1,
  k2: v2
};

// good
const a = { k1: v1, k2: v2 };
const b = {
  k1: v1,
  k2: v2,
};
```
* 4.1 对象尽量静态化，一旦定义，就不得随意添加新的属性。如果添加属性不可避免，要使用Object.assign方法。
```js
// bad
const a = {};
a.x = 3;

// if reshape unavoidable
const a = {};
Object.assign(a, { x: 3 });

// good
const a = { x: null };
a.x = 3;
```
* 4.2 对象的属性和方法，尽量采用简洁表达法，这样易于描述和书写。
```js
var ref = 'some value';

// bad
const atom = {
  ref: ref,

  value: 1,

  addValue: function (value) {
    return atom.value + value;
  },
};

// good
const atom = {
  ref,

  value: 1,

  addValue(value) {
    return atom.value + value;
  },
};
```
5. 使用扩展运算符（...）拷贝数组。
```js
// bad
const len = items.length;
const itemsCopy = [];
for (let i = 0; i < len; i++) {
  itemsCopy[i] = items[i];
}

// good
const itemsCopy = [...items];
```

* 5.1 使用 Array.from 方法，将类似数组的对象转为数组。
```js
const cName = document.querySelectorAll('.className');
const cNameArr = Array.from(cName);
```

6. 立即执行函数可以写成箭头函数的形式。
```js
(() => {
  console.log('Welcome to the Internet.');
})();
```

* 6.1 那些需要使用函数表达式的场合，尽量用箭头函数代替。因为这样更简洁，而且绑定了 this。
```js
// bad
[1, 2, 3].map(function (x) {
  return x * x;
});
// good
[1, 2, 3].map((x) => {
  return x * x;
});
// best
[1, 2, 3].map(x => x * x);
```
* 6.2 箭头函数取代Function.prototype.bind，不应再用 self/_this/that 绑定 this。

```js
// bad
const self = this;
const boundMethod = function(...params) {
  return method.apply(self, params);
}

// acceptable
const boundMethod = method.bind(this);

// best
const boundMethod = (...params) => method.apply(this, params);
```
* 6.3 所有配置项都应该集中在一个对象，放在最后一个参数，布尔值不可以直接作为参数。
```js
// bad
function divide(a, b, option = false ) {
}

// good
function divide(a, b, { option = false } = {}) {
}
```
* 6.4 不要在函数体内使用 arguments 变量，使用 rest 运算符（...）代替。因为 rest 运算符显式表明你想要获取参数，而且 arguments 是一个类似数组的对象，而 rest 运算符可以提供一个真正的数组。

```js
// bad
function concatenateAll() {
  const args = Array.prototype.slice.call(arguments);
  return args.join('');
}

// good
function concatenateAll(...args) {
  return args.join('');
}
```
* 6.5 使用默认值语法设置函数参数的默认值。
```js
// bad
function handleThings(opts) {
  opts = opts || {};
}

// good
function handleThings(opts = {}) {
  // ...
}
```
7. 注意区分 Object 和 Map，只有模拟现实世界的实体对象时，才使用 Object。如果只是需要key: value的数据结构，使用 Map 结构。因为 Map 有内建的遍历机制。
```js
let map = new Map(arr);

for (let key of map.keys()) {
  console.log(key);
}

for (let value of map.values()) {
  console.log(value);
}

for (let item of map.entries()) {
  console.log(item[0], item[1]);
}
```
8. 用 Class，取代需要 prototype 的操作。因为 Class 的写法更简洁，更易于理解。
```js
// bad
function Queue(contents=[]){
  this._queue=[...contents];
}
Queue.prototype.pop=function(){
  const value=this.queue[0];
  this._queue.splice(0,1);
  return value;
}

// good 
class Queue{
  constructor (contents=[])[
    this._queue=[...contents];
  ]
  pop(){
    const value=this._queue[0];
    this._queue.splice(0,1);
    return value;
  }
}
```
8.1 使用extends实现继承，因为这样更简单，不会有破坏instanceof运算的危险。
```js
// bad 
const inherits=require('inherits);
function PeekableQueue(contents){
  Queue.apply(this,contents);
}
inherits(PeekableQueue,Queue);
PeekableQueue.prototype.peek=function(){
  return this._queue[0];
}

// good
class PeekableQueue extends Queue{
  return thhis._queue[0];
}

```
9. Module 语法是 JavaScript 模块的标准写法，坚持使用这种写法。使用import取代require。
```js
// bad 
const moduleA =require('moduleA');
const func1=moduleA.func1;
const func2=moduleB.func2;
// good 
import {func1,func2} from 'moduleA';

```
9.1 使用export取代module.exports。
```js
// commonJs  methods
var React =require ('react);
var Breadcrumbs=React.createClass({
  render(){
    return <nav />;
  }
})

module.exports = Breadcrumbs;

// Es6 methods

import React from 'react';
class Breadcrumbs extends React.Component{
  render(){
    return <nav />;
  }
};
export default Breadcrumbs;

如果模块只有一个输出值，就使用export default，如果模块有多个输出值，就不使用export default，export default与普通的export不要同时使用。
```
9.2 不要在模块输入中使用通配符。因为这样可以确保你的模块之中，有一个默认输出（export default）。
```js
// bad 
import * as myobject from './importModule';

// good

import myobject from './importModule';

```




