### Differences between var, let const and when to use them

Before ES6, `var` was the declaration of choice. There are a few issues that were solved with the advent of ES6 that `var` displays.

#### var

- The scope of `var` is global when declared outside of a function delcaration
- Similarly, `var` is scoped to the local function when declared within said function

For example:

```js
  var tester = "hey hi";
    
    function newFunction() {
        var hello = "hello";
    }
    console.log(hello); // error: hello is not defined
```

- variables declared with `var` can be redefined 

```js
var ageValue = 10;
console.log(ageValue); // 10;

var ageValue = 20;
console.log(ageValue); // 20;

```

- `var` is "hoisted", which allows for the variable definition to be interpreted as being defined as `undefined` before it is instantiated elsewhere above its definition. That way, it is held in memory as a *variable*, but its definition isn't assigned until later.

```js
console.log(example); // undefined <-- hoisted
var example = "hello!"
```

##### The Problem with `var`

- If there is a variable declared with `var` in an upper scope, it can accidentally be redefined with the same name in a lower scope unintentionally. For example: 

```js
    var greeter = "hey hi";
    var times = 4;

    if (times > 3) {
        var greeter = "say Hello instead"; 
    }
    
    console.log(greeter) // "say Hello instead"
```

- In the above example, it's clear that we are redefining the variable. However, in larger applications with hundreds or more variable declarations, it could be easy to encounter this redefining behavior unintentionally. 


#### let

- `let` solves the above problem, because `let` is lexically scoped (or scoped within its given "block")
- In the same example above, if we use `let`, the variable definitions are tied only to their individual scopes:

```js
    let greeting = "say Hi";
    if (true) {
        let greeting = "say Hello instead";
        console.log(greeting); // "say Hello instead"
    }
    console.log(greeting); // "say Hi"
```

- Variables declared with `let` can be updated in value, but not re-declared:

```js
let greeting = "say Hi";
let greeting = "say Hello instead"; // error: Identifier 'greeting' has already been declared
```

- Since `let` delcarations can't be defined twice in the same scope, the original problem won't ensue. 
- As with `var`, `let` is hoisted in the same fashion. *However* variables that are hoisted are *not initialized*. for `var`, they are assigned an `undefined` value, but `let`variables are not initalized at all -- so calling upon them before their declaration will result in a `Reference Error`

#### const

- Variables declared with `const` cannot be redefined. 
- Similarly, `const` delcarations cannot be re-declared
- They are also only accessible in their block scope, and so variables of the same name can be declared in different scopes without interacting with each other.
- Objects are a special case with `const`, as objects declared with `const` delcaration cannot be updated outright, but their *properties* can be updated. 

```js
const greeting = {
    message: "say Hi",
    times: 4
}
greeting = {
        words: "Hello",
        number: "five"
    } // error:  Assignment to constant variable.

greeting.message = "say Hello instead";

console.log(greeting); // {message: "say Hello instead", times: 4}

```

- This will update the value of greeting.message without returning errors.
- As with `var` and `let`, `const` is hoisted in the same fashion. *However* variables that are hoisted are *not initialized*. For `var`, they are assigned an `undefined` value, but `let` and `const` variables are not initalized at all -- so calling upon them before their declaration will result in a `Reference Error`

#### Final note on `let` and `const` scoping

- The block scope ensures that, even if a variable is declared with `let` or `const` outisde of the scope of a function, it will not become part of the global object. `var`, alternatively, *does* become part of the global scope.