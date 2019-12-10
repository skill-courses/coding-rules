# Javascript 语法规范

#### 1. 变量

- 变量在使用前必须通过 `var` 定义（`ES5`），不使用 `var` 定义变量将导致变量污染全局环境；

  ```JavaScript
  // good
  var name = 'MyName';
  
  // bad
  name = 'MyName';
  ```

- 使用 `ES6` 新语法之后，禁止使用 `var` 来定义变量；

- 不允许初始化变量值为 `undefined`，字面值 `undefined` 的主要目的是用于比较；

  ```javascript
  // bad
  var foo = undefined;
  let bar = undefined;
  ```

  

- 每个 `var` 只能声明一个变量；

  > 一个 `var` 声明多个变量，容易导致较长的行长度，并且在修改时容易造成逗号和分号的混淆。

  ```javascript
  // good
  var a = [];
  var b = [];
  var c = {};
  
  // bad
  var a = [],
    b = [],
    c = {};
  ```

  

- 变量必须 **即用即声明**，不得在函数或其它形式的代码块起始位置统一声明所有变量；

  > 变量声明与使用的距离越远，出现的跨度越大，代码的阅读与维护成本越高。

  ```javascript
  // good
  function kv2List(source) {
    var list = [];
  
    for (var key in source) {
      if (source.hasOwnProperty(key)) {
        var item = {
          k: key,
          v: source[key]
        };
        list.push(item);
      }
    }
  
    return list;
  }
  
  // bad
  function kv2List(source) {
    var list = [];
    var key;
    var item;
  
    for (key in source) {
      if (source.hasOwnProperty(key)) {
        item = {
          k: key,
          v: source[key]
        };
        list.push(item);
      }
    }
  
    return list;
  }
  ```

  

#### 2. 语句与表达式

- 不得省略语句结束的分号；

- 在 `if / else / for / do / while` 语句中，即使只有一行，也不得省略块 `{...}`；

  ```javascript
  // good
  if (condition) {
    callFunc();
  }
  
  // bad
  if (condition) callFunc();
  if (condition)
    callFunc();
  ```

  

- 函数定义结束不允许添加分号，如果是函数表达式，分号是不允许省略；

  ```javascript
  // good
  function funcName() {
  }
  
  // bad
  function funcName() {
  };
  
  // 如果是函数表达式，分号是不允许省略的。
  var funcName = function () {
  };
  ```

#### 3. 条件判断

- 使用 `===` 和 `!==` 来进行判断，不允许使用 `==` ，仅当判断 `null` 或 `undefined` 时，允许使用 `== null`；

  > 避免判断中的隐式类型转换。

- 尽可能使用简洁的表达式；

  ```javascript
  // 字符串为空
  
  // good
  if (!name) {
    // ......
  }
  
  // bad
  if (name === '') {
    // ......
  }
  
  // 数组非空
  
  // good
  if (collection.length) {
    // ......
  }
  
  // bad
  if (collection.length > 0) {
    // ......
  }
  
  // 布尔不成立
  
  // good
  if (!notTrue) {
    // ......
  }
  
  // bad
  if (notTrue === false) {
    // ......
  }
  
  // null 或 undefined
  
  // good
  if (noValue == null) {
    // ......
  }
  
  // bad
  if (noValue === null || typeof noValue === 'undefined') {
    // ......
  }
  ```

  

- 如果函数或全局中的 `else` 块后没有任何语句，需要删除 `else`；

  ```javascript
  // bad
  function foo() {
    if (x) {
      return y;
    } else {
      return z;
    }
  }
  
  // good
  function foo() {
    if (x) {
      return y;
    }
  
    return z;
  }
  ```

- 不要在循环体中包含函数表达式，事先将函数提取到循环体外；

  > 循环体中的函数表达式，运行过程中会生成循环次数个函数对象。

  ```javascript
  // good
  function clicker() {
    // ......
  }
  
  for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    addListener(element, 'click', clicker);
  }
  
  
  // bad
  for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    addListener(element, 'click', function () { });
  }
  ```

  

- 对循环内多次使用的不变值，在循环外用变量缓存；

  ```javascript
  // good
  var width = wrap.offsetWidth + 'px';
  for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    element.style.width = width;
    // ......
  }
  
  
  // bad
  for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    element.style.width = wrap.offsetWidth + 'px';
    // ......
  }
  ```

  

- 对有序集合进行遍历时，缓存 `length` ；

  ```javascript
  for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    // ......
  }
  ```

#### 4. 类型检测

- 基本类型检测优先使用 `typeof` ；

- 对象类型检测使用 `instanceof`；

- 判断 `null` 使用下面的方法：

  ```javascript
  var exp = null;
  if (!exp && typeof (exp) != 'undefined' && exp != 0) {
    console.log('is null');
  }　
  ```

  

#### 5. 对象

- 使用对象字面量的方式创建 `Object`；

  ```javascript
  // good
  var obj = {};
  
  // bad
  var obj = new Object();
  ```

  

- 不允许修改和扩展任何原生对象和宿主对象的原型；

  ```javascript
  // 以下行为绝对禁止
  String.prototype.trim = function () {
  };
  ```

  

- 访问属性时，能使用 `.` 来访问的属性，需要使用 `.` 来访问；

  ```javascript
  // good
  info.age;
  info['more-info'];
  
  // bad
  info[age];
  ```

  

- 使用 `for in` 遍历对象时, 使用 `hasOwnProperty` 过滤掉原型中的属性；

  ```javascript
  var newInfo = {};
  for (var key in info) {
    if (info.hasOwnProperty(key)) {
      newInfo[key] = info[key];
    }
  }
  ```

  

#### 6. 数组

- 使用数组字面量 `[]` 创建新数组，除非想要创建的是指定长度的数组；

  ```javascript
  // good
  var arr = [];
  
  // bad
  var arr = new Array();
  ```

  

- 不允许使用 `for in` 遍历数组；

  > 数组对象可能存在数字以外的属性, 这种情况下 `for in` 不会得到正确结果。
  >
  > 1. `for in` 迭代顺序依赖于执行环境，不一定保证顺序；
  > 2. `for in` 不仅会遍历当前对象，还包括原型链上的可枚举属性；
  > 3. `for in` 没有 `break` 中断；
  > 4. `for in` 不适合遍历数组，主要应用为对象。

  ```javascript
  let arr = [{ age: 1 }, { age: 5 }, { age: 100 }, { age: 34 }];
  for (let key in arr) {
    console.log(key, arr[key]);
  }
  // 打印
  // 0 {age: 1}
  // 1 {age: 5}
  // 2 {age: 100}
  // 3 {age: 34}
  ```

#### 7. 函数

- 一个函数的长度控制在 30行以内；

  > 将过多的逻辑单元混合在一个大的函数里，会导致难以维护的缺点，且不利于单元测试。

- 禁止出现空函数；

  ```javascript
  // bad
  function foo() { }
  
  var foo = function () { };
  
  var foo = () => { };
  
  function* foo() { }
  
  var foo = function* () { };
  
  var obj = {
    foo: function () { },
  
    foo: function* () { },
  
    foo() { },
  
    *foo() { },
  
    get foo() { },
  
    set foo(value) { }
  };
  
  class A {
    constructor() { }
  
    foo() { }
  
    *foo() { }
  
    get foo() { }
  
    set foo(value) { }
  
    static foo() { }
  
    static *foo() { }
  
    static get foo() { }
  
    static set foo(value) { }
  }
  ```

- 参数设计，一个函数的参数输了一般控制在 `6` 个以内；

#### 