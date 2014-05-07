---
layout: default-narrow
title: Polyfills
group: navigation
markdown: redcarpet
permalink: polyfills/
---



<h1 class="page-header">jQuery</h1>

### AJAX
{% highlight javascript %}request = new XMLHttpRequest();
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

request.send();{% endhighlight %}


<h1 class="page-header">ES5</h1>

### Curry
{% highlight javascript %}Function.prototype.curry = function() {
  var args = arguments,     // save, for partial application
      that = this,
  return function() {
           // fn invocation, with null context
           // concat args (from partial application) with current arguments
    return that.apply(null, args.concat(Array.prototype.slice.apply(arguments)));
  }
}{% endhighlight %}


### Bind

#### Polyfill, from MDN
{% highlight javascript %}
if (!Function.prototype.bind) {
  Function.prototype.bind = function (oThis) {
    if (typeof this !== "function") {
      // closest thing possible to the ECMAScript 5 internal IsCallable function
      throw new TypeError("Function.prototype.bind - what is trying to be bound is not callable");
    }

    var aArgs = Array.prototype.slice.call(arguments, 1), 
        fToBind = this, 
        fNOP = function () {},
        fBound = function () {
          return fToBind.apply(this instanceof fNOP && oThis
                                 ? this
                                 : oThis,
                               aArgs.concat(Array.prototype.slice.call(arguments)));
        };

    fNOP.prototype = this.prototype;
    fBound.prototype = new fNOP();

    return fBound;
  };
}
{% endhighlight %}





