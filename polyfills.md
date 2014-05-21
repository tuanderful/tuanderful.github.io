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

### Event Listeners
{% highlight javascript %}
// addHandler(node, 'click', cb);
function addHandler(e, type, handler) {
  if (e.addEventListener) {
    // DOM 2
    e.addEventListener(type, handler, false);
  } else if (e.attachEvent) {
    // IE 8
    e.attachEvent('on'+type, handler);
  } else {
    element['on'+type] = handler;       // detach? null
  }
}
{% endhighlight %}



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
}

function add(a, b){ return a + b }

var add1 = add.curry(1);{% endhighlight %}


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



# Underscore

### forEach


<b>ES5 Usage:</b> <code>obj.forEach(iterator, context);</code>, where iterator is <code>function iterator(element, index, array)</code>.

{% highlight javascript %}
var each = _.each = _.forEach = function(obj, iterator, context) {
  if (obj == null) return obj;
  if (nativeForEach && obj.forEach === nativeForEach) {
    obj.forEach(iterator, context);
  } else if (obj.length === +obj.length) {
    for (var i = 0, length = obj.length; i < length; i++) {
      if (iterator.call(context, obj[i], i, obj) === breaker) return;
    }
  } else {
    var keys = _.keys(obj);
    for (var i = 0, length = keys.length; i < length; i++) {
      if (iterator.call(context, obj[keys[i]], keys[i], obj) === breaker) return;
    }
  }
  return obj;
};{% endhighlight %}


### Extend

{% highlight javascript %}
_.extend = function(obj) {
  each(slice.call(arguments, 1), function(source) {
    if (source) {
      for (var prop in source) {
        obj[prop] = source[prop];
      }
    }
  });
  return obj;
};{% endhighlight %}

### Clone

{% highlight javascript %}
_.clone = function(obj) {
  if (!_.isObject(obj)) return obj;
  return _.isArray(obj) ? obj.slice() : _.extend({}, obj);
};{% endhighlight %}






