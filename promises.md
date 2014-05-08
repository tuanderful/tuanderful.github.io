---
layout: default-narrow
title: Promises
group: navigation
markdown: redcarpet
permalink: promises/
---

# ES5 Promises

Create a promise object, passing in a function that you want to execute, and two functions: resolve and reject.

{% highlight javascript %}
var promise = new Promise(function(resolve, reject) {
});
{% endhighlight %}

In your callback, invoke either <code>resolve</code> or <code>reject</code>:

{% highlight javascript %}
var promise = new Promise(function(resolve, reject) {
  // do a thing, possibly async, then…

  if (/* everything turned out fine */) {
    resolve("Stuff worked!");
  }
  else {
    reject(Error("It broke"));
  }
});
{% endhighlight %}

Subsequent functions can be chained to your new <code>promise</code> instance with <code>.then()</code>:
{% highlight javascript %}
promise.then(function(){
  // on fulfilled
}, function() {
  // on rejected
});
{% endhighlight %}

### Transformation

The paramter you pass when you <code>resolve</code> becomes the argument of the <code>onFulfilled</code> handler:

{% highlight javascript %}
var promise = new Promise(function(resolve, reject) {
  resolve(1);
});

promise.then(function(val) {
  console.log(val); // 1
  return val + 2;
}).then(function(val) {
  console.log(val); // 3
});{% endhighlight %}


### Error Handling

One way of adding an <code>onRejected</code> handler:

{% highlight javascript %}
promise.then(function(){
  // on fulfilled
}, function() {
  // on rejected
});
{% endhighlight %}

Also, you can chain the handler to <code>catch()</code>:

{% highlight javascript %}
promise.then(function(){
  // on fulfilled
}).catch(function() {
  // on rejected
});
{% endhighlight %}


### All

We can combine both the worlds of async and sync with <code>all</code>:

{% highlight javascript %}
Promise.all(arrayOfPromises).then(function(arrayOfResults) {
  //...
});{% endhighlight %}

{% highlight javascript %}
promise.then(function() {
  // Take an array of promises and wait on them all
  return Promise.all(
    [array, of, promises]
  );
}).then(function(){
  // something done after all promises are resolved
});{% endhighlight %}

# API

### Constructor

{% highlight javascript %}new Promise(function(resolve, reject) {});{% endhighlight %}

`resolve(thenable)`

Your promise will be fulfilled/rejected with the outcome of thenable

`resolve(obj)`

Your promise is fulfilled with obj

`reject(obj)`

Your promise is rejected with obj. For consistency and debugging (eg stack traces), obj should be an instanceof Error. Any errors thrown in the constructor callback will be implicitly passed to reject().



### Static Methods

`Promise.resolve(promise);`

Returns promise (only if promise.constructor == Promise)

`Promise.resolve(thenable);`

Make a new promise from the thenable. A thenable is promise-like in as far as it has a "then" method.

`Promise.resolve(obj);`

Make a promise that fulfills to obj. in this situation.

`Promise.reject(obj);`

Make a promise that rejects to obj. For consistency and debugging (e.g. stack traces), obj should be an instanceof Error.

`Promise.all(array);`

Make a promise that fulfills when every item in the array fulfills, and rejects if (and when) any item rejects. Each array item is passed to Promise.resolve, so the array can be a mixture of promise-like objects and other objects. The fulfillment value is an array (in order) of fulfillment values. The rejection value is the first rejection value.

`Promise.race(array);`

Make a Promise that fulfills as soon as any item fulfills, or rejects as soon as any item rejects, whichever happens first.


### Instance Methods

`promise.then(onFulfilled, onRejected)`

onFulfilled is called when/if "promise" resolves. onRejected is called when/if "promise" rejects. Both are optional, if either/both are omitted the next onFulfilled/onRejected in the chain is called. Both callbacks have a single parameter, the fulfillment value or rejection reason. "then" returns a new promise equivalent to the value you return from onFulfilled/onRejected after being passed through Promise.resolve. If an error is thrown in the callback, the returned promise rejects with that error.

`promise.catch(onRejected)`

Sugar for <code>promise.then(undefined, onRejected)</code>


# Example

For these examples, I've defined some logging as follows:

{% highlight javascript %}
function printout(i) {
  console.log("Executing Callback " + i + ": " + performance.now());
}{% endhighlight %}


#### Then
We'd like to ensure 2 gets printed out after 1.
{% highlight javascript %}
var promise = new Promise(function(resolve, reject) {
  setTimeout(function(){
    printout(1);
  }, 1000);
});

promise.then(function(){
  printout(2);
});

printout(3);{% endhighlight %}

This fires off a timer, prints out 3, then prints out 1.
It never prints out 2, because we never resolve our promise!


#### Resolving a Promise

{% highlight javascript %}
var promise = new Promise(function(resolve, reject) {
  setTimeout(function(){
    printout(1);
  }, 1000);

  resolve();
});

promise.then(function(){
  printout(2);
});

printout(3);{% endhighlight %}

This fires off a timer, prints out 3, 2, 1.
2 is now printed, but it's not in order!
That's because the timer is fired, the promise is resolved, 2 is printed while the timer is still running, then 1 is printed.


{% highlight javascript %}
var promise = new Promise(function(resolve, reject) {
  setTimeout(function(){
    printout(1);
    resolve();
  }, 1000);
});

promise.then(function(){
  printout(2);
});

printout(3);{% endhighlight %}


We'll want to add the resolve to the function inside of the timeout to ensure 1 is printed before 2.

In all these cases, 3 is printed out first. It's not part of the promise chain.

#### Rejecting a Promise

