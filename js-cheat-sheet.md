---
layout: default
title: JS Cheat Sheet
group: navigation
markdown: redcarpet
permalink: js-cheat-sheet/
---

<style>
table.js-api .highlight {
  margin: 0;
  border: none;
  padding: 0;
  border-radius: 0px;
  background: none;
}
</style>

<h1 class="page-header">Methods</h1>

### Array
<table class="table table-condensed">
  <tr>
    <td><code>array.concat(items)</code></td>
    <td>Create shallow copy of <code>array</code> with <code>items</code> added to the end.</td>
  </tr>
  <tr>
    <td><code>array.join(separator)</code></td>
    <td></td>
  </tr>
  <tr>
    <td><code>array.pop()</code></td>
    <td></td>
  </tr>
  <tr>
    <td><code>array.push()</code></td>
    <td></td>
  </tr>
  <tr>
    <td><code>array.reverse()</code></td>
    <td></td>
  </tr>
  <tr>
    <td><code>array.shift()</code></td>
    <td></td>
  </tr>
  <tr>
    <td><code>array.unshift(item)</code></td>
    <td></td>
  </tr>
  <tr>
    <td><code>array.slice(start, end)</code></td>
    <td>Shallow copy</td>
  </tr>
  <tr>
    <td><code>array.splice()</code></td>
    <td></td>
  </tr>
  <tr>
    <td><code>array.sort(comparator)</code></td>
    <td>comparator = function(a, b){}</td>
  </tr>
</table>


### Function

<table class="table table-condensed">
  <tr>
    <td><code>function.apply(thisArg, argArray)</code></td>
    <td>Invoke <code>function</code> with <code>thisArg</code> as the receiver</td>
  </tr>
  <tr>
    <td><code>function.bind(thisArg, argArray)</code></td>
    <td>Returns a function that has <code>thisArg</code> as the receiver.</td>
  </tr>
</table>

Implementing Bind
http://jsbin.com/vewapaci/3/edit



### Object

<table class="table table-condensed">
  <tr>
    <td><code>Object.create(proto, propertiesObj)</code></td>
    <td>TODO!</td>
  </tr>
  <tr>
    <td><code>Object.defineProperty(obj, prop, descriptor)</code></td>
    <td>Attaches <code>prop</code> to <code>obj</code> given the property descriptor object</td>
  </tr>
  <tr>
    <td><code>Object.getOwnPropertyDescriptor(obj, name)</code></td>
    <td><code>name</code> is a string</td>
  </tr>
  <tr>
    <td><code>Object.getOwnPropertyNames(obj)</code></td>
    <td></td>
  </tr>
  <tr>
    <td><code>Object.keys()</code></td>
    <td></td>
  </tr>
</table>

#### Inherited from Object.prototype
<table class="table table-condensed">
  <tr>
    <td><code>hasOwnProperty('propName')</code></td>
    <td><code>true</code> if propName is a property</td>
  </tr>
  <tr>
    <td><code>propertyIsEnumerable('propName')</code></td>
    <td></td>
  </tr>
  <tr>
    <td><code>isPrototypeOf()</code></td>
    <td>var person = {...}
    <br />var dev = Object.create(person, { propertyDescriptor });
    <br />person.isPrototypeOf(person) // true</td>
  </tr>
  <tr>
    <td><code>valueOf()</code></td>
    <td></td>
  </tr>
  <tr>
    <td><code>toString()</code></td>
    <td>Used as a fallback when <code>valueOf()</code> returns a reference value</td>
  </tr>
</table>



<h1 class="page-header">{{ page.title }}</h1>

### Arrays

#### Slice

