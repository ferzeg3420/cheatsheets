---
title: CSS
---

# CSS - Cascading Style Sheets

This is for personal use. But ALL the good parts of 
this cheatsheet comes from freecodecamp's web curriculum.
Love those guys.  If you haven't already, [check them
out](https://www.freecodecamp.org)

## inline css 

```
<h2 style="color: blue;">CatPhotoApp</h2>
```

## CSS selector for all h2 elements 

```
<style>
  h2 {
    color: red;
  }
</style>
<h2> Red title </h2>
<h2> Also Red </h2>
```

## CSS selector for all elements that have a certain class 

```
<style>
  .blue-text { //The period "." before a selector means the selector is a class
    color: blue;
  }
</style>
<h2 class="blue-text"> Blue text title using a class.</h2>
<h3 class="blue-text"> Also Blue.</h3>
```

## CSS selector for the element with an id (all ids should be unique)

```
<style>
  #some-id { //The pound sign "#" before a selector means the selector is an id
    color: cyan;
  }
</style>
<h3 id="some-id"> Cyan text title using an id. </h2>
```

### Font size

```
h1 {
  font-size: 30px; // changing the font size.
}
```

### Font family

```
h2 {
  font-family: sans-serif;
  font-family: monospace;
}
```

### Specify how fonts should degrade in case a font is not available.

```
p {
  font-family: Helvetica, sans-serif; // If Helvetica isn't available,
                                      // then use sans-serif
}
```

### Sizing images

```
.larger-image {
   width: 500px;
}
```

### Borders

```
.thin-red-border {
   border-width: 5px;
   border-style: solid;
   border-color: red;
}
```

### One-liner border (order is meaningful):

```
.thick-blue-border {
   border: 12px solid blue;
}
```

### round the borders. 50% is a completely round border.

```
.round-border {
   border-radius: 10px;
}
```

### Background color for something like a div.

```
.green-background {
  background-color: green;
}
```

### Padding

```
An element's padding controls the amount of space between the element's
content and its border.

.yellow-box {
   background-color: yellow;
   padding: 10px;
}
```

### Margin

```
An element's margin controls the amount of space between an element's
border and surrounding elements. Negative margins make the object
larger.

.blue-box {
   background-color: blue;
   color: #fff;
   padding: 20px;
   margin: 10px;
}
```

### Padding from different directions

```
.red-box {
   background-color: crimson;
   color: #fff;
   padding-top: 40px;
   padding-right: 20px;
   padding-bottom: 20px;
   padding-left: 40px;
}
```

### Margins

```
.red-box {
   background-color: crimson;
   color: #fff;
   margin-top: 40px;
   margin-right: 20px;
   margin-bottom: 20px;
   margin-left: 40px;
}
```

### One-liner for the padding. 

It goes clockwise starting from the top.  So top is 10px, right is
20px, bottom is 10px, and left is 20px in the following example.

```
.blue-box {
   background-color: blue;
   color: #fff;
   padding: 10px 20px 10px 20px;
}
```

## One-liner for the margin. 

It goes clockwise starting from the top. 
So top is 10px, right is 20px, bottom is 10px, and left is 20px in the
following example.

```
.blue-box {
   background-color: blue;
   color: #fff;
   margin: 10px 20px 10px 20px;
}
```

## Attribute Selector. 

This selector matches and styles elements with a specific attribute
value.

```
[type='radio'] {
  margin: 20px 0px 20px 0px;
}
```

## Relative units

Relative units, such as em or rem, are relative to another length value. 
For example, em is based on the size of an element's font. If you use 
it to set the font-size property itself, it's relative to the parent's 
font-size.

## The Body

Every HTML page has this as the main part where the markup goes. All other
elements are nested within it, so its styling affects the entire page.

```
body {
  background-color: black;
}
```

## Overriding styles

Overriding styles works like this: The latest in the `<style tag>` is 
the one that will be applied as a tie breaker when two stylings apply. 
Inline styling has higher precedence than that in the `<style section>` 
Marking a style with the importnat keyword in CSS makes it higher precedence.

```
.pink-text {
   color: pink  !important;
}
```

## Hex

Hex (hexadecimal notation) to get specific colors

```
body {
  color: #000000;
}
```

## RGB 

RGB function to generate colors

```
body {
  background-color: rgb(255, 165, 0);
}
```

## CSS variables start with --

```
.penguin {
   --penguin-skin: black;
   --penguin-belly: gray;
   --penguin-beak: yellow;
 
   position: relative;
   margin: auto;
   display: block;
   margin-top: 5%;
   width: 300px;
   height: 300px;
}
```

## CSS variables can be reference with the var function.

```
.penguin-top {
   top: 10%;
   left: 25%;
   background: gray; // It's good to have this here as an extra safety fallback.
   background: var(--penguin-skin, gray);// the , gray is a fallback value.
   width: 50%;
   height: 45%;
   border-radius: 70% 70% 60% 60%;
}
```


## The root

:root is a pseudo-class selector that matches the root element of the 
document, usually the html element. By creating your variables in :root, 
they will be available globally and can be accessed from any other selector 
in the style sheet.

```
:root {
   --penguin-belly: pink;
}
```

## Media query for screens smaller than a certain number of pixels.

```
@media (max-width: 350px) {
   :root {
      --penguin-size: 200px;
      --penguin-skin: black;
   }
}
```

## Text-align property to... well... align text.

```
.justify-text {
   text-align: justify;
}

.center-text {
   text-align: center;
}

.right-text { // scoot text to the right
   text-align: right;
}

.left-text {
   text-align: left; // scoot text to the left 
}
```

## Adjust the size of an image

```
img {
  width: 220px;
}

img {
  height: 20px;
}
```

## Shadow to a card

```
#thumbnail {
  box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
  /*
  offset-x (how fat to push the shadow horizontally from the left)
  offset-y (how far to push the shadow vertically from the element)
  blur-radius 
  spread-radius
  color
  //Multiple shadows can be created using "," commas
  */
}
```

## RGBA: Opacity, not Gameboy Advance

RGB plus A. A is the level of opacity. They called it alpha to be
obtuse.  Yes that's not a mistake, but the word abstruse applies
too. Notice, I'm not saying that the implementation of alpha channels
doesn't deserve credit, just that the name doesn't mean anything to 
most people.

```
h4 {
   background-color: rgba(45, 45, 45, 0.1);
}
```

## Opacity

Change the opacity. Make things more transparent by choosing a number
close to 0. More opaque is closer to 1.

```
.links {
  opacity: 0.7;
}

h4 {
   text-transform: uppercase;
   text-transform: capitalize;
   text-transform: lowercase;
   text-transform: initial;
   text-transform: inherit; // use the text-transform from parent element
   text-transform: none; // use the original text
}
```

## Change the space between lines

```
p {
   font-size: 16px;
   line-height: 25px;
}
```

## Change the color of an a tag when it's hovered over.

```
a:hover {
  color: blue;
}
```

## Reposition things

```
h1 {
   position: relative;
   top: 15px;
}

h2 {
   position: relative;
   bottom: 15px;
}

h3 {
   position: relative;
   left: 15px;
}

h4 {
   position: relative;
   right: 15px;
}
```

## Absolute Position

The next option for the CSS position property is absolute, which 
locks the element in place relative to its parent container. 
Unlike the relative position, this removes the element from the normal 
flow of the document, so surrounding items ignore it.

```
#searchbar {
   position: absolute;
   top: 50px;
   right: 50px;
}

section {
   position: absolute;
   bottom: 50px;
   left: 50px;
}
```

## Fixed position 

the fixed position is a type of absolute positioning that 
locks an element relative to the browser window. Similar to 
absolute positioning, it's used with the CSS offset properties 
and also removes the element from the normal flow of the document. 

```
#navbar {
   position: fixed;
   left: 0px;
   top: 0px;
   width: 100%;
   background-color: #767676;
}
```

# Float, not the Decimal Kind 

The float property is used so that floating elements are removed from the 
normal flow of a document and pushed to either the left or right of their 
containing parent element. It's commonly used with the width property to 
specify how much horizontal space the floated element requires.

```
#left {
   float: left;
   width: 50%;
}

#right {
   float: right;
   width: 40%;
}
```

## Z-index

Change the Position of Overlapping Elements with the z-index Property.

```
.first {
   background-color: red;
   position: absolute;
   z-index: 2;
}

.second {
   background-color: blue;
   position: absolute;
   left: 40px;
   top: 50px;
   z-index: 1;
}
```

## Margin to Center Things

Center an Element Horizontally Using the margin Property

```
centered {
   background-color: blue;
   height: 100px;
   width: 100px;
   margin: auto;
}
```

## HSL: Hue, saturation, and lightness.

```
.blue {
   background-color: hsl(240, 100%, 50%);
}
```

## Linear Gradient

Create a Gradual CSS Linear Gradient. This is the syntax: background:
linear-gradient(gradient\_direction, color 1, color 2, ...);

```
div {
    background: linear-gradient(90deg, red, yellow, rgb(204, 204, 255));
}
```

## Repeating gradient

The repeating-linear-gradient() function is very similar to 
linear-gradient() with the major difference that it repeats 
the specified gradient pattern.

```
div {
   background:
      repeating-linear-gradient( 90deg,
                                 yellow 0px,
                                 blue 40px,
                                 green 40px,
                                 red 80px);
}
```

## Background images using url()

```
body {
   background: url(https://cdn-media-1.freecodecamp.org/imgr/MJAkxbh.png);
}
```

## Transfrom: scale

```
Use the CSS Transform scale Property to Change the Size of an Element.

p {
  transform: scale(2);
}
```

## Scale on hover

Use the CSS Transform scale Property to Scale an Element on Hover.

```
p:hover {
   transform: scale(2.1);
}
```

## Transform: skewX

Use the CSS Transform Property skewX to Skew an Element Along the X-Axis.

```
p {
   transform: skewX(-32deg);
}
```

## Transform: skewY

Use the CSS Transform Property skewY to Skew an Element Along the Y-Axis.

```
#top {
   background-color: red;
   transform: skewY(-10deg);
}
```

## Keyframes

Learn How the CSS @keyframes and animation Properties Work.

```
#rect {
   animation-name: rainbow;
   animation-duration: 4s;
}

@keyframes rainbow {
   0% {
     background-color: blue;
   }
   50% {
     background-color: green;
   }
   100% {
     background-color: yellow;
   }
}
```

## Button color on hover

You can use CSS @keyframes to change the color of a button in its
hover state.

```
button:hover {
  animation-name: background-color;
  animation-duration: 500ms;
}
@keyframes background-color {
  100% {
    background-color: #4791d0;
  }
}
```

## Fill mode for animation

Modify Fill Mode of an Animation setting the animation-fill-mode
property to forwards specifies the style applied to an element when
the animation has finished.

```
button {
   border-radius: 5px;
   color: white;
   background-color: #0F5897;
   padding: 5px 10px 8px 10px;
}
button:hover {
   animation-name: background-color;
   animation-duration: 500ms;
   animation-fill-mode: forwards;
}
@keyframes background-color {
   100% {
      background-color: #4791d0;
   }
}
```

## Create Movement Using CSS Animations

```
@keyframes rainbow {
  0% {
    background-color: blue;
    top: 0px;
  }
  50% {
    background-color: green;
    top: 50px;
  }
  100% {
    background-color: yellow;
    top: 0px;
  }
}
```

## Create Visual Direction by Fading an Element from Left to Right.

```
#ball {
  width: 70px;
  height: 70px;
  margin: 50px auto;
  position: fixed;
  left: 20%;
  border-radius: 50%;
  background: linear-gradient(
    35deg,
    #ccffff,
    #ffcccc
  );
  animation-name: fade;
  animation-duration: 3s;
}

@keyframes fade {
  50% {
    left: 60%;
    opacity: 0.1;
  }
}
```


## Animate Elements Continually Using an Infinite Animation Count

```
#ball {
  width: 100px;
  height: 100px;
  margin: 50px auto;
  position: relative;
  border-radius: 50%;
  background: linear-gradient(
    35deg,
    #ccffff,
    #ffcccc
  );
  animation-name: bounce;
  animation-duration: 1s;
  animation-iteration-count: infinite; // <<<------ HERE
}

@keyframes bounce{
  0% {
    top: 0px;
  }
  50% {
    top: 249px;
    width: 130px;
    height: 70px;
  }
  100% {
    top: 0px;
  }
}
```

## Change Animation Timing with Keywords

```
#ball1 {
  left:27%;
  animation-timing-function:linear;
}
#ball2 {
  left:56%;
  animation-timing-function: ease-out;
}
#ball3 {
  left:76%;
  animation-timing-function: ease-in;
}
```

## Bezier Curves for animation movement rates.

In the example below, the x and y values are equivalent for each point (x1 = 0.25 = y1 and x2 = 0.75 = y2), which if you remember from geometry class, results in a line that extends from the origin to point (1, 1).

```
#ball1 {
   left: 27%;
   animation-timing-function: cubic-bezier(0.25, 0.25, 0.75, 0.75);
}
```

## more media queries

### Less than or equal to X

a media query that returns the content when the device's width is 
less than or equal to 100px.

```
@media (max-width: 100px) { /* CSS Rules */ }
```

### Greater than or equal to X

and the following media query returns the content when the device's 
height is more than or equal to 350px:

```
@media (min-height: 350px) { /* CSS Rules */ }
```

## Make image keep its aspect ratio

Responsive images. The max-width of 100% will make sure the image is 
never wider than the container it is in, and the height of auto will 
make the image keep its original aspect ratio.

```
img {
  max-width: 100%;
  height: auto;
}
```

## The four different viewport units are:

- vw (viewport width): 10vw would be 10% of the viewport's width.

- vh (viewport height): 3vh would be 3% of the viewport's height.

- vmin (viewport minimum): 70vmin would be 70% of the viewport's 
smaller dimension (height or width).

- vmax (viewport maximum): 100vmax would be 100% of the viewport's bigger 
dimension (height or width).


## Flex

Placing the CSS property display: flex; on an element allows you to 
use other flex properties to build a responsive page.

```
#box-container {
  height: 500px;
  display:flex;
}
```

### Flex Direction

Flex direction makes it possible to align any children of that
element into rows or columns.  flex-direction can have the following
options:

- row-reverse

- row

- column

- column-reverse

```
#box-container {
   display: flex;
   height: 500px;
   flex-direction: row-reverse;
}
```

## Flex properties:

- Justify-content:

    One of the most commonly used is justify-content: center;, which aligns 
    all the flex items to the center inside the flex container. 

    - flex-start: 

        aligns items to the start of the flex container. For a row,
        this pushes the items to the left of the container. For a column,
        this pushes the items to the top of the container. This is the
        default alignment if no justify-content is specified.

    - flex-end: 

        aligns items to the end of the flex container. For a row, 
        this pushes the items to the right of the container. For a column, this 
        pushes the items to the bottom of the container.

    - space-between:

        aligns items to the center of the main axis, with extra 
        space placed between the items. The first and last items are pushed to 
        the very edge of the flex container. For example, in a row the first 
        item is against the left side of the container, the last item is against 
        the right side of the container, then the remaining space is distributed 
        evenly among the other items.

    - space-around:

        similar to space-between but the first and last items are 
        not locked to the edges of the container, the space is distributed around 
        all the items with a half space on either end of the flex container.

    - space-evenly:

        Distributes space evenly between the flex items with a full 
        space at either end of the flex container

```
#box-container {
   background: gray;
   display: flex;
   height: 500px;
   justify-content: center;
}
```

- The different values available for align-items include:

    - flex-start
        aligns items to the start of the flex container. 
        For rows, this aligns items to the top of the container. For columns, 
        this aligns items to the left of the container.

    - flex-end
        aligns items to the end of the flex container. For rows, 
        this aligns items to the bottom of the container. For columns, 
        this aligns items to the right of the container.

    - center
        align items to the center. For rows, this vertically aligns 
        items (equal space above and below the items). For columns, this 
        horizontally aligns them (equal space to the left and right of the items).

    - stretch
        stretch the items to fill the flex container. For example, 
        rows items are stretched to fill the flex container top-to-bottom. 
        This is the default value if no align-items value is specified.

    - baseline
        align items to their baselines. Baseline is a text concept, 
        think of it as the line that the letters sit on.

```
#box-container {
   background: gray;
   display: flex;
   height: 500px;
   align-items: center;
}
```

## flex-wrap

flex-wrap property tells CSS to wrap items. This means extra items move into a new row or column. The break point of where the wrapping happens depends on the size of the items and the size of the container.

CSS also has options for the direction of the wrap:

nowrap: this is the default setting, and does not wrap items.
wrap: wraps items from left-to-right if they are in a row, or top-to-bottom if they are in a column.
wrap-reverse: wraps items from right-to-left if they are in a row, or bottom-to-top if they are in a column.

```
#box-container {
   background: gray;
   display: flex;
   height: 100%;
   flex-wrap: wrap
}
```

## Flex-shrink

The flex-shrink property. When it's used, it allows an item to shrink 
if the flex container is too small. Items shrink when the width of the 
parent container is smaller than the combined widths of all the flex 
items within it.

```
#box-1 {
   background-color: dodgerblue;
   width: 100%;
   height: 200px;
   flex-shrink: 1;
}

#box-2 {
   background-color: orangered;
   width: 100%;
   height: 200px;
   flex-shrink: 2;
}
```

## The opposite of flex-shrink is the flex-grow property.

```
#box-1 {
   background-color: dodgerblue;
   height: 200px;
   flex-grow: 2;
}
```

## Flex Basis

The flex-basis property specifies the initial size of the item before CSS makes adjustments with flex-shrink or flex-grow.

```
#box-1 {
   background-color: dodgerblue;
   height: 200px;
   flex-basis: 10em;
}
```

## Flexing a bit More

The flex-grow, flex-shrink, and flex-basis properties can all be set 
together by using the flex property.

```
#box-1 {
  background-color: dodgerblue;
  flex: 1 0 10px; // flex-grow of 1, flex-shrink of 0, and a flex-basis of 10px.
  height: 200px;
}
```

## Order

The order property is used to tell CSS the order of how flex items 
appear in the flex container. 

```
#box-1 {
   background-color: dodgerblue;
   order: 2; // <<<---- HERE
   height: 200px;
   width: 200px;
}

#box-2 {
   background-color: orangered;
   order:1; // <<<---- HERE
   height: 200px;
   width: 200px;
}
```

The final property for flex items is align-self. This property
allows you to adjust each item's alignment individually, instead
of setting them all at once.

```
#box-container {
  display: flex;
  height: 500px;
}

#box-1 {
  background-color: dodgerblue;
  align-self: center;
  height: 200px;
  width: 200px;
}

#box-2 {
  background-color: orangered;
  align-self: flex-end;
  height: 200px;
  width: 200px;
}
```

## Grids are grids. LOL

```
.container {
   font-size: 40px;
   width: 100%;
   background: LightGray;
   display:grid; // <<----- HERE
}
```

## Adding two columns with 50px width each.

```
.container {
  display: grid;
  grid-template-columns: 50px 50px;
}
```

Add two rows with grid template rows.

```
.container {
  display: grid;
  grid-template-rows: 50px 50px;
}
```

- fr: sets the column or row to a fraction of the available space,

- auto: sets the column or row to the width or height of its content automatically,

- %: adjusts the column or row to the percent width of its container.

```
.container {
   display: grid;
   grid-template-columns: auto 50px 10% 2fr 1fr;
}
```

## Create a column gap

Create a column gap using grid-column-gap

```
.container {
   display: grid;
   grid-template-columns: 1fr 1fr 1fr;
   grid-template-rows: 1fr 1fr 1fr;
   grid-column-gap: 10px; // <-- HERE
}
```

## Create a row gap

Create a row gap using grid-row-gap.

```
.container {
   display: grid;
   grid-template-columns: 1fr 1fr 1fr;
   grid-template-rows: 1fr 1fr 1fr;
   grid-row-gap: 10px; // <-- HERE
}
```
## grid-gap

grid-gap is a shorthand property for grid-row-gap and grid-column-gap.

```
.container {
   display: grid;
   grid-template-columns: 1fr 1fr 1fr;
   grid-template-rows: 1fr 1fr 1fr;
   grid-gap: 10px 20px; // <-- HERE: row and then column.
}
```

## Grid column property

The grid-column property is meant for use on the grid items themselves.

To control the amount of columns an item will consume, you can use the 
grid-column property in conjunction with the line numbers you want the 
item to start and stop at.

The lines are hypothetical lines that divide the grid elements. Look it up!
Search term: CSS grid layout


```
.item5 {
  background: PaleGreen;
  grid-column: 2 / 4;
}
```

The grid-row property is meant for use on the grid items themselves.

To control the amount of rows an item will consume, you can use the 
grid-row property in conjunction with the line numbers you want the 
item to start and stop at.

The lines are hypothetical lines that divide the grid elements. Look it up!
Search term: CSS grid layout

```
.item5 {
  background: PaleGreen;
  grid-row: 2 / 4;
}
```

## CSS grid 

In CSS Grid, the content of each item is located in a box which is referred to as a cell. You can align the content's position within its cell horizontally using the justify-self property on a grid item. By default, this property has a value of stretch, which will make the content fill the whole width of the cell. This CSS Grid property accepts other values as well:

start: aligns the content at the left of the cell,

center: aligns the content in the center of the cell,

end: aligns the content at the right of the cell.

```
.item2 {
   background: LightSalmon;
   justify-self: center;
}
```

## align-self 

Just as you can align an item horizontally using justify-self,
align-self is way to align an item vertically as well.

```
.item3 {
  background: PaleTurquoise;
  align-self: end;
}
```

## Justify all items in a container

Horizontally Justify all items in a container

```
.container {
   display: grid;
   grid-template-columns: 1fr 1fr 1fr;
   grid-template-rows: 1fr 1fr 1fr;
   grid-gap: 10px;
   justify-items: center;
}
```
## Vertically align all items in a container

```
.container {
   display: grid;
   grid-template-columns: 1fr 1fr 1fr;
   grid-template-rows: 1fr 1fr 1fr;
   grid-gap: 10px;
   align-items: center;
}
```

## Custom name area

You can group cells of your grid together into an area and give the 
area a custom name. Do this by using grid-template-areas on the 
container like this:
(The period makes that cell an empty cell.)

```
.container {
  grid-template-areas:
    "header header header"
    "advert content content"
    "footer footer .";
}
```

## grid-area?

After creating an area's template for your grid container, as 
shown in the previous example, you can place an item in your 
custom area by referencing the name you gave it.

```
.item1 {
  grid-area: header;
}
```

## Grid area 2

The grid-area property you learned in the last example can be 
used in another way. If your grid doesn't have an areas template to 
reference, you can create an area on the fly for an item to be placed 
like this:

```
item1 { grid-area: 1/1/2/4; }

grid-area: horizontal line to start at / vertical line to start at 
           / horizontal line to end at / vertical line to end at;
```

## Reduce repetition with the repeat function

```
.container {
   display: grid;
   grid-template-rows: repeat(100, 50px);
}
```

## Minmax for grids

There's another built-in function to use with grid-template-columns 
and grid-template-rows called minmax. It's used to limit the size 
of items when the grid container changes size.

```
.container {
   display: grid;
   grid-template-columns: 100px minmax(50px, 200px);
}
```

## Auto-fill

Create Flexible Layouts Using auto-fill
The repeat function comes with an option called auto-fill. 
This allows you to automatically insert as many rows or columns of 
your desired size as possible depending on the size of the container. 
You can create flexible layouts when combining auto-fill with 
minmax, like this:

```
.container {
   display: grid;
   grid-template-columns: repeat(auto-fill, minmax(60px, 1fr));
}
```

## Auto-fit

auto-fit works almost identically to auto-fill. The only difference 
is that when the container's size exceeds the size of all the 
items combined, auto-fill keeps inserting empty rows or columns 
and pushes your items to the side, while auto-fit collapses those 
empty rows or columns and stretches your items to fit the size 
of the container.

```
.container {
   display: grid;
   grid-template-columns: repeat(auto-fit, minmax(60px, 1fr));
}
```

## import a google font 

```
<link href="https://fonts.googleapis.com/css?family=Lobster"
      rel="stylesheet"
      type="text/css">
```


## Make div scrollable 

```
.some-class {
  overflow-y: auto;
}
```

## Links 

Change the color and get rid of the underline completely

```
color: salmon;
text-decoration: none;
```

Add the underline

```
text-decoration: underline;
```

Link states:

###  unvisited link 

```
a:link {
  color: red;
}
```

### visited link 

```
a:visited {
  color: green;
}
```

### mouse over link 

```
a:hover {
  color: hotpink;
}
```

### selected link 

```
a:active {
  color: blue;
}
```
