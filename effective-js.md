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
.table {
  width: 537px;
  margin-left: 40px;
}

h3 {
  font-weight: 600;
  margin-top: 48px;
}

h4 {
  margin-top: 36px;
}
</style>

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


#### 4. Primitives over Primitive Wrappers

* A String object is only equal to itself
{% highlight javascript %}
var s1 = new String("hello");
var s2 = new String("hello");
s1 === s2;        // false
s1 == s2;         // false
{% endhighlight %}

* JavaScript implicitly coerces primitives so that they may be used with methods on the Primitive wrapper.
{% highlight javascript %}
"hello".toUpperCase();   // "HELLO"
{% endhighlight %}

* You can set properties on primitives, as they are implicitly wrapped. After the set, the object is destroyed, so the properties don't persist.
{% highlight javascript %}
"hello".someProperty = 17;
"hello".someProperty;       // undefined
{% endhighlight %}


#### 5. Avoid using == with mixed types

* Explicitly coerce primitives to numbers before comparison with unary `+` operator

* The following coercion rules apply when using ==

<table class="table table-condensed">
  <tr>
    <th>Argument</th>
    <th>Coerces to</th>
  </tr>
  <tr>
    <td>string, number, boolean</td>
    <td>number</td>
  </tr>
  <tr>
    <td><code>Date</code></td>
    <td>toString, valueOf</td>
  </tr>
  <tr>
    <td>Non-<code>Date</code> object</td>
    <td>valueOf, toString</td>
  </tr>
</table>

* `null == undefined`
* `null` and `undefined` evaluate to false when compared to anything other than `null` or `undefined`

{% highlight javascript %}
var date = new Date("1999/12/31");    // date => date.toString() => "Fri Dec 31 1999 00:00:00 GMT-0800 (PST)"
date == "1999/12/31";                 // false
{% endhighlight %}


#### 6. Limits of Semicolon Insertion

* Semicolons are only inserted:
  * before }
  * after one more more newlines
  * end of program
  * next input token cannot be parsed

{% highlight javascript %}
a = b
(f());    // => a = b(f()); // parses OK - no ; is inserted

a = b
f();      // => a = b f();  // doesn't parse, ; is inserted
{% endhighlight %}

* Five problematic characters: `(`, `[`, `+`, `-`, `/`
  * Never omit before a statement with problem character
  * Can act as an expression operator, so newlines starting with these won't have semi-colon inserted
{% highlight javascript %}
a = b
["r", "g", "b"].forEach(...)

a = b['r', 'g', 'b'].forEach()  // a = b['b'].forEach()
{% endhighlight %}

* Never put newline before argument to `return` `throw`, `break`, `continue`, `++`, or `--`

* Semi-colons never inserted in head of `for` loop

* Semi-colons never inserted as empty statement

{% highlight javascript %}
function infiniteLoop() { while (true) }    // parse error
// must add ; after while()
{% endhighlight %}


#### 7. 16-bit Code Units

* JavaScript strings consist of 16-bit code units
* One *code point* such as &#x1d11e; can contain two *code units* (known as surrogate pairs)
* Cannot rely on `length`, `charAt`, and `charCodeAt`

<table class="table table-condensed" id="item-7-table">
<style scoped>
#item-7-table td {
  text-align: center;
  font-size: .85em;
}
</style>
<tr>
  <td colspan="2">&#x1d11e;</td>
  <td></td>
  <td>c</td>
  <td>l</td>
  <td>e</td>
  <td>f</td>
</tr>
<tr>
  <td>0xd834</td>
  <td>0xdd1e</td>
  <td>0x0020</td>
  <td>0x0063</td>
  <td>0x006c</td>
  <td>0x0065</td>
  <td>0x0066</td>
</tr>
</table>


### Variable Scope

#### 8. Minimize Use of Global Object
* Use global for feature detection, like `if (!this.JSON)`
* Calling a constructor without new may introduce variables into global scope
{% highlight javascript %}
function Person(name) {
  this.name = name
}
var person = Person("Tuan");              // this binds to global scope
console.log(person instanceof Person);    // false
console.log(typeof person);               // "undefined"
console.log(name);                        // "Tuan" - defined under window.name
{% endhighlight %}


#### 9. Always Declare Local Variables
* Variables not initialized with `var` are crated on global scope

#### 10. Avoid with
* `with` treats an object as if it represented a variable scope
* Explicitly bind local variables to object properties instead of implicitly binding with `with`



<!--ul>
{% for chapter in site.data.effective-js %}
  <li>
    <a href="https://github.com/{{ chapter.name }}">
      {{ chapter.name }}
    </a>
    <ul>
    {% for item in chapter.sections %}
      <li>
        {{ item.name }}
      </li>
    {% endfor %}
    </ul>
  </li>
{% endfor %}
</ul-->
