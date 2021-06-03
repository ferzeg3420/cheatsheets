# HTML cheatsheet

```
<!-- This is a comment -->
```

```
<!--
Multi-line
comment
-->
```

## Headers 

```
<h1>Biggest header</h1>

<h2>Second biggest header</h2>

<h3>Medium header</h3>

<h4>Small header</h4>

<h5>Smaller header</h4>

<h6>Smallest header</h6>
```

## Paragraph 

```
<p> Normal text i.e. a paragraph. </p>
```

## Special div for main content 

```
<main>
   Same as a div. It is used to help SEO (Search engine optimization)
   and accesibility. The main content of the page (whatever that is) goes here.
</main>
```

## images 

All img elements must have an alt attribute. The text inside an alt
attribute is used for screen readers to improve accessibility and
is displayed if the image fails to load.

Note: If the image is purely decorative, using an empty alt attribute
is a best practice. alt=""

```
<!-- just an image -->
<img src="https://upload.wikimedia.org/wikipedia/commons/2/21/Northsea-eckwarderh%C3%B6rne_hg.jpg"
      alt="image of a weird looking arch">

<!-- Image with link? -->
<a title="Hannes Grobe, CC BY-SA 4.0 &lt;https://creativecommons.org/licenses/by-sa/4.0&gt;, via Wikimedia Commons" href="https://commons.wikimedia.org/wiki/File:Northsea-eckwarderh%C3%B6rne_hg.jpg">
   <img width="512"
        alt="Northsea-eckwarderhörne hg" 
        src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/21/Northsea-eckwarderh%C3%B6rne_hg.jpg/512px-Northsea-eckwarderh%C3%B6rne_hg.jpg">
</a>
```

## links 

```
<a href="https://freecodecamp.org">this links to freecodecamp.org</a>

<!-- Link to internal sections of a page: -->
<a href="#contacts-header">Contacts</a>
... other stuff...
<h2 id="contacts-header">Contacts</h2>

<!-- Can be nested inside a paragraph tag -->
<p>
  Here's a <a target="_blank" href="http://freecodecamp.org"> link to freecodecamp.org</a> for you to follow.
</p>

<!-- Dead links that take you nowhere -->
 <a href="#">cat photos</a>.

<!-- Links that open a new tab with target="_blank" -->
 <a href="https://freecatphotoapp.com" target="_blank">cat photos</a>.

<!-- image link
Nest your image within an a element. Here's an example:
-->
<a href="#">
   <img src="https://bit.ly/fcc-running-cats" alt="Three kittens running towards the camera.">
</a>
```

## Bullet points 

```
<ul>
  <li>milk</li>
  <li>cheese</li>
</ul>
```


## Enumerated list 

```
<ol>
  <li>Garfield</li>
  <li>Sylvester</li>
</ol>
```


## text field 

```
<input type="text">

<!-- text usually comes with a label: -->

<label for="my-text"></label>
<input type="text" id="my-text">

<!-- text field with a placeholder -->

<input type="text" placeholder="this is placeholder text">
```

## Forms (where you usually nest input fields)

```
<!-- The action URL is the URL that receives the result of the form -->
<form action="/url-where-you-want-to-submit-form-data"></form>

<-- Button -->
<button type="submit">this button submits the form</button>

<!-- Require users to provide the correct input for text fields using HTML5 -->

<!-- checks that the text field is not empty -->
<input type="text" required>

<!-- Checks that the text field looks like an email -->
<input type="email" required>

<!-- Checks that the text field is a number and is in the range -->
<input type="number" min="9" max="99" required>

<!-- Radio buttons -->

<form action="https://freecatphotoapp.com/submit-cat-photo">
   <label for="indoor">
      <input id="indoor"
             type="radio"
             name="indoor-outdoor">
      Indoor
   </label>
   <label for="outdoor">
      <input id="outdoor"
             type="radio"
             name="indoor-outdoor">
      Outdoor
   </label>
   <br>
   <button type="submit">
      Submit
   </button>
</form>

<!-- Checkbox -->
<form>
   <label for="loving">
      <input id="loving"
             type="checkbox"
             name="personality">
      Loving
   </label>
   <label for="lazy">
      <input id="lazy"
             type="checkbox"
             name="personality">
      Lazy
   </label>
   <label for="energetic">
      <input id="energetic"
             type="checkbox"
             name="personality">
      Energetic
   </label>
   <button type="submit">
      Submit
   </button>
</form>

<!-- value -->

<!--
When a form gets submitted, the data is sent to the server and includes
entries for the options selected. Inputs of type radio and checkbox report
their values from the value attribute.
-->

<label for="indoor">
   <input id="indoor" 
         value="indoor"
         type="radio"
         name="indoor-outdoor">
      Indoor
</label>

<label for="outdoor">
   <input id="outdoor" 
          value="outdoor"
          type="radio"
          name="indoor-outdoor">
   Outdoor
</label>

<!-- Check radio buttons and checkboxes by default -->

<input type="radio" name="test-name" checked>
```

