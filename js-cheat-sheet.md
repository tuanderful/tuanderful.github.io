---
layout: default
title: JS Cheat Sheet
group: navigation
markdown: redcarpet
permalink: /
---

<div class="span9" role="main">
  <div id="home">
    <h1 class="page-header">JS Cheat Sheet</h1>
    <p class="lead">
      Prepare for your interview, or just brush up on your JavaScript basics.
    </p>

    <h3>Arrays</h3>

    <h4>Slice</h4>
    <div class="row">
      <div class="span5">
{% highlight javascript %}
fruits = ['apples', 'oranges', 'banana', 'pear', 'grape'];
basket = fruits.slice(2, 3);
//fruits = [ 'apples', 'oranges', 'banana', 'pear', 'grape' ]
//basket = [ 'banana' ]
{% endhighlight %}
      </div>
      <div class="span4">
        <ul>
          <li>Creates a shallow <strong>copy</strong></li>
          <li>Leaves <strong>original array unchanged</strong></li>
          <li>Returns an array of copied elements</li>
        </ul>
      </div>
    </div>

    <h4>Splice</h4>
    <div class="row">
      <div class="span5">
{% highlight javascript %}
fruits = ['apples', 'oranges', 'banana', 'pear', 'grape'];
basket = fruits.splice(2, 3);
//fruits = [ 'apples', 'oranges' ]
//basket = [ 'banana', 'pear', 'grape' ]
{% endhighlight %}
      </div>
      <div class="span4">
        <ul>
          <li>Removes <code>count</code> number of elements from the array</li>
          <li>Inserts new elements into the original array</li>
          <li>Returns an array of the removed elements (possibly empty)</li>
        </ul>
      </div>
    </div>


    <h3>Document Object Model</h3>
    <h4>Document Type</h4>
    <div class="row">
      <div class="span5">
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
      <div class="span4">
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

    <h4>Element Type</h4>
    <div class="row">
      <div class="span5">
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
      <div class="span4">
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



  </div>
</div>

<div class="span3">
  sidebar nav
</div>