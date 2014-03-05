---
layout: default
title: Aria
group: navigation
permalink: aria/
---

<div class="col-md-8 col-md-offset-2" id="home" role="main">
<h1 class="page-header">Aria Attributes</h1>

<table class="table table-condensed table-hover">
  <thead>
  </thead>
  <tbody>
    <tr>
      <td><code>aria-hidden="true"</code></td>
      <td></td>
    </tr>
    <tr>
      <td><code>aria-controls</code></td>
      <td></td>
    </tr>
    <tr>
      <td><code>aria-describedby</code></td>
      <td></td>
    </tr>
    <tr>
      <td><code>aria-disabled</code></td>
      <td></td>
    </tr>
    <tr>
      <td><code>aria-haspopup</code></td>
      <td></td>
    </tr>
    <tr>
      <td><code>aria-hidden</code></td>
      <td></td>
    </tr>
    <tr>
      <td><code>aria-label</code></td>
      <td></td>
    </tr>
    <tr>
      <td><code>aria-labelledby</code></td>
      <td></td>
    </tr>
    <tr>
      <td><code>aria-live</code></td>
      <td></td>
    </tr>
    <tr>
      <td><code>aria-readonly</code></td>
      <td></td>
    </tr>
    <tr>
      <td><code>aria-role</code></td>
      <td></td>
    </tr>
    <tr>
      <td><code>aria-valuemax</code></td>
      <td></td>
    </tr>
    <tr>
      <td><code>aria-valuemin</code></td>
      <td></td>
    </tr>
    <tr>
      <td><code>aria-valuenow</code></td>
      <td></td>
    </tr>
    <tr>
      <td><code>aria-valuetext</code></td>
      <td></td>
    </tr>
  </tbody>
</table>



<h1 class="page-header">Role Attributes</h1>

<h2>Landmark Roles</h2>
<p>Regions of the page intended to be navigational landmarks</p>
<table class="table table-condensed table-hover">
  <tbody>
    <tr><td><code>role="application"</code></td><td>A region declared as a web application, as opposed to a web document.</td></tr>
    <tr><td><code>role="banner"</code></td><td>A region that contains mostly site-oriented content, rather than page-specific content.</td></tr>
    <tr><td><code>role="complementary"</code></td><td>A supporting section of the document, designed to be complementary to the main content at a similar level in the DOM hierarchy, but remains meaningful when separated from the main content.</td></tr>
    <tr><td><code>role="contentinfo"</code></td><td>A large perceivable region that contains information about the parent document.</td></tr>
    <tr><td><code>role="form"</code></td><td>A landmark region that contains a collection of items and objects that, as a whole, combine to create a form. See related search.</td></tr>
    <tr><td><code>role="main"</code></td><td>The main content of a document.</td></tr>
    <tr><td><code>role="navigation"</code></td><td>A collection of navigational elements (usually links) for navigating the document or related documents.</td></tr>
    <tr><td><code>role="search"</code></td><td>A landmark region that contains a collection of items and objects that, as a whole, combine to create a search facility. See related form.</td></tr>
  </tbody>
</table>











