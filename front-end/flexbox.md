# Flexbox

> **Jennifer Pazos on 08/14/19**

## **Flexbox Layout Module**

The flex layout is meant to accommodate all kinds of display devices and screen sizes by expanding items to fill available free space and shrinking them to prevent overflow. Most importantly, the flexbox layout is direction-agnostic as opposed to regular layouts \(block which is vertically-based and inline which is horizontally-based\).

## **Flexbox Basics**

Since flexbox is a whole module, it comes with an extensive set of properties. Some are meant to be set on the container \(parent element, known as "flex container"\), whereas the others are meant to be set on the children \(said "flex items"\).

* The flex layout is based on "flex-flow directions"
* Items will be laid out following either the main axis \(from main-start to main-end\) or the cross axis \(from cross-start to cross-end\)
* It is possible to nest flex displays
* Start with your outermost container when setting up flexbox

{% tabs %}
{% tab title="HTML" %}
```markup
<div class="flex-container">
  <!-- body content -->
</div>
```
{% endtab %}

{% tab title="CSS" %}
```css
.flex-container {
  /* This defines a flex container; inline or block depending 
on the given value it enables a flex context for all its 
  direct children. */
  display: flex; /* or inline-flex */
  
  /* This establishes the main-axis, thus defining the 
  direction flex items are placed in the flex container. 
  Flexbox is (aside from optional wrapping) a single-direction 
  layout concept. Think of flex items as primarily laying out 
  either in horizontal rows or vertical columns. */
  flex-direction: row | row-reverse | column | column-reverse;
  /* row (default): left to right */
  /* row-reverse: right to left */
  /* column: top to bottom */
  /* column-reverse: bottom to top */
  
  /* By default, flex items will all try to fit onto one line. 
  You can change that and allow the items to wrap as needed 
  with this property. */
  flex-wrap: nowrap | wrap | wrap-reverse;
  /* nowrap (default): all flex items will be on one line */
  /* wrap: flex items will wrap onto multiple lines, from top 
  to bottom */
  /* wrap-reverse: flex items will wrap onto multiple lines 
  from bottom to top */
  
  /* This is a shorthand for the flex-direction and flex-wrap 
  properties, which together define the flex container's main 
  and cross axes. The default value is row nowrap. */
  flex-flow: <'flex-direction'> || <'flex-wrap'>
}
```
{% endtab %}
{% endtabs %}

### **Example of Responsive Design with Flexbox**

```css
/* Large */
 .navigation {  
  display: flex; 
  flex-flow: row wrap; 
  /* This aligns items to the end 
  line on main-axis */ 
  justify-content: flex-end; 
}  

/* Medium screens */
 @media all and (max-width: 800px) {  
.navigation {  
  /* When on medium sized screens, 
  we center it by evenly distributing 
  empty space around items */  
  justify-content: space-around;  } 
}
  
/* Small screens */
 @media all and (max-width: 500px) {  
.navigation {  
  /* On small screens, we are no longer 
  using row direction but column */  
  flex-direction: column;  } 
}
```

## **Resources**

* [A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

