# CSS 编码规范

##### 1. 缩进与换行

- 使用 2 个空格做为一个缩进层级，不允许使用 4 个空格 或 tab 字符；

- **选择器** 与 { 之间必须包含空格；

- **属性名** 与之后的 : 之间不允许包含空格， : 与 **属性值** 之间必须包含空格；

- **列表型属性值** 书写在单行时，**,** 后必须跟一个空格；

  ```css
  font-family: Arail, sans-serif;
  ```

- 每行不得超过 120 个字符，除非单行不可分割；

##### 2. 选择器

* 当一个 rule 包含多个 selector 时，每个选择器声明必须独占一行；

  ```css
  .post,
  .page,
  .comment {
    font-size: 10px;
  }
  ```

* \>、+、~ 选择器的两边各保留一个空格；

  ```css
  main > nav {
    padding: 10px;
  }
  ```

* 选择器的嵌套层级应不大于 3 级，位置靠后的限定条件应尽可能精确；

##### 3. 属性

* 属性定义必须另起一行；

  ```css
  /* Bad */
  .selector {padding:10px; marging:10px;}
  
  /* Good */
  .selector {
    padding: 10px;
    marging:10px;
  }
  ```

* 属性定义后必须以分号结尾，不要省掉分号；

* 同一 rule set 下的属性在书写时，应按功能进行分组，并以 Formatting Model（布局方式、位置） > Box Model（尺寸） > Typographic（文本相关） > Visual（视觉效果） 的顺序书写，分组之间应该换行，以提高代码的可读性；

  ```css
  .sidebar {
    /* Formatting Model: position, offset, top, left, display... */
    position: absolute;
    top: 50px;
    left: 0;
    
    /* Box Model: size, padding, marging, boarders... */
    margin: 10px;
    padding: 10px;
  
    /* Typographic: font, aligns, text styles... */
    font-size: 10px;
    line-height: 10px;
    
    /* Visual: colors, shadows... */
    background-color: black;
    color: red;
    transtion: color ls;
  }
  ```

##### 4. **值与单位**

- 长度为 0 时需省略单位

- 文本内容必须用双引号包围

- 颜色值中的英文字符采用小写。如不用小写也需要保证同一项目内保持大小写一致。