## Divs

The div element, also known as a division element, is a general purpose container for other elements.

```
<div>Other divs, paragraphs, headers, anything.</div>
```

## Doctype: declaring you're using html:

```
<!DOCTYPE html>
<html>
  <!-- Your HTML code goes here -->
</html>
```

## Head & Shoulders... Ahem, body 

```
<!DOCTYPE html>
<html>
  <head>
    <!-- metadata elements -->
  </head>
  <body>
    <!-- page contents -->
  </body>
</html>
```

## HTML video elements for embedding videos 

```
<video width="320" height="240" controls>
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.ogg" type="video/ogg">
Your browser does not support the video tag.
</video>
```

## iframes to embed other websites like videos from youtube 

```
<iframe width="420" 
        height="315"
        src="https://www.youtube.com/embed/tgbNymZ7vqY">
</iframe>
```

## Different types of text 

- probably better to use a class on a `span` element 
(as of the time of me writing this).

```
<strong>This text is bold</strong>

<u>Underlined text</u>

<em>Italicized text</em>

<s>Strikethrough text</s>
```

## Horizontal line 

```
<hr>
```

## Audio element example 

```
<audio id="meowClip" controls>
  <source src="audio/meow.mp3" type="audio/mpeg" />
  <source src="audio/meow.ogg" type="audio/ogg" />
</audio>
```

## Figure is useful for accesibility 

```
<figure>
  <img src="roundhouseDestruction.jpeg" alt="Photo of Camper Cat executing a roundhouse kick">
  <br>
  <figcaption>
    Master Camper Cat demonstrates proper form of a roundhouse kick.
  </figcaption>
</figure>
```

## Wrapping radio buttons in a fieldset to improve accessibility 

```
<form>
  <fieldset>
    <legend>Choose one of these three items:</legend>
    <input id="one" type="radio" name="items" value="one">
    <label for="one">Choice One</label><br>
    <input id="two" type="radio" name="items" value="two">
    <label for="two">Choice Two</label><br>
    <input id="three" type="radio" name="items" value="three">
    <label for="three">Choice Three</label>
  </fieldset>
</form>
```

## Accesible datepicker 

```
<label for="input1">Enter a date:</label>
<input type="date" id="input1" name="input1">
```

## a datetime attribute to standardize times. 

```
<p>Master Camper Cat officiated the cage match between Goro and
Scorpion <time datetime="2013-02-13">last Wednesday</time>, which
ended in a draw.</p>
```

## HTML offers the accesskey attribute 

to specify a shortcut key to activate or bring focus to an element. 

```
<button accesskey="b">Important Button</button>
```

## Use tabindex to change the order in which tab focuses on elements

```
<div tabindex="1">I get keyboard focus, and I get it first!</div>
<div tabindex="2">I get keyboard focus, and I get it second!</div>
```

## Entities

| Character | Description | Code |
| --- | --- | --- | 
| ` ` | non-breaking space | `&nbsp;` |
| `<` | less than | `&lt;` | 
| `>` | greater than | `&gt;` | 
| `&` | ampersand | `&amp;` |
| `"` | double quotation mark | `&quot;` |
| `'` | single quotation mark (apostrophe) | `&apos;` |
| `¢` | cent | `&cent;` |
| `£` | pound | `&pound;` |
| `¥` | yen | `&yen;` |
| `€` | euro | `&euro;` |
| `©` | copyright | `&copy;` |
| `®` | registered trademark | `&reg;` |
