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


