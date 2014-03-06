---
layout: default-narrow
title: Effective JS
group: navigation
markdown: redcarpet
permalink: effective-js/
---

<style>
.highlight {
  margin: 0 40px 14px;
}
</style>

<h1 class="page-header">{{ page.title }}</h1>

### Accustoming Yourself to JavaScript


#### 1. Know Which JavaScript You Are Using
* Strict Mode only works the `"use strict";` is included at the top of a function or the top of a file.

* Since concatenation doesn't gaurantee order, wrap your file in an IIFE:
{% highlight javascript %}
(function() {
    "use strict";
  function f() {
    //...
  }
})();
{% endhighlight %}


#### 2. Understand JavaScript's Floating Point Numbers
* All numbers are _double-precision floating point numbers_, 64-bit doubles

* bitwise operators implicitly convert arguments to 32-bit integers

* Binary representation of a number can be detemined with `toString` and passing in a radix of 2:
{% highlight javascript %}
(8).toString(2); // => "1000"
{% endhighlight %}


#### 3. Implicit Coercions
* Arithmetic operators attempt to convert arguments to numbers

* `+` is overloaded to perform numeric addition or string concatenation.
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

* `NaN === NaN` evalutes to false

* Objects convert to strings by implictly calling `toString`
{% highlight javascript %}
"J" + { toString: function() { return "S"; }};   // => "JS"
{% endhighlight %}

* Objects convert to numbers by implictly calling `valueOf`
{% highlight javascript %}
2 * { valueOf: function() { return 3; }};        // => 6
{% endhighlight %}

* With `+`, object will coerced with `valueOf` over `toString` if both methods exist.

* Check for `undefined` with `typeof`, not truthiness:
{% highlight javascript %}
if (typeof x === 'undefined')
{% endhighlight %}


#### 4. Primitives over Object Wrappers

* A String object is only equal to itself
{% highlight javascript %}
var s1 = new String("hello");
var s2 = new String("hello");
s1 === s2;        // false
s1 == s2;         // false
{% endhighlight %}

* JavaScript implicitly coerces primitives so that they may be used with methods on the Object wrapper.
{% highlight javascript %}
"hello".toUpperCase();   // "HELLO"
{% endhighlight %}
