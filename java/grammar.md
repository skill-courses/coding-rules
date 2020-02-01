# Java 语法规范

### 1. 枚举类

枚举常量间用逗号隔开，换行可选。

没有方法和文档的枚举类可写成数组初始化的格式：
```
    private enum Suit { CLUBS, HEARTS, SPADES, DIAMONDS }
```

### 2. 变量声明

- 每次只声明一个变量

    不要使用组合声明，比如`int a, b;`。
- 需要时才声明，并尽快进行初始化

    不要在一个代码块的开头把局部变量一次性都声明了，而是在第一次需要使用它时才声明。 
    局部变量在声明时最好就进行初始化，或者声明后尽快进行初始化。

### 3. 数组

数组初始化，可写成块状结构
```
new int[] {
  0, 1, 2, 3 
}

new int[] {
  0,
  1,
  2,
  3
}

new int[] {
  0, 1,
  2, 3
}

new int[]{0, 1, 2, 3}
```

### 4. switch语句

- 缩进

    switch块中的内容缩进为4个空格，每个switch标签后新起一行，再缩进4个空格，写下一条或多条语句。
- 注释

    在一个switch块内，每个语句组要么通过break, continue, return或抛出异常来终止，要么通过一条注释来说明程序将继续执行到下一个语句组， 
    任何能表达这个意思的注释都是OK的(典型的是用`// fall through`)。这个特殊的注释并不需要在最后一个语句组(一般是`default`)中出现。
    
    示例：
    ```
        switch (input) {
          case 1:
          case 2:
            prepareOneOrTwo();
            // fall through
          case 3:
            handleOneTwoOrThree();
            break;
          default:
            handleLargeNumber(input);
        }
    ```
 -  default
 
    每个switch语句都包含一个default语句组，即使它什么代码也不包含。
    
### 5. 注解

注解紧跟在文档块后面，应用于类、字段、方法和构造函数，一个注解独占一行。这些换行不属于自动换行，因此缩进级别不变。

例如：
```
    @Override
    @Nullable
    public String getNameIfPresent() { ... }
```

### 6. 注释

块注释与其周围的代码在同一缩进级别。它们可以是`/* ... */`风格，也可以是`// ...`风格。对于多行的`/* ... */`注释，后续行必须从`*`开始， 并且与前一行的`*`对齐。

以下示例注释都是OK的：
```
/*
 * This is                   
 * okay.                     
 */

/* Or you can
 * even do this. */

// And so  
// is this.
```

### 7. 修饰符

类和成员的modifiers如果存在，则按Java语言规范中推荐的顺序出现：
```
public protected private abstract static final transient volatile synchronized native strictfp
```
