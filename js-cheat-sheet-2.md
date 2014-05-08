---
layout: default-narrow
title: JS Reference
group: navigation
markdown: redcarpet
permalink: js-reference/
---

<style>
table.js-api .highlight {
  margin: 0;
  border: none;
  padding: 0;
  border-radius: 0px;
  background: none;
}
</style>


### Browser Events

![](https://dvcs.w3.org/hg/webperf/raw-file/tip/specs/NavigationTiming/timing-overview.png)

### Browser Object Model
#### Window Object
* Acts as `Global` object.
* Variables added to global scope via `var` have their `[[Configurable]]` attribute set to `false` and cannot be removed via `delete`.
* If `foo` is not defined, trying to access `foo` will throw a `Reference Error: foo is not defined` while `window.foo` will return undefined (because it is a property lookup).
* Each frame has its own `window` object. `top` ferences the outermost frame, `parent` points to the current frame's immediate parent frame.
* `window.screenLeft`, `window.screenX`, `window.screenTop`, `window.screenY`
* `window.innerWidth`, `window.innerHeight`, `window.outerWidth`, `window.outerHeight`
  * `window.resizeTo()`, `window.resizeBy()`
* `window.open()` can return null if pop-up blocker prevents it from happening. `window.close()` to close.
* `setTimeout()` and `setInterval()` are window methods.
  * Avoid intervals, better to recurseviely call `setTimeout()`

#### Location Object
* `hash`, `hostname`, `href`, `pathname`, `search` (query string)
* Set `window.location` to navigate
* `replace()` to navigate to a URL but not update the history stack
* `reload()` reloads current page

#### Navigator Object
_TODO_
* Browser information


### Document Object Model
#### Node Type

All node types inherit from <code>Node</code> in JavaScript. A node <code>n</code> shares the same basic properties:

<table class="table table-condensed js-api">
  <tr>
    <td>{% highlight javascript %}n.nodeType{% endhighlight %}</td>
    <td>A number from 1 - 12</td>
  </tr>
  <tr>
    <td>{% highlight javascript %}n.nodeName{% endhighlight %}</td>
    <td>For elements, the tag name</td>
  </tr>
  <tr>
    <td>{% highlight javascript %}n.nodeValue{% endhighlight %}</td>
    <td>For elements, always <code>null</code></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}n.childNodes{% endhighlight %}</td>
    <td>A <code>NodeList</code>, an array like object of child nodes.
      <br />Can be accessed via bracket notation, <code>n.childNodes[0]</code>
      <br />or the <code>item()</code> method, <code>n.childNodes.item(1)</code>
      <br />Also contains a <code>length</code> property.
    </td>
  </tr>
  <tr>
    <td>{% highlight javascript %}n.parentNode{% endhighlight %}</td>
    <td>Parent in the document tree</td>
  </tr>
  <tr>
    <td>{% highlight javascript %}n.previousSibling{% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}n.nextSibling{% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}n.firstChild{% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}n.lastChild{% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}n.hasChildNodes(){% endhighlight %}</td>
    <td>More efficient than <code>n.childNodes.length</code></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}n.ownerDocument(){% endhighlight %}</td>
    <td>Quick way to access <code>Document</code> node rather than traversing up the node hierarchy</td>
  </tr>
  <tr>
    <td>{% highlight javascript %}n.appendChild(){% endhighlight %}</td>
    <td>Add node to the end of <code>childNodes</code>.
      <br />If passing in a <code>node</code>, remove it from previous location.</td>
  </tr>
  <tr>
    <td>{% highlight javascript %}n.insertBefore(){% endhighlight %}</td>
    <td>Accepts two arguments: node to insert and reference node.
    <br /><code>null</code> reference node? Act as <code>.appendChild()</code></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}n.replaceChild(){% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}n.removeChild(){% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}n.cloneNode(){% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}n.normalize(){% endhighlight %}</td>
    <td>Remove empty text nodes and join text nodes that are immediate siblings.</td>
  </tr>
</table>




#### Document Type

<h5>Properties</h5>
<table class="table table-condensed js-api">
  <tr>
    <td>{% highlight javascript %}document.anchors{% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}document.applets{% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}document.forms{% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}document.images{% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}document.links{% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}document.readyState == 'loading'{% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}document.readyState == 'interactive'{% endhighlight %}</td>
    <td>DOMContentLoaded</td>
  </tr>
  <tr>
    <td>{% highlight javascript %}document.readyState == 'complete'{% endhighlight %}</td>
    <td>sub-resources loaded</td>
  </tr>
</table>

<h5>Methods</h5>
<table class="table table-condensed js-api">
  <tr>
    <td>{% highlight javascript %}document.getElementById(){% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}document.getElementsByTagName(){% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}document.getElementsByClassName(){% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}document.querySelector('.some.selector'){% endhighlight %}</td>
    <td>{% highlight javascript %}$('.some.selector')[0];{% endhighlight %}</td>
  </tr>
  <tr>
    <td>{% highlight javascript %}document.querySelectorAll('.some.selector'){% endhighlight %}</td>
    <td>Returns array of 0 or more matched elements
        <br />{% highlight javascript %}$('.some.selector');{% endhighlight %}</td>
  </tr>
  <tr>
    <td>{% highlight javascript %}document.createElement(){% endhighlight %}</td>
    <td></td> 
  </tr>
  <tr>
    <td>{% highlight javascript %}document.createDocumentFragment(){% endhighlight %}</td>
    <td></td>
  </tr>
</table>


#### Element Type

<h5>Properties</h5>
<table class="table table-condensed js-api">
  <tr>
    <td>{% highlight javascript %}element.childElementCount{% endhighlight %}</td>
    <td>Number of children</td>
  </tr>
  <tr>
    <td>{% highlight javascript %}element.firstElementChild{% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}element.lastElementChild{% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}element.previousElementSibling{% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}element.nextElementSibling{% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}element.className{% endhighlight %}</td>
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
  </tr>
</table>

<h5>Methods</h5>
<table class="table table-condensed js-api">
  <tr>
    <td>{% highlight javascript %}element.getElementById(){% endhighlight %}</td>
    <td>$('#...')</td>
  </tr>
  <tr>
    <td>{% highlight javascript %}element.getElementByTagName(){% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}element.querySelector(){% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}element.createElement(){% endhighlight %}</td>
    <td></td>
  </tr>
  <tr>
    <td>{% highlight javascript %}element.createDocumentFragment(){% endhighlight %}</td>
    <td></td>
  </tr>
</table>



