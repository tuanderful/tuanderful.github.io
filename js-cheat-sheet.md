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

.js-api td:nth-child(3) {
  width: 350px;
}
.js-api td:nth-child(2) {
}
.js-api td:nth-child(1) {
  width: 550px;
}
</style>

<h1 class="page-header">{{ page.title }}</h1>
<p class="lead">
  Prepare for your interview, or just brush up on your JavaScript basics.
</p>

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
      <li><code>(start, count)</code>
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

### Document Object Model
#### Document Type
<div class="row">
  <div class="col-md-12">
    <h5>Properties</h5>
    <table class="table table-condensed js-api">
      <tr>
        <td>{% highlight javascript %}document.anchors{% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}document.applets{% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}document.forms{% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}document.images{% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}document.links{% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}document.readyState == 'loading'{% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}document.readyState == 'interactive'{% endhighlight %}</td>
        <td>DOMContentLoaded</td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}document.readyState == 'complete'{% endhighlight %}</td>
        <td>sub-resources loaded</td>
        <td></td>
      </tr>
    </table>
  
    <h5>Methods</h5>
    <table class="table table-condensed js-api">
      <tr>
        <td>{% highlight javascript %}document.getElementById(){% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}document.getElementsByTagName(){% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}document.getElementsByClassName(){% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}document.querySelector('.some.selector'){% endhighlight %}</td>
        <td>{% highlight javascript %}$('.some.selector')[0];{% endhighlight %}</td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}document.querySelectorAll('.some.selector'){% endhighlight %}</td>
        <td>Returns array of 0 or more matched elements</td>
        <td>{% highlight javascript %}$('.some.selector');{% endhighlight %}</td>
      </tr>
      <tr>
        <td>{% highlight javascript %}document.createElement(){% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}document.createDocumentFragment(){% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
    </table>
  </div>
</div>

#### Element Type
<div class="row">
  <div class="col-md-12">
    <h5>Properties</h5>
    <table class="table table-condensed js-api">
      <tr>
        <td>{% highlight javascript %}element.childElementCount{% endhighlight %}</td>
        <td>Number of children</td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}element.firstElementChild{% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}element.lastElementChild{% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}element.previousElementSibling{% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}element.nextElementSibling{% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}element.className{% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}element.classList{% endhighlight %}</td>
        <td>
        {% highlight javascript %}add(){% endhighlight %},
        {% highlight javascript %}remove(){% endhighlight %},
        {% highlight javascript %}contains(){% endhighlight %},
        {% highlight javascript %}toggle(){% endhighlight %}
        </td>
        <td></td>
      </tr>
    </table>

    <h5>Methods</h5>
    <table class="table table-condensed js-api">
      <tr>
        <td>{% highlight javascript %}element.getElementById(){% endhighlight %}</td>
        <td>$('#...')</td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}element.getElementByTagName(){% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}element.querySelector(){% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}element.createElement(){% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>{% highlight javascript %}element.createDocumentFragment(){% endhighlight %}</td>
        <td></td>
        <td></td>
      </tr>
    </table>
  </div>
</div>

### AJAX
<div class="row">
  <div class="col-md-6">
    <h5>jQuery</h5>
{% highlight javascript %}
$.ajax({
  type: 'GET',
  url: '/my/url',
  success: function(resp) {

  },
  error: function() {

  }
});
{% endhighlight %}
  </div>
  <div class="col-md-6">
    <h5>IE9+</h5>
{% highlight javascript %}
request = new XMLHttpRequest();
request.open('get', '/my/url', true);

request.onload = function() {
  if (request.status >= 200 && request.status < 400) {
    resp = request.responseText;
  } else {
    // target server reached, error returned
  }
}

request.error = function() {
  // connection error
}

request.send();
{% endhighlight %}
  </div>
</div>


### Object Internals

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
          <td>Determine if property is enumerable</td>
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
  <div class="col-md-6">
    <h5>Data Properties</h5>
    
  </div>
  <div class="col-md-6">
    <h5>Accessor Properties</h5>
    
  </div>

  <div class="col-md-12">
    <table class="table table-condensed">
      <tbody>
        <tr>
          <th></th>
          <th>Data Properties</th>
          <th>Accessor Properties</th>
          <th>Sealed</th>
          <th>Frozen</th>
        </tr>
        <tr>
          <th><code>[[Value]]</code></th>
          <td>Automatically filled, even functions</td>
          <td>N/A</td>
          <td></td>
          <td></td>
        </tr>
        <tr>
          <th><code>[[Enumerable]]</code></th>
          <td><code>true</code></td>
          <td></td>
          <td></td>
          <td></td>
        </tr>
        <tr>
          <th><code>[[Configurable]]</code></th>
          <td><code>true</code></td>
          <td></td>
          <td></td>
          <td></td>
        </tr>
        <tr>
          <th><code>[[Writable]]</code></th>
          <td><code>true</code><br />Throw an error if attempt to change a nonwritable prop</td>
          <td>N/A</td>
          <td></td>
          <td></td>
        </tr>
        <tr>
          <th><code>[[Get]]</code></th>
          <td>N/A</td>
          <td></td>
          <td></td>
          <td></td>
        </tr>
        <tr>
          <th><code>[[Set]]</code></th>
          <td>N/A</td>
          <td></td>
          <td></td>
          <td></td>
        </tr>
      </tbody>
    </table>
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




### Patterns

#### Modular Design Patterns

<div class="row">
  <div class="col-md-6">
    <h5>AMD</h5>
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
    <h5>CommonJS: require() and exports</h5>
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