<div class="row">
  <div class="col-md-8">
{% highlight javascript %}
fruits = ['apples', 'oranges', 'banana', 'pear', 'grape'];
basket = fruits.slice(2, 3);
//fruits = [ 'apples', 'oranges', 'banana', 'pear', 'grape' ]
//basket = [ 'banana' ]
{% endhighlight %}
  </div>
  <div class="col-md-4">
    <ul>
      <li><code>(start, end)</code>, exclusive of end</li>
      <li>Creates a shallow <strong>copy</strong></li>
      <li>Leaves <strong>original array unchanged</strong></li>
      <li>Returns an array of copied elements</li>
    </ul>
  </div>
</div>

#### Splice
<div class="row">
  <div class="col-md-8">
{% highlight javascript %}
fruits = ['apples', 'oranges', 'banana', 'pear', 'grape'];
basket = fruits.splice(2, 3);
//fruits = [ 'apples', 'oranges' ]
//basket = [ 'banana', 'pear', 'grape' ]
{% endhighlight %}
  </div>
  <div class="col-md-4">
    <ul>
      <li><code>(start, count)</code></li>
      <li>Removes <code>count</code> number of elements from the array</li>
      <li>Inserts new elements into the original array</li>
      <li>Returns an array of the removed elements (possibly empty)</li>
    </ul>
  </div>
</div>


#### substr


#### substring



### Functions
<div class="row">
  <div class="col-md-3">
  <strong>Function Declaration</strong>
{% highlight javascript %}
foo();    // works
function foo() {
  console.log('hi');
}
foo();    // works
{% endhighlight %}
  </div>
  <div class="col-md-3">
  <strong>Function Expression</strong>
{% highlight javascript %}
foo();    // fails
foo = function() {
  console.log('hi');
}
foo();    // works
{% endhighlight %}
  </div>
  <div class="col-md-6">
  <strong>Named Function Expression</strong>
{% highlight javascript %}
foo();    // TypeError: undefined not a function
bar();    // ReferenceError: bar is not defined
foo = function bar() {
  console.log('hi');
}
foo();    // okay!
bar();    // ReferenceError: bar is not defined
{% endhighlight %}
  </div>
</div>


### Bit Manipulation

<table class="table">
  <tr>
    <td>x &gt;&gt; n</td>
    <td>right shift (by n)</td>
    <td>sign is copied; effectively divide by 2<sup>n</sup></td>
  </tr>
  <tr>
    <td>x &gt;&gt;&gt; 0</td>
    <td>right-shift (by 0) without sign extension</td>
    <td>  </td>
  </tr>
  <tr>
    <td>~~x</td>
    <td>double bit-wise not</td>
    <td>parseInt(x, 10), or Math.floor(x)</td>
  </tr>
  <tr>
    <td><code>!!~array.indexOf(...)</code></td>
    <td></td>
    <td>Fancy way of:<br />
    if (array.indexOf(...) >= 0)
    </td>
  </tr>
</table>











<h1 class="page-header">Checks</h1>

<div class="row">
  <div class="col-md-6">
  {% highlight javascript %}
typeof 1                // "number"
typeof '1'              // "string"
typeof true             // "boolean"
typeof undefined        // "undefined"
typeof null             // "object"
typeof {}               // "object"
typeof function(){}     // "function"
  {% endhighlight %}
  </div>
  <div class="col-md-6">
    Checks for:
    <ul>
      <li>Number</li>
      <li>String</li>
      <li>Boolean</li>
      <li>Object</li>
      <li>Function</li>
    </ul>
    Returns <code>function</code> if an object has a <code>[[Call]]</code> internal property.
  </div>
</div>


<div class="row">
  <div class="col-md-6">
  {% highlight javascript %}someArray = [...];

// ES5
Array.isArray(someArray);

// Polyfill
if(!Array.isArray) {
  Array.isArray = function(arg) {
    return Object.prototype.toString.call(arg) === '[object Array]';
  };
}
  {% endhighlight %}
  </div>
  <div class="col-md-6">
    When you call <code>toString</code> on an object, you get <code>[object Cnstrctr]</code>
  </div>
</div>

<div class="row">
  <div class="col-md-6">
  {% highlight javascript %}obj.prop !== undefined
