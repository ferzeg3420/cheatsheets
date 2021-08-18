---
title: Bootstrap
---

# Bootstrap Basics

## Add Bootstrap

Add a link tag that looks like the ones from the [official
site](https://getbootstrap.com/) to the head of your html.

## Bootstrap requires that all the body elements be nested inside
a div with class container-fluid

```
<div class="container-fluid">
  <h1>All of your body elements </h1>
</div>
```

## Make an image responsive

```
<img class="img-responsive" 
     src="https://bit.ly/fcc-relaxing-cat" 
     alt="A cute orange cat lying on its back.">
```

## Center text

```
<h2 class="red-text text-center">your centered text</h2>
```

## Create a button

```
<button class="btn btn-default">
  Like
</button>
```

### Make an full-width button

```
<button class="butn btn-default btn-block">
  Submit
</button>
```

### Button colors

```
<!-- White -->
<button class="butn btn-default btn-block">
  Default 
</button>

<!-- Dark blue -->
<button class="butn btn-primary btn-block">
  Primary 
</button>

<!-- Dark Grey -->
<button class="btn btn-secondary">
  Secondary
</button>

<!-- Dark Green -->
<button class="btn btn-success">
  Success
</button>

<!-- Dark Red -->
<button class="btn btn-danger">
  Danger
</button>

<!-- Dark Yellow -->
<button class="btn btn-warning">
  Warning
</button>

<!-- Cyan/Turquoise -->
<button class="btn btn-info">
  Info
</button>

<!-- Light Grey -->
<button class="btn btn-light">
  Light
</button>

<!-- Very dark grey AKA black-->
<button class="btn btn-dark">
  Dark
</button>
```

## Grids

Options: col-md-* col-xs-*
md is medium 
xs is extra small (for small mobile phones)
Bootstrap uses a responsive 12-column grid system, which makes it
easy to put elements into rows and specify each element's relative
width.

```
<div class="row">
  <div class="col-xs-4">
    <button class="btn btn-block btn-primary">Like</button>
  </div>
  <div class="col-xs-4">
    <button class="btn btn-block btn-info">Info</button>
  </div>
  <div class="col-xs-4">
    <button class="btn btn-block btn-danger">Delete</button>
  </div>
</div>
```

### Heading example:

```
<div class="row">
  <div class="col-xs-8">
    <h2 class="text-primary text-center">CatPhotoApp</h2>
  </div>
  <div class="col-xs-4">
    <a href="#">
      <img class="img-responsive thick-green-border"
           src="https://bit.ly/fcc-relaxing-cat"
           alt="A cute orange cat lying on its back.">
    </a>
  </div>
</div>
```

### Form radio buttons and checkboxes example:

```
<div class="row">
  <div class="col-xs-6">
    <label><input type="radio" name="indoor-outdoor"> Indoor</label>
  </div>
  <div class="col-xs-6">
    <label><input type="radio" name="indoor-outdoor"> Outdoor</label>
  </div>
</div>
<div class="row">
  <div class="col-xs-4">
    <label><input type="checkbox" name="personality"> Loving</label>
  </div>
  <div class="col-xs-4">
    <label><input type="checkbox" name="personality"> Lazy</label>
  </div>
  <div class="col-xs-4">
    <label><input type="checkbox" name="personality"> Crazy</label>
  </div>
</div>
```

## Color text

```
<h2 class="text-primary text-center">Dark blue text, centered</h2>

<h2 class="text-secondary text-center">Dark grey text, centered</h2>

<h2 class="text-success text-center">Dark green text, centered</h2>

<h2 class="text-danger text-center">Dark red text, centered</h2>

<h2 class="text-warning text-center">Dark yellow text, centered</h2>

<h2 class="text-light text-center">Light grey text, centered</h2>

<h2 class="text-info text-center">Turquoise/cyan text, centered</h2>

<h2 class="text-dark text-center">Black text, centered</h2>
```

## Spans

By using the inline span element, you can put several elements on
the same line, and even style different parts of the same line
differently.

```
<p>
  Top 3 things cats <span class="text-danger">hate:</span>
</p>
```

## Font awesome link

Get an updated one from the [official fontawesome website](https://fontawesome.com/start).

## Add an icon

```
<i class="fas fa-info-circle"></i>
```

## Prettier form controls

All textual `<input>`, `<textarea>`, and `<select>` elements with the
class .form-control have a width of 100%.

```
<input class="form-control"
       type="text"
       placeholder="cat photo URL"
       required>
```

## Wells

```
<div class="well">
  A box that has a shadow such that it gives the box a little depth.
</div>
```
