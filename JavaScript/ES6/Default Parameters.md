_from freeCodeCamp_

In order to help us create more flexible functions, ES6 introduces default parameters for functions.
```
function greeting(name = "Anonymous") {
  return "Hello " + name;
}
console.log(greeting("John")); // Hello John
console.log(greeting()); // Hello Anonymous
```
The default parameter kicks in when the argument is not specified (it is undefined). As you can see in the example above, the parameter 
name will receive its default value "Anonymous" when you do not provide a value for the parameter. You can add default values for as many 
parameters as you want.
