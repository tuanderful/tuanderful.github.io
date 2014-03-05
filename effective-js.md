---
layout: default
title: Effective JS
group: navigation
markdown: redcarpet
permalink: effective-js/
---

<style>
ul {
  padding: 0 40px;
}
</style>

<div class="col-md-8 col-md-offset-2" role="main">
  <div id="home">
    <h1 class="page-header">{{ page.title }}</h1>

    <h3>Accustoming Yourself to JavaScript</h3>
    <h4>1. Know Which JavaScript You Are Using</h4>
    <ul>
      <li>Strict Mode only works the <code>"use strict";</code> is included at the top of a function or the top of a file.</li>
      <li>Since concatenation doesn't gaurantee order, wrap your file in an IIFE:
{% highlight javascript %}
(function() {
  "use strict";
  function f() {
    //...
  }
})();
{% endhighlight %}
      </li>
    </ul>

    <h4>2. Understand JavaScript's Floating Point Numbers</h4>
    <ul>
      <li>All numbers are <em>double-precision floating point numbers</em>, 64-bit doubles</li>
      <li>bitwise operators implicitly convert arguments to 32-bit integers</li>
      <li>Binary representation of a number can be detemined with <code>toString</code> and passing in a radix of 2:
{% highlight javascript %}
(8).toString(2); // => "1000"
{% endhighlight %}
      </li>
    </ul>

    <h4>3. Implicit Coercions</h4>
    <ul>
      <li>Arithmetic operators attempt to convert arguments to numbers</li>
      <li><code>+</code> is overloaded to perform numeric addition or string concatenation.
{% highlight javascript %}
2 + "3";      // => "23" If there is a string, number is cast to string
"2" + 3;      // => "23"

1 + 2 + "3";  // => "33" Addition is "left-associative" and groups from the left

"17" * 3;     // =>  51, the string is coerced into a number
"18" / 3;     // =>   6

null * 3;     // =>   0, null coerces to 0
undefined * 3;// => NaN, undefined coerces to NaN
"foo" * 3;    // => NaN, try parseInt("foo")
{% endhighlight %}
      </li>
      <li><code>NaN === NaN</code> evalutes to false</li>
      <li>Objects convert to strings by implictly calling <code>toString</code>
{% highlight javascript %}
"J" + { toString: function() { return "S"; }};   // => "JS"
{% endhighlight %}
      </li>
      <li>Objects convert to numbers by implictly calling <code>valueOf</code>
{% highlight javascript %}
2 * { valueOf: function() { return 3; }};        // => 6
{% endhighlight %}
      </li>
      <li>With <code>+</code>, object will coerced with <code>valueOf</code> over <code>toString</code> if both methods exist.</li>
      <li>Check for <code>undefined</code> with <code>typeof</code>, not truthiness:
{% highlight javascript %}
if (typeof x === 'undefined')
{% endhighlight %}
      </li>
    </ul>


    <h4>4. Primitives over Object Wrappers</h4>
    <ul>
      <li>A String object is only equal to itself
{% highlight javascript %}
var s1 = new String("hello");
var s2 = new String("hello");
s1 === s2;        // false
s1 == s2;         // false
{% endhighlight %}
      </li>
      <li>JavaScript implicitly coerces primitives so that they may be used with methods on the Object wrapper.
{% highlight javascript %}
"hello".toUpperCase();   // "HELLO"
{% endhighlight %}
    </ul>




  </div>
</div>