### All methods for strings and their uses

## What are strings?

Strings are a list of characters that are wrapped in quotations, and are typically best used for holding text-like values. 

Strings have a `.length` property that attributes the amount of characters contained within a string.

Strings can be concatenated via the `+` and `+=` operators.

Strings can be created via the `String()` constructor:

```js
let string1 = "this is a string";
let string2 = new String("this is a string");
```

#### String primitives and String Objects

In the above example, both instantiations of the string constructor are similar, but are different implementations of strings. 

String Literals, like in `string1` above, are the typical instantiation of strings. They are created automatically by wrapping a value in single or double quotations, or via coercion through concatenation. Additionally, passing in any value into the `String()` method will also return a string primitive. (for example, `const strPrimitive = String(true)` would become `"true"`)

String Objects, however, are created by instantiating the string constructor. These are not typically used in many circumstances. 

 String objects are treated exactly as objects, but can be converted to its primitive using the `valueOf()` method.

 #### Template Literals

 Other than the two main ways to instantiate a string primitive (single or double quotes), backticks will create a *template literal*, and is the third way to create a string. These types of strings can interpolate expressions. 

 ```js
 let someVariable = 12345;
 let templateLiteral = `This is a template literal ${someVariable} with a number in the middle`

 console.log(templateLiteral); // "This is a template literal 12345 with a number in the middle"
 
 ```

#### String Properties

* `String.prototype.constructor`: The constructor function that created the instance object. 
* `length`: Reflects the `length` of the string. Read-only.

#### String Methods

* `.at()`: Returns the character (one UTF-16 code unit) at the specified `index` provided to the method. 
    * Accepts a negative integer as well, which will count *back from the last string character instead!*
* `.charAt()`: Returns the character (one UTF-16 unit) at the specified `index`
* `.charCodeAt()`: Returns a *number* that is the UTF-16 code unit value of the character at the given `index`
* `.codePointAt()`: Returns a *non negative* Number that is the code point value of the UTF-16 encoded code point starting at the specified `pos`
* `.concat()`: Conbines the text of two (or more) strings and returns the new combined string.
    * Example: `str.concat(' ', str2)` would return the value of str and str2 with a space in the middle. Can take infinite arguments and combine them.
* `.endsWith()`: Returns a true of false whether the string in question contains the argument as the ending of the string. Optionally can provide an `index` for where to check in the string.
* `.includes()`: Performs a *case-sensitive* search to see if the given argument exists in the string, returning `true` or `false`. 
* `.indexOf()`: Returns the first `index` of any occurence of the provided `searchValue` argument. If the value is not present, returns `-1`
