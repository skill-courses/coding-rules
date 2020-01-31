# Java 编程实践

### 1. @Override

重写的方法一定要用@Override注解。

### 2. 捕获的异常：不能忽视

绝大部分情况下对捕获的异常要做出响应。典型的响应方式是打印日志，或者如果它被认为是不可能的，则把它当作一个`AssertionError`重新抛出。

如果确实不需要在catch块中做任何响应，需要做注释加以说明，例如：
```
try {
  int i = Integer.parseInt(response);
  return handleNumericResponse(i);
} catch (NumberFormatException ok) {
  // it's not numeric; that's fine, just continue
}
return handleTextResponse(response);
```

### 3. 静态成员：使用类进行调用

使用类名调用静态的类成员，而不是具体某个对象或表达式。

```
Foo aFoo = ...;
Foo.aStaticMethod(); // good
aFoo.aStaticMethod(); // bad
somethingThatYieldsAFoo().aStaticMethod(); // very bad
```

### 4. Finalizers: 禁用

极少会去重写Object.finalize。