obj.hasOwnProperty('prop')
'prop' in obj
  {% endhighlight %}
  </div>
  <div class="col-md-6">
    Checking for properties
  </div>
</div>









<h1 class="page-header">Object Internals</h1>

<div class="row">
  <div class="col-md-6">
    <h4>Internal Methods</h4>
    <table class="table table-condensed">
      <tbody>
        <tr>
          <th><code>[[Put]]</code></th>
          <td>Method: Add an <em>own</em> property to an object</td>
        </tr>
        <tr>
          <th><code>[[Set]]</code></th>
          <td>Method: Modify a property already on an object</td>
        </tr>
        <tr>
          <th><code>[[Delete]]</code></th>
          <td>Method: remove a property. Called by <code>delete</code> operator.</td>
        </tr>
      </tbody>
    </table>
  </div>
  <div class="col-md-6">
    <h4>Methods Inherited from Object.prototype</h4>
    <table class="table table-condensed">
      <tbody>
        <tr>
          <th><code>hasOwnProperty()</code></th>
          <td>Determine if <em>own</em> property exists with given name</td>
        </tr>
        <tr>
          <th><code>propertyIsEnumerable()</code></th>
          <td>Determine if property is enumerable (has enumerable attribute = true)</td>
        </tr>
        <tr>
          <th><code>isPrototypeOf()</code></th>
          <td>Determine if object is prototype of another</td>
        </tr>
        <tr>
          <th><code>valueOf()</code></th>
          <td>Called when operator is used on an object</td>
        </tr>
        <tr>
          <th><code>toString()</code></th>
          <td>Called when <code>valueOf()</code> returns a reference value instead of primitive.</td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

* All properties added to an object are *enumerable* by default
  * Iterable with a `for-in` loop
  * Has an internal `[[Enumerable]]` attribute set to true


#### Types of Properties

<div class="row">
  <div class="col-md-12">
    <table class="table table-condensed">
      <tbody>
        <tr>
          <th>Property Attribute</th>
          <th>Data Properties</th>
          <th>Accessor Properties</th>
        </tr>
        <tr>
          <td><code>[[Value]]</code></td>
          <td>Automatically filled, even functions</td>
          <td>N/A</td>
        </tr>
        <tr>
          <td><code>[[Enumerable]]</code><br />Counted by Object.keys()</td>
          <td><code>true</code></td>
          <td></td>
        </tr>
        <tr>
          <td><code>[[Configurable]]</code><br />Can remove with delete, or update config</td>
          <td><code>true</code></td>
          <td></td>
        </tr>
        <tr>
          <td><code>[[Writable]]</code></td>
          <td><code>true</code><br />Throw an error if attempt to change a nonwritable prop</td>
          <td>N/A</td>
        </tr>
        <tr>
          <td><code>[[Get]]</code></td>
          <td>N/A</td>
          <td></td>
        </tr>
        <tr>
          <td><code>[[Set]]</code></td>
          <td>N/A</td>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

#### Preventing Object Modification

<div class="row">
  <div class="col-md-4">
    <h5>Prevent Extension</h5>
    <p>Cannot add properties</p>
    {% highlight javascript %}
Object.isExtensible(obj);
Object.preventExtensions(obj);{% endhighlight %}
  </div>
  <div class="col-md-4">
    <h5>Seal</h5>
    <p>Cannot add properties</p>
    <p>Cannot remove properties</p>
    <p>Cannot change property type (data &hArr; accessor)</p>
{% highlight javascript %}
Object.isSealed(obj);
Object.seal(obj);{% endhighlight %}
  </div>
  <div class="col-md-4">
    <h5>Freeze</h5>
    <p>Cannot add properties</p>
    <p>Cannot remove properties</p>
    <p>Cannot change property type (data &hArr; accessor)</p>
    <p>Cannot write to data property</p>
    {% highlight javascript %}
Object.isFrozen(obj);
Object.freeze(obj);{% endhighlight %}
  </div>
