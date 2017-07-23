# Explicit Binding (JavaScript)

## Function.prototype.call() 

The `call()` method calls a function with a given `this` value and arguments 
provided _individually_.

```
var sayName = function (food1, food2, food3) {
  console.log("My name is " + this.name + " and I like to eat " + food1 + ", " + food2 + " and " + food3);
}

var justin = {
  name: "Justin",
  age: 35
}

var food = ["pizza", "cheeseburgers", "Takis"];

sayName.call(justin, food[0], food[1], food[2]);

// "My name is Justin and I like to eat pizza, cheeseburgers and Takis" 
```

[JSBin](http://jsbin.com/mufadupefa/edit?js,console) 
[Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call)

## Function.prototype.apply()

The `apply()` method calls a function with a given `this` value and arguments 
provided in an _array_.

```
  ...

sayName.apply(justin, food);

// "My name is Justin and I like to eat pizza, cheeseburgers and Takis" 
```

[JSBin](http://jsbin.com/wazefecisu/1/edit?js,console) 
[Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply)

## Function.prototype.bind()

`bind()` is very similar to `call()` but it returns a new function.

```
  ...

var newFunc = sayName.bind(justin, food[0], food[1], food[2]);

newFunc();

// "My name is Justin and I like to eat pizza, cheeseburgers and Takis" 
```

[JSBin](http://jsbin.com/dopihajobi/1/edit?js,console) 
[Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)
