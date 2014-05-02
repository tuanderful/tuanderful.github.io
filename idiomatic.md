---
layout: default
title: Idiomatic
permalink: idiomatic/
---

# Idiomatic Clipboard

<style>
.idiomatic-notes {
}

.idiomatic-notes p {
}
</style>

<!-- Section 2: Parens, Linebreaks, Spaces ================================= -->
### Parens, Linebreaks, Spaces

<div class="row">
  <div class="col-md-6">
{% highlight js %}
if (condition) {
  // statements
}

while (something === somethingElse) {
  // statements
}

if (true) {
  // statements
} else {
  // statements
}
{% endhighlight %}
  </div>
  <div class="col-md-6 idiomatic-notes">
  <p>Spaces outside of parens
  <p>No spaces immediately inside parens
  <p>Spaces between operators
  </div>
</div>

<div class="row">
  <div class="col-md-6">
{% highlight js %}
for (var i = 0; i < 100; i++) {
  // statements
}

for ( ; i < length; i++ ) {
  // statements
}

for (prop in object) {
  // statements
}
{% endhighlight %}
  </div>
  <div class="col-md-6 idiomatic-notes">
  <p><strong>for-loop</strong>
  <p>Space after semi-colon

  </div>
</div>

<!-- Section 2: ============================================================ -->
### Assignments, Declarations, Functions
<div class="row">
  <div class="col-md-6">
{% highlight js %}
var foo = "bar",
  num = 1,
  undef
  someArray = [],
  some Obj = {};
{% endhighlight %}
  </div>
  <div class="col-md-6 idiomatic-notes">
    <p>Hoist variable declarations to the top
    <p>One <code>var</code> per scope
    <p>One variable per line
    <p><code>const</code> and <code>let</code> should also be at the top
    <p>Use object literals for array, object creation
    <br />
    <p>Variable indentation
    <p><input type="radio" />2 spaces</p>
    <p><input type="radio" />4 spaces</p>
  </div>
</div>

<div class="row">
  <div class="col-md-6">
{% highlight js %}
function foo( arg1, argN ) {
}

function square( number ) {
  return number * number;
}

foo( param1, param2 );

// continuous callback
function square( number, callback ) {
  callback( number * number );
}

square( 10, function( square ) {
  // callback statements
});

{% endhighlight %}
  </div>
  <div class="col-md-6 idiomatic-notes">
  </div>
</div>

### Assignments, Declarations, Functions
<div class="row">
  <div class="col-md-6">
{% highlight js %}
var factorial = function factorial( number ) {
  if ( number < 2 ) {
    return 1;
  }

  return number * factorial( number - 1 );
};
{% endhighlight %}
  </div>
  <div class="col-md-6 idiomatic-notes">
    <p>Function expression with named function
    <ul>
      <li>Can reference itself inside function</li>
      <li>Useful for debugging</li>
      <li>Note: Named function expressions can't be referenced externally
      (outside the scope of the function) by its <em>internal</em> name.</li>
    </ul>
  </div>
</div>









<!-- Section 2: ============================================================ -->
### Assignments, Declarations, Functions
<div class="row">
  <div class="col-md-6">
{% highlight js %}
{% endhighlight %}
  </div>
  <div class="col-md-6 idiomatic-notes">
  </div>
</div>




