---
layout: default
title: JS Cheat Sheet
group: navigation
markdown: redcarpet
permalink: js-cheat-sheet/
---


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
  <div class="col-md-6">
    <h5>Properties</h5>
    <table>
      <tr><td><code>document.anchors</code></td><td></td></tr>
      <tr><td><code>document.applets</code></td><td></td></tr>
      <tr><td><code>document.forms</code></td><td></td></tr>
      <tr><td><code>document.images</code></td><td></td></tr>
      <tr><td><code>document.links</code></td><td></td></tr>
      <tr><td><code>document.readyState</code></td><td><code>loading</code><code>complete</code></td></tr>
    </table>
  </div>
  <div class="col-md-6">
    <h5>Methods</h5>
    <table>
      <tr><td><code>document.getElementById()</code></td><td></td></tr>
      <tr><td><code>document.getElementsByTagName()</code></td><td></td></tr>
      <tr><td><code>document.getElementsByClassName()</code></td><td></td></tr>
      <tr><td><code>document.querySelector()</code></td><td></td></tr>
      <tr><td><code>document.createElement()</code></td><td></td></tr>
      <tr><td><code>document.createDocumentFragment()</code></td><td></td></tr>
    </table>
  </div>
</div>

#### Element Type
<div class="row">
  <div class="col-md-6">
    <h5>Properties</h5>
    <table>
      <tr><td><code>element.childElementCount</code></td><td></td></tr>
      <tr><td><code>element.firstElementChild</code></td><td></td></tr>
      <tr><td><code>element.lastElementChild</code></td><td></td></tr>
      <tr><td><code>element.previousElementSibling</code></td><td></td></tr>
      <tr><td><code>element.nextElementSibling</code></td><td></td></tr>
      <tr><td><code>element.className</code></td><td></td></tr>
      <tr><td><code>element.classList</code></td><td>
        <code>add()</code>,
        <code>remove()</code>,
        <code>contains()</code>,
        <code>toggle()</code>
      </td></tr>
    </table>
  </div>
  <div class="col-md-6">
    <h5>Methods</h5>
    <table>
      <tr><td><code>element.getElementById()</code></td><td></td></tr>
      <tr><td><code>element.getElementByTagName()</code></td><td></td></tr>
      <tr><td><code>element.querySelector()</code></td><td></td></tr>
      <tr><td><code>element.createElement()</code></td><td></td></tr>
      <tr><td><code>element.createDocumentFragment()</code></td><td></td></tr>
    </table>
  </div>
</div>
