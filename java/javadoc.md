# Javadoc

### 1. 格式

- 一般形式

    Javadoc块的基本格式如下所示：
    ```
        /**
         * Multiple lines of Javadoc text are written here,
         * wrapped normally...
         */
        public int method(String p1) { ... }
    ```

    或者是以下单行形式：
    ```
      /** An especially short bit of Javadoc. */
    ```
  
    基本格式总是OK的。当整个Javadoc块能容纳于一行时(且没有Javadoc标记@XXX)，可以使用单行形式。
- 段落

    空行(即，只包含最左侧星号的行)会出现在段落之间和Javadoc标记(@XXX)之前(如果有的话)。 
    除了第一个段落，每个段落第一个单词前都有标签<p>，并且它和第一个单词间没有空格。
    
- Javadoc标记

    标准的Javadoc标记按以下顺序出现：@param, @return, @throws, @deprecated, 前面这4种标记如果出现，
    描述都不能为空。 当描述无法在一行中容纳，连续行需要至少再缩进8个空格。
    
### 2. 摘要片段

每个类或成员的Javadoc以一个简短的摘要片段开始。这个片段是非常重要的，在某些情况下，它是唯一出现的文本，比如在类和方法索引中。

这只是一个小片段，可以是一个名词短语或动词短语，但不是一个完整的句子。它不会以`A {@code Foo} is a...`或`This method returns...`开头, 
它也不会是一个完整的祈使句，如`Save the record...`。然而，由于开头大写及被加了标点，它看起来就像是个完整的句子。
  
### 3. 使用时机

至少在每个public类及它的每个public和protected成员处使用Javadoc。

以下是一些例外：
- 不言自明的方法

    对于简单明显的方法如getFoo，Javadoc是可选的(即，是可以不写的)。这种情况下除了写“Returns the foo”，确实也没有什么值得写了。
    
- 重写

    如果一个方法重写了超类中的方法，那么Javadoc并非必需的。
    
- 其它

    对于包外不可见的类和方法，如有需要，也是要使用Javadoc的。如果一个注释是用来定义一个类，方法，字段的整体目的或行为， 
    那么这个注释应该写成Javadoc，这样更统一更友好。
