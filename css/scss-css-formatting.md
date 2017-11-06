# CSS/SCSS Formatting
As stated previously we ensure all CSS is actually written in SCSS, being careful when and where to nest our style elements.

##  Classes, IDs &amp; SCSS Variables.

####  IDs
**DO NOT** use `id` for styling purposes. Acceptable uses for `id` include:

* JavaScript selection - prefix these with `js-` to indicate they are for JavaScript only
* Assigning form labels to inputs
* Jump links between sections of a page

```html
<div class="js-camel-case" id="js-camelCase"> ... </div>
```

```html
<label for="firstName">First Name</label>
<input type="text" id="firstName" class="form-cotrol" />
```

```html
<a href="#mainContent">Skip to Main Content</a>

...

<div class="content" id="mainContent"> ... </div>
```

#### SCSS Variables
Like IDs use camelCase for SCSS Variable names:
````scss
$fontDefault: 'Helvetica', sans-serif;
$darkGray: #333;
$red: #F00;
````

#### Classes
Use dashes **-** **NOT** undescores **_** in class names.
```html
<div class="camel-case"> ... </div>
<div class="js-camel-case"> ... </div>
```

##### Class Naming Quality

Class names should be specific enough so that you can comprehend the name without context, but generic enough for reuse throughout the code base.

```scss
.post-card {}
.kamino {}
.container {}
.btn {}
.icn {}
```

## Name Delimiters
For more information on our naming conventions and structures please visit our [CSS](css/css.md) page. Alternatively read our [methodology](general/methodology.md).

#### Base Elements (Molecules)c
````scss
.post-card {
    position: relative;
    padding: 10px;
    border: 1px solid black;
}
````
#### Sub Componenets

Use a hyphen before a class member (sub-component) name, prefixed with the base class name. Ensure it is nested as these sub-components are only used within their base element blocks.

````scss
.post-card {
    padding: 10px;
    position: relative;
    
    .post-header {
        margin-bottom: 10px;
    }
    
    .post-body {
        margin-bottom: 10px;
    }
    
    .post-footer {
        border-top: 1px solid black;
    }
}
````

### Modifiers

If a modifier needs to be created. i.e a background modifier. New button modifier etc. Please note we at times append ``!important`` to ensure it is style used.

'bg' is the shorthand for background when used for class names.
````scss
.bg-black {
    background-color: black !important;
}
````
'bt' is the shorthand for button when used for class names.
````scss
.btn-black {
    background-color: black !important;
}
````
## Brackets
Place the opening curly-bracket of each rule block on the same line as the last selector.

Place the closing curly-bracket of each rule block on its own line after the final property of the rule block.
````scss
.selector {
    color: white;
    font-family: 'Helvetica', sans-serif;
}
````
## Indentation
We use the google css standards for spacing: 
````
Tab Size = 2
Indent = 2
Continuation Indent = 2
````

##  Property Whitespace

Put each property on its own line.

Follow each property with a colon and a single space.

```scss
.selector {
    color: #ff0000;
    font-family: 'Helvetica', sans-serif;
}
```

##  Semi-colons

Follow each property value with a semi-colon.

```scss
.selector {
    color: #ff0000;
    font-family: 'Helvetica', sans-serif;
}
```

## Trailing Whitespaces
Remove all trailing whitespace.

##  Rule Block Separation

Separate each rule block by an empty line.

```scss
.selector {
    color: #ff0000;
    font-family: 'Helvetica', sans-serif;
}

.selector {
    color: #ff0000;
    font-family: 'Helvetica', sans-serif;
    
}
```

##  Property Order

CSS properties should be grouped by commonality (display, then box-model, then positioning, then background/color, then typography, then misc/etc).

```scss
.selector {
    display: block;
    width: 400px;
    height: 222px;
    padding: 4px;
    margin: 2px;
    position: absolute;
    top: 22px;
    left: -12px;
    color: #ffffff;
    font-family: 'Helvetica', sans-serif;
    text-transform: uppercase;
    text-indent: 0;
}
```

##  Vendor Prefixes

As we use a build tool to generate our css, there is no need to vendor-prefix within your SCSS file. This will be done via the compiler. Please take a look at our [Build Tools]() page for more info.

As a rule, we accommodate the latest 2 browser versions, we do not support below IE 10. 

Use resources like <http://caniuse.com/> to see whether features can be used, and in what browser.

##  Quotes

Use single quotes.

**File Paths and Data URIs**

Use single quotes for file paths and data URIs.

```css
.selector {
    background-image: url('background.png');
}
```

**Font Family**

Use single quotes for font names unless they are system fonts that don't require them.