<h2>Document Structure</h2>
<p>Describe structures that organize the page. Usually not interactive.</p>
<table class="table table-condensed table-hover">
  <tbody>
    <tr><td><code>role="article"</code></td><td>A section of a page that consists of a composition that forms an independent part of a document, page, or site.</td></tr>
    <tr><td><code>role="columnheader"</code></td><td>A cell containing header information for a column.</td></tr>
    <tr><td><code>role="definition"</code></td><td>A definition of a term or concept.</td></tr>
    <tr><td><code>role="directory"</code></td><td>A list of references to members of a group, such as a static table of contents.</td></tr>
    <tr><td><code>role="document"</code></td><td>A region containing related information that is declared as document content, as opposed to a web application.</td></tr>
    <tr><td><code>role="group"</code></td><td>A set of user interface objects which are not intended to be included in a page summary or table of contents by assistive technologies.</td></tr>
    <tr><td><code>role="heading"</code></td><td>A heading for a section of the page.</td></tr>
    <tr><td><code>role="img"</code></td><td>A container for a collection of elements that form an image.</td></tr>
    <tr><td><code>role="list"</code></td><td>A group of non-interactive list items. See related listbox.</td></tr>
    <tr><td><code>role="listitem"</code></td><td>A single item in a list or directory.</td></tr>
    <tr><td><code>role="math"</code></td><td>Content that represents a mathematical expression.</td></tr>
    <tr><td><code>role="note"</code></td><td>A section whose content is parenthetic or ancillary to the main content of the resource.</td></tr>
    <tr><td><code>role="presentation"</code></td><td>An element whose implicit native role semantics will not be mapped to the accessibility API.</td></tr>
    <tr><td><code>role="region"</code></td><td>A large perceivable section of a web page or document, that is important enough to be included in a page summary or table of contents, for example, an area of the page containing live sporting event statistics.</td></tr>
    <tr><td><code>role="row"</code></td><td>A row of cells in a grid.</td></tr>
    <tr><td><code>role="rowgroup"</code></td><td>A group containing one or more row elements in a grid.</td></tr>
    <tr><td><code>role="rowheader"</code></td><td>A cell containing header information for a row in a grid.</td></tr>
    <tr><td><code>role="separator"</code></td><td>A divider that separates and distinguishes sections of content or groups of menuitems.</td></tr>
    <tr><td><code>role="toolbar"</code></td><td>A collection of commonly used function buttons or controls represented in compact visual form.</td></tr>
  </tbody>
</table>

<h2>Widgets</h2>
<p>Interactive, user interface widgets. Standalone, or apart of composite UI widgets.</p>
<table class="table table-condensed table-hover">
  <tbody>
    <tr><td><code>role="alert"</code></td><td>A message with important, and usually time-sensitive, information. See related alertdialog and status.</td></tr>
    <tr><td><code>role="alertdialog"</code></td><td>A type of dialog that contains an alert message, where initial focus goes to an element within the dialog. See related alert and dialog.</td></tr>
    <tr><td><code>role="button"</code></td><td>An input that allows for user-triggered actions when clicked or pressed. See related link.</td></tr>
    <tr><td><code>role="checkbox"</code></td><td>A checkable input that has three possible values: true, false, or mixed.</td></tr>
    <tr><td><code>role="dialog"</code></td><td>A dialog is an application window that is designed to interrupt the current processing of an application in order to prompt the user to enter information or require a response. See related alertdialog.</td></tr>
    <tr><td><code>role="gridcell"</code></td><td>A cell in a grid or treegrid.</td></tr>
    <tr><td><code>role="link"</code></td><td>An interactive reference to an internal or external resource that, when activated, causes the user agent to navigate to that resource. See related button.</td></tr>
    <tr><td><code>role="log"</code></td><td>A type of live region where new information is added in meaningful order and old information may disappear. See related marquee.</td></tr>
    <tr><td><code>role="marquee"</code></td><td>A type of live region where non-essential information changes frequently. See related log.</td></tr>
    <tr><td><code>role="menuitem"</code></td><td>An option in a set of choices contained by a menu or menubar.</td></tr>
    <tr><td><code>role="menuitemcheckbox"</code></td><td>A menuitem with a checkable state whose possible values are true, false, or mixed.</td></tr>
    <tr><td><code>role="menuitemradio"</code></td><td>A checkable menuitem in a set of elements with role menuitemradio, only one of which can be checked at a time.</td></tr>
    <tr><td><code>role="option"</code></td><td>A selectable item in a select list.</td></tr>
    <tr><td><code>role="progressbar"</code></td><td>An element that displays the progress status for tasks that take a long time.</td></tr>
    <tr><td><code>role="radio"</code></td><td>A checkable input in a group of radio roles, only one of which can be checked at a time.</td></tr>
    <tr><td><code>role="scrollbar"</code></td><td>A graphical object that controls the scrolling of content within a viewing area, regardless of whether the content is fully displayed within the viewing area.</td></tr>
    <tr><td><code>role="slider"</code></td><td>A user input where the user selects a value from within a given range.</td></tr>
    <tr><td><code>role="spinbutton"</code></td><td>A form of range that expects the user to select from among discrete choices.</td></tr>
    <tr><td><code>role="status"</code></td><td>A container whose content is advisory information for the user but is not important enough to justify an alert, often but not necessarily presented as a status bar. See related alert.</td></tr>
    <tr><td><code>role="tab"</code></td><td>A grouping label providing a mechanism for selecting the tab content that is to be rendered to the user.</td></tr>
    <tr><td><code>role="tabpanel"</code></td><td>A container for the resources associated with a tab, where each tab is contained in a tablist.</td></tr>
    <tr><td><code>role="textbox"</code></td><td> Input that allows free-form text as its value.</td></tr>
    <tr><td><code>role="timer"</code></td><td>A type of live region containing a numerical counter which indicates an amount of elapsed time from a start point, or the time remaining until an end point.</td></tr>
    <tr><td><code>role="tooltip"</code></td><td>A contextual popup that displays a description for an element.</td></tr>
    <tr><td><code>role="treeitem"</code></td><td>An option item of a tree. This is an element within a tree that may be expanded or collapsed if it contains a sub-level group of treeitem elements.</td></tr>
  </tbody>
