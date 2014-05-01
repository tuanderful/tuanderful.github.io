---
layout: default
title: Web Dev Screening
group: navigation
markdown: redcarpet
permalink: webdev-screening/
---

# JS

### What is a Closure?
* When a function is able to remember an access its lexical scope even when that function is executing outside its lexical scope.

### Lexical Scope
* Scope that is defined at lexing time, step 1 of compilation process.

### Cheat Lexical Scope
* `eval` modify the existing lexical scope
  * When in strict, it creates and modifies its own scope, not impacting enclosing scope
* `with`
  * LHS lookup: can create variable in global scope
  * Normal `var` declaration will be scoped to the containing function

### Compilation Process
* Lexing/Tokenizing - *break up string of characters, turn into tokens*
* Parsing - *take stream of tokens, turn into AST, or Abstract Syntax Tree*
* Code generation - *Turn an AST into executable code*

### LHS/RHS Assignment
* LHS tries to find the variable container, so it can assign (value on RHS)
  * If not found, it is created. Since lookup goes up to global scope, variable is created in global scope.
  * If not found in strict mode, will throw `ReferenceError`
* RHS is just a variable lookup. Will throw `ReferenceError` if variable doesn't exist.

### Prototype
* `C.prototype`
* `Object.getPrototypeOf(someObj)`
* `someObj.__prototype__`

# Objects
`Object.create`

`Object.getOwnPropertyDescriptor`




