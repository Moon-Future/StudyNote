# 对象
1、数字的字面值（literal）不能当作对象使用。这是因为 JavaScript 解析器的一个错误， 它试图将点操作符解析为浮点数字面值的一部分。
```js
2.toString(); // 出错：SyntaxError
```