If your promise is fulfilled, the <code>onFulfilled</code> callback is executed.
Otherwise, the <code>onRejected</code> callback is executed.

{% highlight javascript %}
var promise = new Promise(function(resolve, reject) {
  setTimeout(function(){
    printout(1);
    resolve();    // try changing to reject();
  }, 1000);
});

promise.then(function(){
  printout('2-onResolve');
}, function(){
  printout('2-onReject');
});

printout(3);{% endhighlight %}


# Other

States and Fates: https://github.com/domenic/promises-unwrapping/blob/master/docs/states-and-fates.md

![](http://www.mediumequalsmessage.com/blog-images/promises.png)

# Polyfill

{% highlight javascript %}
import { config, configure } from "./config";
import { objectOrFunction, isFunction, now } from './utils';
import { all } from "./all";
import { race } from "./race";
import { resolve as staticResolve } from "./resolve";
import { reject as staticReject } from "./reject";
import { asap } from "./asap";

var counter = 0;

config.async = asap; // default async is asap;

/**
 * Promise constructor
 */

function Promise(resolver) {
  if (!isFunction(resolver)) {
    throw new TypeError('You must pass a resolver function as the first argument to the promise constructor');
  }

  if (!(this instanceof Promise)) {
    throw new TypeError("Failed to construct 'Promise': Please use the 'new' operator, this object constructor cannot be called as a function.");
  }

  this._subscribers = [];

  // pass this promise into the resolver
  invokeResolver(resolver, this);
}

/**
 * Invocations
 */

function invokeResolver(resolver, promise) {
  function resolvePromise(value) {
    // (a) resolve
    resolve(promise, value);
  }

  function rejectPromise(reason) {
    reject(promise, reason);
  }

  try {
    // execute the resolver (arguments[0]), which effectively calls (a)
    resolver(resolvePromise, rejectPromise);
  } catch(e) {
    rejectPromise(e);
  }
}

function invokeCallback(settled, promise, callback, detail) {
  var hasCallback = isFunction(callback),
      value, error, succeeded, failed;

  if (hasCallback) {
    try {
      value = callback(detail);
      succeeded = true;
    } catch(e) {
      failed = true;
      error = e;
    }
  } else {
    value = detail;
    succeeded = true;
  }

  if (handleThenable(promise, value)) {
    return;
  } else if (hasCallback && succeeded) {
    resolve(promise, value);
  } else if (failed) {
    reject(promise, error);
  } else if (settled === FULFILLED) {
    resolve(promise, value);
  } else if (settled === REJECTED) {
    reject(promise, value);
  }
}

var PENDING   = void 0;
var SEALED    = 0;
var FULFILLED = 1;
var REJECTED  = 2;

function subscribe(parent, child, onFulfillment, onRejection) {
  var subscribers = parent._subscribers;
  var length = subscribers.length;

  subscribers[length] = child;
  subscribers[length + FULFILLED] = onFulfillment;
  subscribers[length + REJECTED]  = onRejection;
}

function publish(promise, settled) {
  var child, callback,
      subscribers = promise._subscribers,
      detail = promise._detail;

  for (var i = 0; i < subscribers.length; i += 3) {
    child = subscribers[i];
    callback = subscribers[i + settled];

    invokeCallback(settled, child, callback, detail);
  }

  promise._subscribers = null;
}

Promise.prototype = {
  constructor: Promise,

  _state: undefined,
  _detail: undefined,
  _subscribers: undefined,

  then: function(onFulfillment, onRejection) {
    // create a promise for this and then
    var promise = this;
    var thenPromise = new this.constructor(function() {});

    //
    if (this._state) {
      var callbacks = arguments;
      config.async(function invokePromiseCallback() {
        invokeCallback(promise._state, thenPromise, callbacks[promise._state - 1], promise._detail);
      });
    } else {
      subscribe(this, thenPromise, onFulfillment, onRejection);
    }

    // return then
    return thenPromise;
  },

  'catch': function(onRejection) {
    return this.then(null, onRejection);
  }
};

Promise.all = all;
Promise.race = race;
Promise.resolve = staticResolve;
Promise.reject = staticReject;

function handleThenable(promise, value) {
  var then = null,
  resolved;

  try {
    if (promise === value) {
      throw new TypeError("A promises callback cannot return that same promise.");
    }

    if (objectOrFunction(value)) {
      then = value.then;

      if (isFunction(then)) {
        then.call(value, function(val) {
          if (resolved) { return true; }
          resolved = true;

          if (value !== val) {
            resolve(promise, val);
          } else {
            fulfill(promise, val);
          }
        }, function(val) {
          if (resolved) { return true; }
          resolved = true;

          reject(promise, val);
        });

        return true;
      }
    }
  } catch (error) {
    if (resolved) { return true; }
    reject(promise, error);
    return true;
  }

  return false;
}

function resolve(promise, value) {
  if (promise === value) {
    fulfill(promise, value);
  } else if (!handleThenable(promise, value)) {
    fulfill(promise, value);
  }
}

function fulfill(promise, value) {
  if (promise._state !== PENDING) { return; }
  promise._state = SEALED;
  promise._detail = value;

  config.async(publishFulfillment, promise);
}

function reject(promise, reason) {
  if (promise._state !== PENDING) { return; }
  promise._state = SEALED;
  promise._detail = reason;

  config.async(publishRejection, promise);
}

function publishFulfillment(promise) {
  publish(promise, promise._state = FULFILLED);
}

function publishRejection(promise) {
  publish(promise, promise._state = REJECTED);
}

export { Promise };
{% endhighlight %}
















