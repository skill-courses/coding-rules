# Git Commit 规范

#### 1.基本格式

**[Name1, Name2] {Type}-{StoryNo}: commit description**
注意：
Type前有空格,冒号后有空格Name1, Name2写pair两人名字有逗号，单人时只写一个

#### 2. 描述

每次提交应当符合单一职责原则，应当是**最小的不可分割的**业务单元，这样有利于部署和维护。所以每次提交的描述就仅仅描述唯一的这一件事情。

#### 3. Type类型

* feat：增加新功能 
* fix: 修改问题
* refactor: 重构