</div>

#### Defining an Accessor Property via Object Literal

{% highlight javascript %}
var person1 = {
  _name: "Nicholas",

  get name() {        // ES5
    // ...
  }
}{% endhighlight %}



<h1 class="page-header">Object Patterns</h1>

<h3>Singleton</h3>

{% highlight javascript %}var MySingleton = (function(){
  // store reference to instance
  var instance;
  
  function init(){
    // private variables
    return {

    }
  }

  // Singleton Return Object: A single accessor getInstance()
  return {
    getInstance: function(){
      if (!instance) {
        instance = init();
      }
      return instance;
    }
  }
})();{% endhighlight %}


<h3>Factory</h3>

<div class="row">
  <div class="col-md-6">
  {% highlight javascript %}
function createPerson(name, age) {
  var o = new Object();
  o.name = name;
  o.age = age;
  return o;
}{% endhighlight %}
  </div>
  <div class="col-md-6">
    Call a method that creates an object then returns it.
  </div>
</div>

### Constructor Pattern

<div class="row">
  <div class="col-md-6">
  {% highlight javascript %}
function Person(name, age) {
  this.name = name;
  this.age = age;
}{% endhighlight %}
  </div>
  <div class="col-md-6">
    <ul>
      <li>Methods are created for each instance.</li>
      <li>Get around this by pointing method to externally defined function, or attaching to prototype.</li>
    </ul>
  </div>
</div>

<div class="row">
  <div class="col-md-6">
  {% highlight javascript %}new Person('Tuan', 32);{% endhighlight %}
  </div>
  <div class="col-md-6">
    Use a function as a constructor with the <code>new</code> operator.
    <ul>
      <li><code>prototype</code> property gets added.</li>
      <li>Each instance gets a <code>[[Prototype]]</code> property, <code>__proto__</code>.</li>
    </ul>
  </div>
</div>

## Prototypical Inheritance

<div class="row">
  <div class="col-md-6">
  {% highlight javascript %}Person.prototype.sayName = function() {
  console.log(this.name);
}{% endhighlight %}
  </div>
  <div class="col-md-6">
    <ul>
      <li>Methods can be attached to prototype as properties.</li>
    </ul>
  </div>
</div>

<div class="row">
  <div class="col-md-6">
  {% highlight javascript %}Person.prototype = {
  sayName: function(){},
  constuctor: Person
}

person.constructor === Person; // true{% endhighlight %}
  </div>
  <div class="col-md-6">
    <ul>
      <li>Can also be defined via object literal notation</li>
      <li>Be sure to specify <strong>constructor</strong> property!!</li>
    </ul>
  </div>
</div>















## Modular Design Patterns

<div class="row">
  <div class="col-md-6">
    <h4>AMD</h4>
{% highlight javascript %}
define(function(require){
  var lib = require( "package/lib" );

  // behaviour for our module
  function foo(){
    lib.log( "hello world!" );
  }

  // export (expose) foo for other modules
  return {
    foobar: foo
  };
});

// -- Consuming the module
require(["foobar", "baz"], function ( foobar, baz ) {
  // rest of your code here
  foobar.doSomething();
});
{% endhighlight %}
<ul>
  <li>Browser-first approach to development</li>
  <li>Asychronous</li>
  <li>Require.js</li>
</ul>
  </div>
  <div class="col-md-6">
    <h4>CommonJS: require() and exports</h4>
{% highlight javascript %}
// -- foobar.js ------------------
var lib = require( "package/lib" );
 
// behaviour for our module
function foo(){
  lib.log( "hello world!" );
}

// export (expose) foo to other modules
exports.foo = foo;




// -- Consuming the module -------
var foobar = require("./foobar.js").foobar,
    test   = new foobar();

 
{% endhighlight %}
<ul>
  <li>Server-first approach to development</li>
  <li>File I/O</li>
  <li>CommonJS, Node</li>
</ul>
  </div>
</div>








