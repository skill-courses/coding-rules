# Javascript 中代码格式

#### 1. 缩进

- 强制使用一致的缩进（`2` 个空格，不允许出现 `4` 个空格，禁止使用 `tab` 进行缩进）；

  ```
  // good
  function hello(indentSize, type) {
    if (indentSize === 2 && type !== 'tab') {
      console.log('Each next indentation will increase on 2 spaces');
    }
  }
  
  // bad
  function hello(indentSize, type) {
      if (indentSize === 4 && type !== 'tab') {
          console.log('Each next indentation will increase on 4 spaces');
      }
  }
  ```

- `switch` 下的 `case` 和 `default` 必须增加一个缩进层级；

  ```
  // good
  switch (variable) {
    case '1':
      // do...
      break;
      
    case '2':
      // do...
      break;
      
    default:
    // do...
  }
  
  // bad
  switch (variable) {
  case '1':
      // do...
      break;
  
  case '2':
      // do...
      break;
  
  default:
      // do...
  }
  ```

#### 2. 空行

- 不允许多个空行，最大空行数不允许超过 `2` 行；

  > 空白对于分离代码代码段逻辑是有帮助的，有时候可以提高代码的可读性；但过量的空白会占用更多的屏幕。

  ```
  // good
  var foo = 5;
  
  var bar = 3;
  
  // bad
  var foo = 5;
  
  
  
  var bar = 3;
  ```

#### 3. 空格

- 二元运算符两侧必须有一个空格，一元运算符与操作对象之间不允许有空格；

  ```
  var a = !arr.length;
  a++;
  a = b + c;
  ```

- 用作代码块起始的左花括号 `{` 前必须有一个空格；

  ```
  // good
  if (condition) {
  }
  
  while (condition) {
  }
  
  function funcName() {
  }
  
  // bad
  if (condition){
  }
  
  while (condition){
  }
  
  function funcName(){
  }
  ```

- `if / else / for / while / function / switch / do / try / catch / finally` 关键字后，必须有一个空格；

  ```
  // good
  if (condition) {
  }
  
  while (condition) {
  }
  
  (function () {
  })();
  
  // bad
  if(condition) {
  }
  
  while(condition) {
  }
  
  (function() {
  })();
  ```

- 在对象创建时，属性中的 `:` 之后必须有空格，`:` 之前不允许有空格；

  ```
  // good
  var obj = {
      a: 1,
      b: 2,
      c: 3
  };
  
  // bad
  var obj = {
      a : 1,
      b:2,
      c :3
  };
  ```

- 函数声明、具名函数表达式、函数调用中，函数名和 `(` 之间不允许有空格；

  ```
  // good
  function funcName() {
  }
  
  var funcName = function funcName() {
  };
  
  funcName();
  
  // bad
  function funcName () {
  }
  
  var funcName = function funcName () {
  };
  
  funcName ();
  ```

- `,` 和 `;` 前不允许有空格；

  ```
  // good
  var a, b;
  callFunc(a, b);
  
  // bad
  var a , b ;
  callFunc(a, b) ;
  ```

- 在函数调用、函数声明、括号表达式、属性访问、`if / for / while / switch / catch` 等语句中，`()` 和 `[]` 内紧贴括号部分不允许有空格；

  ```
  // good
  
  callFunc(param1, param2, param3);
  
  save(this.list[this.indexes[i]]);
  
  needIncream && (variable += increament);
  
  if (num > list.length) {
  }
  
  while (len--) {
  }
  
  
  // bad
  
  callFunc( param1, param2, param3 );
  
  save( this.list[ this.indexes[ i ] ] );
  
  needIncreament && ( variable += increament );
  
  if ( num > list.length ) {
  }
  
  while ( len-- ) {
  }
  ```

- 单行初始化的数组与对象，如果包含元素，`{}` 和 `[]` 内紧贴括号部分不允许包含空格；

  > 初始化包含元素的数组与对象，只有当内部元素的形式较为简单时，才允许写在一行。元素复杂的情况，还是应该换行书写。

  ```
  // good
  var arr1 = [];
  var arr2 = [1, 2, 3];
  var obj1 = {};
  var obj2 = {name: 'obj'};
  var obj3 = {
      name: 'obj',
      age: 20,
      sex: 1
  };
  
  // bad
  var arr1 = [ ];
  var arr2 = [ 1, 2, 3 ];
  var obj1 = { };
  var obj2 = { name: 'obj' };
  var obj3 = {name: 'obj', age: 20, sex: 1};
  ```

- 行尾不得有多余的空格；

  ```
  // good
  var foo = 0;
  var baz = 5;
  
  // bad
  var foo = 0;//•••••
  var baz = 5;//••
  ```

#### 4. 换行

- 每个独立语句结束后必须换行；

- 每行不得超过 `120` 个字符；超长的不可分割的代码允许例外，如复杂的正则表达式；

- 运算符处换行时，运算符必须在新行的行首；

  ```
  // good
  if (user.isAuthenticated()
    && user.isInRole('admin')
    && user.hasAuthority('add-admin')
    || user.hasAuthority('delete-admin')
  ) {
    // Code
  }
  
  var result = number1 + number2 + number3
    + number4 + number5;
  
  
  // bad
  if (user.isAuthenticated() &&
    user.isInRole('admin') &&
    user.hasAuthority('add-admin') ||
    user.hasAuthority('delete-admin')) {
    // Code
  }
  
  var result = number1 + number2 + number3 +
    number4 + number5;
  ```

- 在函数声明、函数表达式、函数调用、对象创建、数组创建、`for` 语句等场景中，不允许在 `,` 或 `;` 前换行；

  ```
  // good
  var obj = {
    a: 1,
    b: 2,
    c: 3
  };
  
  foo(
    aVeryVeryLongArgument,
    anotherVeryLongArgument,
    callback
  );
  
  
  // bad
  var obj = {
    a: 1
    , b: 2
    , c: 3
  };
  
  foo(
    aVeryVeryLongArgument
    , anotherVeryLongArgument
    , callback
  );
  ```

- 对于 `if...else...`、`try...catch...finally` 等语句，推荐使用在 `}` 号后添加一个换行的风格，使代码层次结构更清晰，阅读性更好；

  ```
  if (condition) {
    // some statements;
  }
  else {
    // some statements;
  }
  
  try {
    // some statements;
  }
  catch (ex) {
    // some statements;
  }
  ```