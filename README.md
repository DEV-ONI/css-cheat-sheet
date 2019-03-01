# css-cheat-sheet
So it begins. My cheat sheet for CSS.

### Regards & learning materials
I was inspired and finally motivated to learn CSS because of [iamshaunjp](https://github.com/iamshaunjp) aka [The Net Ninja](https://www.youtube.com/channel/UCW5YeuERMmlnqo4oq8vwUpg) and his fantastic tutorials.

### HTML elements
* block elements - always starts on a new line and takes up the whole block (div, fieldset, form, footer, h1-h6, header, li, nav, ol, p, table, ul, video)
* inline elements - do not start on a new line and only take up as much width as necessary (a, button, i, img, input, label, span, strong, textarea). Margin top and botton won't be applied to them because the box model isn't working for inline elements. If we want them to be treated as block elements, we have to give them the ```display: block``` profull width availableperty. If we want them to be treated like blocked AND inline element, we should give the m ```display: inline-block```

### Terminology 
* descendants - children + grandchildren + ... of
* children - only first level
* inheritance - inherits the style from the parent element (the ```inherit``` value)

### Important tips
* the browser is "reading" the CSS from top to bottom (cascade) - two identical selectors with different properties, the bottom one will win
* if some font families have 2 words, we need to put them in quote marks

### Selectors
* ```#container``` - ID selector
* ```.container``` - class selector
* ```span``` - element selector
* ```span, div, p``` - multiple elements selector
* ```#container p``` - select ```p``` that is the descendant of ```#container```
* ```#container > p``` - select ```p``` that is the child od ```#container```
* ```h2 + p``` - adjacent selector, the one that comes directly after the ```h2```
* ```input[type="text"]``` - attribute selector
* ```span:hover``` - dynamic pseudo selector (behavior) - hover, presses, checked etc
* ```ul:nth-child(5)``` - structural pseudo selector (parent-child relationship) - 5th li tag, element without children etc.
* ```*``` - universal selector (mostly used to override default styles)

### Selector specific points
* ID - 100 points
* classes - 10 points
* elements - 1 point
* !important - overrides everything (try not to use this, rather write nice and clean code!)

### The box model
How (block level) elements represent themselves in terms of space.
![The box model](https://s3.amazonaws.com/viking_education/web_development/web_app_eng/css_box_model_chrome.png)
```css
.box {
  margin: 30px 20px 15px 5px; /* top-right-bottom-left */
  padding: 30px;
  border: 1px solid black;
  width: 400px; /* width of the blue box */ 
  height: 200px;
  /* 
    total width will be 522px = 400px + 2*margin + 2*padding + 2*border 
    that means that if we set the width to 100%, it can break through and produce unwanted behavior
    pay attention to collapsing margins - 30px + 30px =/= 60px.
  */ 
}
```

# CSS properties
### Font size
* absolute - px
* relative - em, percentages - used when making responsive design

```css
.container {
  font-size: 12px;
}
article {
  font-size: 14px;
}
article h2 {
  font-size: 2em; /* inherit font size from article and miltiple it by 2 */
}
article p {
  font-size: 50%; /* inherit font size from article and take 50% of size */
}
```

### Font family
Note: some families already exist on user's computer. Remember to use the font family stack for fallbacks.
```css
.container {
  font-family: arial, helvetica, sans-serif; /* if arial is not available, use helvetica etc. */
}
```

### Text decoration
Possible values: ```inerhit|line-through|none|underline|overline|inherit```
```css
.container {
  text-decoration: underline;
}
```

### Font weight
Possible values: ```normal|bold|bolder|lighter|number|initial|inherit```

Note: Bold is same as 700, normal is same as 400. Most font families won't have every possible number value.

Note: some font families don't have certain weights as their options!
```css
.container {
  font-weight: bolder;
}
```

### Text transform
Changing the letter casing.

Possible values: ```none|capitalize|uppercase|lowercase|initial|inherit```
```css
.container {
  text-transform: uppercase;
}
```

### Text color
Changing the color of the text.
```css
 .container {
  color: blue;
  color: #FEFEFE;
 }
```

### Letter spacing and word spacing
Spacing between letters: e.g. s p a c i n g

Spacing between words: e.g. space   between   words

Values mostly in pixels;
```css
.container {
  letter-spacing: 3px;
  word-spacing: 5px;
  letter-spacing: 2em; /* the case with em's is font-size times number of em's */
}
```

### Line height
Vertical space between lines in a paragraph. Not the gap, just the height of the line.

The font size itself is not included, meaning,if you put ```line-height``` to be 12px and the ```font-size``` itself is 12px, nothig will happen.

Possible values: normal|number|length|initial|inherit
```css
.container {
  line-height: 24px;
  line-height: 2em; /* the case with em's is font-size times number of em's */
}
```

### Border style
Mostly used values: solid|none|hidden
```css
.container {
  border: 1px solid black; /* width, style, color */
  border-radius: 10px; /* for rounded corners; it has 4 corners */
  border-radius: 5px 10px 30px 20px; /* different corenrs */
}
```

### Width and height
They Can be static (in pixels) and dynamic (in percentages).
```css
.container {
  height: 100px; /* static height */
  width: 300px; /* static width, no matter how big the browser is */
  width: 70%; /* dynamic, width is 70% of the parent element */
}
.container{
  width: 40%;
  display: inline-block; /* display inline but keep respecting the box model (block elements) */
}
```

### Background
It can be colored or used an image background.
```css
.container {
  width: 500px;
  height: 500px;
  background-color: #606060;
  background-image: url(https:url);
  background-repeat: no-repeat; /* if the image is smaller than the container and we don't want it to repeat */
  background-position: center; /* or we can specify in pixels */
  background-size: 100px; /* if we have an background image, we can resize it */
}
```

### Gradient
Smooth transitions between colors.
Useful links:
* https://uigradients.com
* http://www.gradients.io/
Important: add prefixes like ```-moz-``` and ```-webkit-``` for Mozilla Firefox and other supports.
```css
/* syntax */
background: linear-gradient(direction, color-stop1, color-stop2, ...);
.container {
  background: yellow; /* fallback, if gradient isn't supported in the browser */
  background: linear-gradient(to bottom right, red, yellow);
}
```
