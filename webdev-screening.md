---
layout: default-narrow
title: Web Dev Screening
markdown: redcarpet
permalink: webdev-screening/
---

# Basics

### Get vs Post
* Get for safe actions (data passed in URL), post for secure
* GET for idempotent actions (often cached)
* POST for long requests (GET limited to 2048 char in IE)
* GET for AJAX (POST implemented as two-step process, sending headers first)

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
* `C.prototype` - read-only; the prototype of objects created by `C()`
* `Object.getPrototypeOf(someObj)` - retrieve prototype of someObj
* `someObj.__prototype__` - non-standard mechanism for retrieving the prototype

### Event Bubbling vs Event Capturing
* Determines order events fire.
  * Bubbling: Event on deepest child fires first, then bubbles upwards
  * Capturing: Event fires on highest level element (document), then goes downward.

# Objects
`Object.create`

`Object.getOwnPropertyDescriptor`


