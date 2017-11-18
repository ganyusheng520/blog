### 前言
> 很多初学者都对函数,实例(对象), 原型之间的关系理不清楚。
    网上五花八门的文章很多，要么不知所云，要么是晦涩难懂。
    本文意在用最简洁的语言跟示例让初学者理清楚这三者之间的关系，无需理会其内部原理
    

### 一张图说明`函数` `实例(对象)` `原型`之间的联系
![GitHub set up](https://user-gold-cdn.xitu.io/2017/11/18/15fcf9018d13add5?w=863&h=597&f=png&s=103660)

> 图片来源:http://www.cnblogs.com/wilber2013/p/4924309.html#_nav_3

**由上图得出结论：**

1. 每个**函数**都有一个prototype属性指向另一个对象，这个对象就叫函数的**原型对象**

2. 由构造函数产生的**实例对象**，其`[[prototype]]`属性(不可见，浏览器通常实现为`__proto__`)指向构造函数的**原型对象**

3. 每个**函数**，都可以认为是通过new Function()实例化的对象

4. 不是通过**构造函数(new XXX())**实例化的对象(**非函数**)，都可以认为是new Object()实例化的对象

5. 基于结论2,3，每个**函数**的`[[prototype]]`(`__proto__`)属性都指向它的**原型对象**Function.prototype

6. 基于结论2,3,4，每个**函数**(基于结论8，除了Object())的**原型对象**的`[[prototype]]`(`__proto__`)属性都指向Object.prototype

7. **原型对象**的constructor属性指向**构造函数**(与1刚好相反)

8. Object.prototype.`__proto__`指向null

### 示例代码：

```
function Person(){}

Person.prototype.name = "Nicholas";
Person.prototype.age = 29;
Person.prototype.job = "Software Engineer";
Person.prototype.sayName = function(){
 console.log(this.name);
};

var person = new Person();
person.sayName(); //"Nicholas"

var person1 = new Person();
person1.sayName(); //"Nicholas"

console.log(person.sayName == person1.sayName); //true      
``` 

### 基于上述定义的示例函数,验证以上结论

1. Person为**构造函数**,其中prototype属性指向它的**原型对象** Person.prototype,
   
   ```
        console.log(Person.prototype)
   ``` 

2. person为new Person()产生的**实例对象**,其`__proto__`属性指向它的**原型** Person.prototype

    ```
        person.__proto__ === Person.prototype   //true
        Person.prototype.isPrototypeOf(person) //true
        Object.getPrototypeOf(person) === Person.prototype //true
    ``` 
3. 结合结论1，定义任意函数，其`__proto__`属性与Function.prototype比较
    
    ```
    function fn () {}
    fn.__proto__ === Function.prototype  //true
    ```
4. 结合结论2,定义任意对象（非 new XXX()实例化对象,非函数),其`__proto__`与 Object.prototype比较
    
    ```
        var obj = {}
        obj.__proto__ === Object.prototype  //true
        
    ```
    
5. 函数Person的`__proto__`属性指向Function.prototype

    ```
        Person.__proto__ === Function.prototype //true
        Object.__proto__ === Function.prototype //true
    ```
6. 原型对象Person.prototype的`__proto__`属性指向Object.prototype

    ```
        Person.prototype.__proto__ === Object.prototype //true
        Function.prototype.__proto__ === Object.prototype //true
    ```
7. Person.prototype的constructor属性与Person比较

    ```
        Person.prototype.constructor === Person     //true
        Function.prototype.constructor === Function  //true
        Object.prototype.constructor === Object     //true
    ```

8. 输出Object.prototype.`__proto__`的值
    
    ```
    console.log(Object.prototype.__proto__)  //null
    ```



#### 简而言之：

对于函数：函数XXX的prototype属性，指向XXX.prototype(函数原型对象)

对于对象：XXX实例化的对象的`[[prototype]]`(也就是`__proto__`)属性,指向XXX.prototype

对于原型：XXX.prototype的constructor属性都指向构造函数XXX


> 更多请参考: JavaScript高级程序设计（第3版）6.2.3 原型模式

