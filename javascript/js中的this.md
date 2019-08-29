# JavaScript 中的 this (面试总是考，附面试中的一道题)
>
## 概述  
>
面向对象语言中，this表示当前对象的一个引用。Js中this是随着**执行环境**而变化的  
>
1. 在方法中，this为该方法所属对象。  
2. 单独使用this表示全局对象window（严格模式也是）。  
3. 在函数中，this表示全局对象。  
4. 在函数中，严格模式，this是未定义的（undefined）。  
5. 在事件中，this表示接受时间的元素。  
6. 可以使用call（）和replay（）将this引用到任何对象。
>
## 样例  
>
  ```javascript
  var person = {
    firstName: "John",
    lastName : "Doe",
    id       : 5566,
    fullName : function() {
      return this.firstName + " " + this.lastName;
    }
  };
  ```
>
## 详细说明
>
### 1.方法中的this表示所属对象
>
  ```javascript
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
  ```
>
上述person对象中的，fullName方法中的this表示person。
>
### 2.单独使用
>
  ```javascript
  var x = this;
  ```
>
无论是否使用严格模式`"use strict";`this指向全局对象即[object Window]。
>
### 3.函数中的this
>
#### 默认
>
  ```javascript
  function myFunction() {
    return this;
  }
  ```
>
this此时表示为全局对象Window
>
#### 严格模式
>
  ```javascript
  "use strict";
  function myFunction() {
    return this;
  }
  ```
>
this此时是undefined
>
### 4.事件中的this
>
  ```html
  <button onclick="this.style.display='none'">
  </button>
  ```
 >
在 HTML 事件句柄中，this 指向了接收事件的 HTML 元素
>
### 5.显示函数绑定call（）
>
  ```javascript
  var person1 = {
    fullName: function() {
      return this.firstName + " " + this.lastName;
    }
  }
  var person2 = {
    firstName:"John",
    lastName: "Doe",
  }
  person1.fullName.call(person2);  // 返回 "John Doe"
  ```
>
在 JavaScript 中函数也是对象，对象则有方法，apply 和 call 就是函数对象的方法。这两个方法异强大，他们允许切换函数执行的上下文环境（context），即 this 绑定的对象。  
在下面实例中，当我们使用 person2 作为参数来调用 person1.fullName 方法时, this 将指person2, 即便它是 person1 的方法。  
>
### 面试真题
>
#### 第一题
>
  ```javascript
  var name = "A"; 
  var person = {
    name: "kang",
    pro: {
      name: "B",
      getName: function() {
        return this.name;
      }
    }
  };
  console.log(person.pro.getName()); // B
  var pepole = person.pro.getName;
  console.log(pepole()); // A
  ```
>
#### 第二题
>
这道题具体到了this表示谁
>
  ```javascript
  var name = "A";
  var person = {
    name: "kang",
    pro: {
      name: "B",
      getName: function() {
        console.log(this);
        return this.name;
      }
    }
  };
  console.log(person.pro.getName()); // Object { name: "...", getName: () }, B
  var pepole = person.pro.getName;
  console.log(pepole()); // Window, A
  ```
>
如果这道题使用严格模式，people中的this表示undefined。  
>