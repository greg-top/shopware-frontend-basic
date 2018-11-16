# Overview

* Less is a CSS preprocessor
* Shopware compiler transforms Less to CSS automatically 
* main Less structure in Shopware:
    * themes/Frontend/Responsive/frontend/_public/src/less/all.less
    * hacks.less - all dirty CSS here (negative margins, important clause)

# How to add less code to custom theme
* go to themes/Frontend/'Your-theme'/frontend/_public/src/less
* create all.less file
* create a tree structure hierarchy for all less files 
* in backend, in theme manager compile custom theme (action depends on dev configuration)

# BEM methodology for styling

### B- Block
* standalone entity that is meaningful on its own, examples:
    * header
    * container
    * menu
    * checkbox
    * input
### E - Element
* A part of a block that has no standalone meaning and is semantically tied to its block, xamples:
    * menu item
    * list item
    * checkbox caption
    * header title
### M - Modifier
* A flag on a block or element. Use them to change appearance or behaviour, examples:
    * disabled
    * highlighted
    * checked
    * fixed
    * size
    * big
    * color yellow
 
 <p>Examle of CSS BEM code:</p>
 <pre>
 .button {              //This is a BLOCK
    display: inline-block;
    border-radius: 3px;
    padding: 7px 12px;
    border: 1px solid #D5D5D5;
    font: 700 13/18px Helvetica, arial;
 }
  </pre>
<pre>
 .button--state-success {     //Modifier (block--modifier-value)
    color: #0F0;
    border-color: #0F0;
 }
 .button--state-danger {...}    //Modifier
</pre>
<pre>
.button__icon {     //Element (block__element)
    color: #FFF;
    ...
    ...
    ...
}
</pre>

<p>More examples of BEM naming</p>
.form {} <br>
.form--theme-xmas {} <br>
.form--simple {} <br>
.form__input {} <br>
.form__submit () <br>
.form__submit--disabled {}

# Responsive Adjustment
* Mobile first principle
    * starting with the smallest layout style
    * scaling of the layout with growing viewport size
    * adjusting the layout at specific device breakpoints
    * breakpoints are set via the **min-width** media query
* Breakpoints
    * Phone (Start) -> min-width: 0;
    * @phoneLandScapeViewPortWidth: 30em; <br>
        -> min-width: 480px;
    * @tabletViewPortWidth: 48em; <br>
        -> min-width: 768px;
    * @tabletLandScapeViewPortWidth: 64em; <br>
        -> min-width: 1024px;
    * @desktopViewPortWidth: 78.75em; <br>
        -> min-width: 1260px;
<p>example:</p>
<pre>
.container {
    padding: 10px;      //mobile portrait view (start)        
}
</pre>
<pre>
@media screen and (min-width: @phoneLandScapeViewPortWidth) {
    padding: 20px;
}
</pre>

# Unitize mixin
* mixin for transforming static **px** units to dynamic **rem** units (Shopware mixin)
* operates all common CSS properties
* it contains additional **px** units for legacy browsers

<p>example</p>
<pre>
#LESS
.container {
    .unitize-padding(15, 10, 25, 10);       //parameters - pixel units
    .unitize-width(250);
    .unitize(font-size, 16);
}
</pre>
<pre>
#CSS
.container {
    padding: 15px 10px 25px 10px;       //legacy for older browsers
    padding: .9375rem .625rem 1.5625rem .625rem;
    ...
    ...
    ...
}
</pre>

# Components and UI elements
* source: https://developers.shopware.com/styletile/

# Responsive images
* use **srcset** attribute to add extra sources for high definition screens
* the **< picture >** element is used to add different sources for other viewport sizes
* Picturefill.js is used as a polyfill for legacy browsers

<p>example</p>
<pre>
< img srcset="product.jpg, product@2x.jpg 2x" alt="">
< picture>
    < source media="(min-width: 64em)"
             srcset="pr-lg.jpg", pr-lg@2x.jpg 2x>
    < source media="(min-width: 48em)"
                 srcset="pr-md.jpg", pr-md@2x.jpg 2x>
    < img srcset="pr-sm.jpg, pr-sm@2x.jpg 2x" alt="">       //mobile view
< /picture>
</pre>