</table>

<h2>Composite UI Widgets</h2>
<p>Typically containers that for other widgets.</p>
<table class="table table-condensed table-hover">
  <tbody>
    <tr><td><code>role="combobox"</code></td><td>A presentation of a select; usually similar to a textbox where users can type ahead to select an option, or type to enter arbitrary text as a new item in the list. See related listbox.</td></tr>
    <tr><td><code>role="grid"</code></td><td>A grid is an interactive control which contains cells of tabular data arranged in rows and columns, like a table.</td></tr>
    <tr><td><code>role="listbox"</code></td><td>A widget that allows the user to select one or more items from a list of choices. See related combobox and list.</td></tr>
    <tr><td><code>role="menu"</code></td><td>A type of widget that offers a list of choices to the user.</td></tr>
    <tr><td><code>role="menubar"</code></td><td>A presentation of menu that usually remains visible and is usually presented horizontally.</td></tr>
    <tr><td><code>role="radiogroup"</code></td><td>A group of radio buttons.</td></tr>
    <tr><td><code>role="tablist"</code></td><td>A list of tab elements, which are references to tabpanel elements.</td></tr>
    <tr><td><code>role="tree"</code></td><td>A type of list that may contain sub-level nested groups that can be collapsed and expanded.</td></tr>
    <tr><td><code>role="treegrid"</code></td><td>A grid whose rows can be expanded and collapsed in the same manner as for a tree.</td></tr>
  </tbody>
</table>





<h2>Abstract Roles</h2>
<table class="table table-condensed table-hover">
  <tbody>
    <tr>
      <td><code>role="command"</code></td>
      <td>A form of widget that performs an action but does not receive input data.</td>
    </tr>
    <tr>
      <td><code>role="composite"</code></td>
      <td>A widget that may contain navigable descendants or owned children.</td>
    </tr>
    <tr>
      <td><code>role="input"</code></td>
      <td>A generic type of widget that allows user input.</td>
    </tr>
    <tr>
      <td><code>role="landmark"</code></td>
      <td>A region of the page intended as a navigational landmark.</td>
    </tr>
    <tr>
      <td><code>role="range"</code></td>
      <td>An input representing a range of values that can be set by the user.</td>
    </tr>
    <tr>
      <td><code>role="roletype"</code></td>
      <td>The base role from which all other roles in this taxonomy inherit.</td>
    </tr>
    <tr>
      <td><code>role="section"</code></td>
      <td>A renderable structural containment unit in a document or application.</td>
    </tr>
    <tr>
      <td><code>role="sectionhead"</code></td>
      <td>A structure that labels or summarizes the topic of its related section.</td>
    </tr>
    <tr>
      <td><code>role="select"</code></td>
      <td>A form widget that allows the user to make selections from a set of choices.</td>
    </tr>
    <tr>
      <td><code>role="structure"</code></td>
      <td>A document structural element.</td>
    </tr>
    <tr>
      <td><code>role="widget"</code></td>
      <td>An interactive component of a graphical user interface (GUI).</td>
    </tr>
    <tr>
      <td><code>role="window"</code></td>
      <td>A browser or application window.</td>
    </tr>
  </tbody>
</table>

</div>