```css
.selector {
    font-family: 'LeagueGothic', Helvetica, Arial, sans-serif;
}
```

**Generated Content**

Use single quotes around generated content values.

```css
.selector:before {
    content: 'Chapter:';
    display: inline;
}
```

**Attribute Selectors**

Use single quotes around values in attribute selectors.

```css
input[type='text'] {
    color: #ff0000;
}
```

##  Multiple Selectors

Separate multiple selectors in the same rule block with a comma and place each selector on a new line.

```css
.selector:focus,
.selector:active {
    color: #ff0000;
    font-family: Times, 'Times New Roman', serif;
}
```

##  Comments & Grouping

Group related rule blocks by base object using the standardized section comment style.

```css
/* ---------------------------------------------------------------------
Post
------------------------------------------------------------------------ */

.post-card {
    padding: 20px;
    background-color: #ccc;
}
```

If a section requires additional subsets of comments, a single line comment is acceptable.

If a property / value pair needs additional clarity or is not self-documenting, add comments on the same line immediately following the value.

```scss
/* ---------------------------------------------------------------------
Horizontal List
------------------------------------------------------------------------ */
.list-horiz {
    overflow: hidden;
}

.list-horiz > * { float: left; }
```

```scss
.carousel {
    position: relative; /* A positioning reference for .carousel-nav */
}

.carousel-nav {
    position: absolute; /* Positioned against .carousel base class */
    right: 20px;
    bottom: 20px;
    z-index: 10; /* Pull navigation on top of .carousel-slides */
}
```

##  Hexadecimal Notation

Use three characters and lowercase hexadecimal notation where you can. We se SCSS so define variables once then reuse through documents.

```css
.selector {
    background-color: #f00;
}
```
##  TODO Comments

Mark todos and action items with a comment that includes `TODO`. Be sure that `TODO` is always uppercase.

```css
/* TODO - Review content styles */
.selector {
    color: #ff0000;
}
```
## Contextual Selectors

Avoid cross module contextual selection.

```css
/* DO NOT */
.selector .hrz { 

}
```

If a single module can make use of a contextual selector (as the markup structure is known), be sure to apply it with the proper depth of applicability.

```css
.list > li { }
```

## Selector Specificity

Keep selector specificity as low as possible, opting for a single class as the best selector.

```css
.selector {
    padding: 20px;
    background-color: #ccc;
}
```

**Resources**

* <http://www.w3.org/TR/css3-selectors/#specificity>
* <http://www.stuffandnonsense.co.uk/archives/css_specificity_wars.html>
* <http://css-tricks.com/specifics-on-css-specificity/>
* <http://www.standardista.com/css3/css-specificity/>

## Shorthand

Use of shorthand is encouraged unless setting a single value.

When using shorthand, be explicit and define all values.

```css
.selector {
    margin: 12px 0 16px 0;
}
```

## Units

We will work with 3 units of measure being pixels, rem's and percentages. These units of measure will be used in different ways as outlined below.

**PLEASE NOTE:** The body font size will be in pixels all other font sizes will be in rem's.

The body font size should be in **pixels**.
```scss
html {
    font-size: 16px;
}
```

All font sizes thereafter should be in rem's. 1rem being equal to 16px.

```css
.my-title {
    font-size: 1rem;
}
```

Spacing should be done primarily using pixels.
```scss
.mt-10 {
    margin-top: 10px;
}
```

However if using Bootstrap 4, you have the option of using rem's for more information visit the [Bootstrap 4 documentation](https://getbootstrap.com/docs/4.0/utilities/spacing/).

... Assuming the root font size is 16px.

```scss
mt-1 {
    margin-top: .25rem; // 4px.
}

.mt-2 {
    margin-top: .5rem; // 8px
} 

.mt-3 {
    margin-top: 1rem; // Default value (16px)
}
```
Whichever unit of measure chosen be sure to stick to using it throughout the project to not confuse future people working on the project.

Container and Block sizing
```scss
.element-block {
    width: 25%;
    margin-bottom: 10px;
}
```

## Line-Heights

Declare line-height values as unit-less. Unit-less line heights act as a multiplier to the text size for a given element.

```scss
.selector {
    font-size: 16px;
    line-height: 1.5;
}
```

## Color Values

Use hexadecimal notation for color values. RGBA is acceptable if opacity is needed, but be sure to provide a fallback for browsers that don't support RGBA.

```css
.selector {
    color: #ff0000;
}

.selector {
    color: #ff0000; /* fallback for non-rgba browsers */
    color: rgba(255, 0, 0, 0.8);
}
```