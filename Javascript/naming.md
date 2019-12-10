# JavaScript 命名

- 变量使用驼峰命名法；

- 常量的名称全部字母大写，单词间以下划线分割；

- 函数名使用小驼峰命名法，函数名使用动宾短语；

  ```
  function getStyle(element) {
  }
  ```

- 函数的参数使用小驼峰命名法；

- 类使用大驼峰命名法，但是首字母需要大写（`Pascal` 命名法），类名使用名词；

- 类的属性 / 方法使用小驼峰命名法；

- 枚举变量使用 `Pascal` 命名法，枚举的属性名称全部大写，单词间以下划线分割；

  ```
  var TargetState = {
      READING: 1,
      READED: 2,
      APPLIED: 3,
      READY: 4
  };
  ```

- `boolean` 类型的变量使用 `is` 或 `has` 开头；

  ```
  var isReady = false;
  var hasMoreCommands = false;
  ```

### 