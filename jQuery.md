---
title: jQuery
---

All the credit goes to freecodecamp
All the mistakes are on me

jQuery is one of the many libraries for JavaScript. It is designed to simplify scripting done on the client side. jQuery's most recognizable characteristic is its dollar sign ($) syntax. With it, you can easily manipulate elements, create animations and handle input events.

# To prevent bugs where jQuery is run before the html is rendered

```
<script>
  $(document).ready(function() {
  });
</script>
```

# Make all button elements bounce

```
<script>
  $(document).ready(function() {
    $("button").addClass("animated bounce");
  });
</script>
```

# Make all elements with the class text-primary shake (assume the ready function is being used).

```
$(".text-primary").addClass("animated shake");
```

# Make all elements with the id target6 fade out (assume the ready function is being used).

```
$("#target6").addClass("animated fadeOut")
```

# Delete a class from an element

```
$("#target2").removeClass("btn-default");
```

# Change the css directly

```
$("#target1").css("color", "blue");
```

# Disable a button using non-css props

```
$("button").prop("disabled", true);
```

# Change text inside an element using jquery
```
$("h3").html("<em>jQuery Playground</em>");
```

# Remove an element using jQuery
```
$("#target4").remove();
```

# Move elements using jQuery
Deletes the first argument and puts it at the end of the contents of the second argument

```
$("#target4").appendTo("#left-well");
```

# copy elements using jQuery
Copies first argument and puts the copy at the end of the contents of the second argument

```
$("#target2").clone().appendTo("#right-well");
```

# Target the parent of an html element

```
$("#left-well").parent().css("background-color", "blue")
```

# Target the child of an html element

```
$("#left-well").children().css("color", "blue")
```

# Target a specific child of an html element

```
$(".target:nth-child(3)").addClass("animated bounce");
```

# Target even or odd elements

```
$(".target:odd").addClass("animated shake");

$(".target:even").addClass("animated shake");
```

# Make your entire page hang by a loose hinge and fall down to the nether

```
$("body").addClass("animated hinge");
```


