# 对象
1、数字的字面值（literal）不能当作对象使用。这是因为 JavaScript 解析器的一个错误， 它试图将点操作符解析为浮点数字面值的一部分。
```
2.toString(); // 出错：SyntaxError
```
有很多变通方法可以让数字的字面值看起来像对象。
```
2..toString(); // 第二个点号可以正常解析
2 .toString(); // 注意点号前面的空格
(2).toString(); // 2先被计算
```

# 作用域（程序源代码中定义变量的区域）
静态作用域与动态作用域 
- 静态作用于（词法作用域）：函数的作用域在函数定义的时候就决定了
- 动态作用于：函数的作用域在函数调用的时候才决定
- JavaScript 采用词法作用域(lexical scoping)，也就是静态作用域。

# 执行上下文（execution context）：
对于每个执行上下文，都有三个重要属性：
- 变量对象(Variabel object, VO)
- 作用域链(Scope chain)
- this


# JSON
'{"prop": "val"}' 是个合法的JSON, 但'{prop: "val"}'和"{'prop': 'val'}"都是不合法的,
所有属性名称和它的值都必须用双引号引住，不能使用单引号
