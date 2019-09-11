_from freeCodeCamp & hackerrank_
(https://blog.csdn.net/weixin_33889665/article/details/91455882)

# Arrow Functions

These expressions lexically bind the `this` value while using less syntax than a typical function expression. Arrow functions are always _anonymous_.

ES6 provides us with the syntactic sugar of anonymous functions: **arrow function syntax**
```
const myFunc = () => {
  const myVar = "value";
  return myVar;
}
```
When there is no function body, and only a return value, arrow function syntax allows you to omit the keyword return as well as the brackets surrounding the code. This helps simplify smaller functions into one-line statements:
```
const myFunc = () => "value"
```
1. Arrow functions work really well with higher order functions, such as map(), filter(), and reduce(), that take other functions as arguments for processing collections of data.

Read the following code:
```
FBPosts.filter(function(post) {
  return post.thumbnail !== null && post.shares > 100 && post.likes > 500;
})
```
We have written this with filter() to at least make it somewhat readable. Now compare it to the following code which uses arrow function syntax instead:
```
FBPosts.filter((post) => post.thumbnail !== null && post.shares > 100 && post.likes > 500)
```
This code is more succinct and accomplishes the same task with fewer lines of code.

## This
JS 中 this 的指向问题一直都是面试高频考点，总结起来就是一句话：“ this 永远指向调用它的那个对象 (object)”，而箭头函数则改写了这一规则，就是`箭头函数共享当前代码上下文的 this`. 
* 箭头函数不会创建自己的 `this`，它只会从自己的作用域链的上一层继承 `this`，如果上一层还是箭头函数，则继续向上查找，直至全局作用域，在浏览器环境下即 _window_。
* 函数具有作用域链，对象则不具有

箭头函数还有以下特点:
* 由于箭头函数没有自己的 this 指针，通过 call 或 apply 调用，第一个参数会被忽略
* 不绑定 Arguments 对象，其引用上一层作用域链的 Arguments 对象
* 不能用作构造器，和 new 一起用会抛出错误。
* 没有 prototype 属性。

现在你应该明白为何 React 中的函数写法都为箭头函数，就是为了绑定 this

```
const goat = {
  dietType: 'herbivore',
  makeSound() {
    console.log('baaa');
  },
  diet: () => {
    console.log(this.dietType);
  }
};

goat.diet(); // Prints undefined
```
The key takeaway from the example above is to _**avoid**_ using arrow functions when using `this` in a method!


