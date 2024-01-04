### What does truth and falsely mean (and when does something evaluate to each)

Booleans in JavaScript, like `true` and `false`, are utilized liberally in JavaScript coding. However, some values and types can be considered equivalent to these booleans even if their value is not that data type. 

For this reason, there are values and JavaScript types that can be *truthy* or *falsy* which means that they *emulate* those sorts of values under certain circumstances, like a ternary operator or branching statement. 

#### truthy

There are a few different values that can be considered *truthy* in JavaScript.

- `true` bool
- Any numbers other than `0`
- Any string other than an empty string `""`
- Any object (except the built-in `document.all`)
- Any function

#### falsy

- `false` bool
- The integer `0`, `-0`, and `0n`
- Empty strings, `""` and `''`
- `null`
- `undefined`
- `NaN`
- `document.all`

#### The importance of this distinction

While using truthy and falsy values to determine branches, certain issues can occur. For instance, 