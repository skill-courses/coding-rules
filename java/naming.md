# Java 命名约定

标识符只能使用ASCII字母和数字，因此每个有效的标识符名称都能匹配正则表达式\w+

### 1. 包名

包名全部小写，连续的单词只是简单地连接起来，不使用下划线。

### 2. 类名

类名都以`UpperCamelCase`风格编写。

类名通常是名词或名词短语，接口名称有时可能是形容词或形容词短语。现在还没有特定的规则或行之有效的约定来命名注解类型。

测试类的命名以它要测试的类的名称开始，以`Test`结束。例如，`HashTest`或`HashIntegrationTest`。

### 3. 方法名

方法名都以`lowerCamelCase`风格编写。

方法名通常是动词或动词短语。

下划线可能出现在JUnit测试方法名称中用以分隔名称的逻辑组件。一个典型的模式是：`test<MethodUnderTest>_<state>`，
例如`testPop_emptyStack`。 并不存在唯一正确的方式来命名测试方法。

### 4. 常量名

常量名命名模式为`CONSTANT_CASE`，全部字母大写，用下划线分隔单词。

常量名通常是名词或名词短语。

每个常量都是一个静态final字段，但不是所有静态final字段都是常量。在决定一个字段是否是一个常量时， 考虑它是否真的感觉像是一个常量。
例如，如果任何一个该实例的观测状态是可变的，则它几乎肯定不会是一个常量。
```
// Constants
static final int NUMBER = 5;
static final ImmutableList<String> NAMES = ImmutableList.of("Ed", "Ann");
static final Joiner COMMA_JOINER = Joiner.on(',');  // because Joiner is immutable
static final SomeMutableType[] EMPTY_ARRAY = {};
enum SomeEnum { ENUM_CONSTANT }

// Not constants
static String nonFinal = "non-final";
final String nonStatic = "non-static";
static final Set<String> mutableCollection = new HashSet<String>();
static final ImmutableSet<SomeMutableType> mutableElements = ImmutableSet.of(mutable);
static final Logger logger = Logger.getLogger(MyClass.getName());
static final String[] nonEmptyArray = {"these", "can", "change"};
```

### 5. 非常量字段名

非常量字段名以`lowerCamelCase`风格编写。

非常量字段名通常是名词或名词短语。

### 6. 参数名

参数名以`lowerCamelCase`风格编写。

参数应该避免用单个字符命名。

### 7. 局部变量名

局部变量名以`lowerCamelCase`风格编写，比起其它类型的名称，局部变量名可以有更为宽松的缩写。

虽然缩写更宽松，但还是要避免用单字符进行命名，除了临时变量和循环变量。

即使局部变量是final和不可改变的，也不应该把它示为常量，自然也不能用常量的规则去命名它。

### 8. 类型变量名（泛型中的类型参数名）

类型变量可用以下两种风格之一进行命名：
- 单个的大写字母，后面可以跟一个数字(如：E, T, X, T2)。
- 以类命名方式，后面加个大写的T(如：RequestT, FooBarT)。
