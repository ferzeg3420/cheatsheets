Sass, or "Syntactically Awesome StyleSheets", is a language extension of CSS. It adds features that aren't available using basic CSS syntax. Sass makes it easier for developers to simplify and maintain the style sheets for their projects.

Sass can extend the CSS language because it is a preprocessor. It takes code written using Sass syntax, and converts it into basic CSS. This allows you to create variables, nest CSS rules into others, and import other Sass files, among other things. The result is more compact, easier to read code.

There are two syntaxes available for Sass. The first, known as SCSS (Sass CSS), is an extension of the syntax of CSS. This means that every valid CSS stylesheet is a valid SCSS file with the same meaning. Files using this syntax have the .scss extension.

The second and older syntax, known as the indented syntax (or sometimes just "Sass"), uses indentation rather than brackets to indicate nesting of selectors, and newlines rather than semicolons to separate properties. Files using this syntax have the .sass extension.

Vendor prefixes are features implemented by specific browsers

# Variables 

## To declare variables:

```
$main-fonts: Arial, sans-serif;
$headings-color: green;
```

## To use variables:
```
h1 {
  font-family: $main-fonts;
  color: $headings-color;
}
```

# Nest css with Sass 

## Instead of:
```
nav {
  background-color: red;
}
nav ul {
  list-style: none;
}
nav ul li {
  display: inline-block;
}
```
## One can do:
```
nav {
  background-color: red;
  ul {
    list-style: none;
    li {
      display: inline-block;
    }
  }
}
```

# Mixins are is like pasting with arguments 

```
@mixin box-shadow($x, $y, $blur, $c){ 
  -webkit-box-shadow: $x $y $blur $c;
  -moz-box-shadow: $x $y $blur $c;
  -ms-box-shadow: $x $y $blur $c;
  box-shadow: $x $y $blur $c;
}
```
## Using the mixin:
```
div {
  @include box-shadow(0px, 0px, 4px, #fff);
}
```

# Logic for your mixins: if, else if, else; conditionals 
```
@mixin text-effect($val) {
  @if $val == danger {
    color: red;
  }
  @else if $val == alert {
    color: yellow;
  }
  @else if $val == success {
    color: green;
  }
  @else {
    color: black;
  }
}
```

# For Loops 

## 1,2,...,12 last is inclusive.
```
@for $i from 1 through 12 {
  .col-#{$i} { width: 100%/12 * $i; }
  /* #{$i} is syntax to convert an int to a string */
}
```
## 1,2,...,11 last is not inclusive.
```
@for $i from 1 through 12 {
  .col-#{$i} { width: 100%/12 * $i; }
}
```

# For each loop 

```
@each $color in blue, red, green {
  .#{$color}-text {color: $color;}
}
```

## Using a map
```
$colors: (color1: blue, color2: red, color3: green);
@each $key, $color in $colors {
  .#{$color}-text {color: $color;}
}
```
## $key gets rid of the keys

# While loop 

```
$x: 1;
@while $x < 13 {
  .col-#{$x} { width: 100%/12 * $x;}
  $x: $x + 1;
}
```

# Partials in Sass are separate files that hold segments of CSS code. 

Names for partials start with the underscore (_) character, which
tells Sass it is a small segment of CSS and not to convert it into
a CSS file.  so we may create a file called _mixins.scss and add
some mixins in there

## Then to import to our main.scss file (no need for the extension or underscore):
```
@import 'mixins'
```

# Inherit all the properties from another class 

```
.panel{
  background-color: red;
  height: 70px;
  border: 2px solid green;
}
.big-panel{
  @extend .panel;
  width: 150px;
  font-size: 2em;
}
```
