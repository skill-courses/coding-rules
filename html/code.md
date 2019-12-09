# HTML 编码规范

##### 1. DOCTYPE

HTML文件必须加上 DOCTYPE 声明，并统一使用 HTML5 的文档声明:

```html
<!DOCTYPE html>
```

##### 2. 编码格式

一般情况下统一使用 “UTF-8” 编码：

```html
<meta charset="UTF-8">
```

##### 3. 缩进与换行

* 使用 2 个空格做为一个缩进层级，不允许使用 4 个空格 或 tab 字符；

  ```html
  <body>
    <header></header>
    <article></article>
    <footer></footer>
  </body>
  ```

* 每行不得超过 120 个字符：过长的代码不容易阅读与维护。但是考虑到 HTML 的特殊性，所以不做硬性要求。

* 每个块状元素独立一行，内联元素可以根据上一条规则来判断。

  ```html
  <!-- Good -->
  <div>
    <h1></h1>
    <p></p>
  </div>	
  <p><span></span><span></span></p>
  
  <!-- Bad -->
  <div>
    <h1></h1><p></p>
  </div>	
  <p> 
    <span></span>
    <span></span>
  </p>
  ```

##### 4. 命令规范

* 元素的id和name属性的命令用小驼峰法或。

* 元素 id 必须保证页面唯一。

* class的命令与css命令规范保持一致

  ```html
  <div id="articleInfo" name="articleInfo" class="article-info">
  </div
  ```

##### . 标签规范

* 标签名必须使用小写字母；

* 对 HTML5 中规定允许省略的闭合标签，不允许省略闭合标签；

  ```html
  <!-- Bad -->
  <ul>
    <li>first
    <li>second
  </ul>
  
  <!-- Good -->
  <ul>
    <li>first</li>
    <li>second</li>
  </ul>
  ```

* tbody 必须置于 table 中

* div 不要嵌套在 p 中 

* 标签的使用应尽量简洁，减少不必要的标签，避免标签嵌套太深

  ```html
  <span>
    <img src="./logo.png" alt="logo">
  </span>
  ```

* img标签要有alt属性