# Lesson 2 - Intro to CSS

[Mozilla Developer Network (MDN)](https://developer.mozilla.org/en-US/docs/Web/CSS) is a great resource for learning about and referencing CSS. When searching the web for something related to front end technologies, prefix it with 'mdn,' like `mdn font-size`. Avoid w3schools, it's not a very good resource.

[jsbin](http://jsbin.com) is a great way to play around with HTML and CSS and get a live preview of what you are creating.

## What is CSS?

**C**ascading **S**tylesheets **S**heets

* a way to specify styling for HTML elements
* overrides the default styles of the browser

## Where do you put CSS?

### Inline

Usually not the best way, but can be useful.

```
<p style="background-color: yellow; color: red;">Lorem ipsum dolor sit amet...</p>
```

### In a style tag

Also not usually the best way, but can be useful.

In the head of your HTML document:

```
<style>
  p {
    background-color: yellow;
    color: red;
  }
</style>
```

### In a .css file

Arguably, the ideal way to uss CSS. You can link to the file from multiple html documents.

In the head of your HTML document:

```
<link rel="stylesheet" href="style.css">
```

In style.css:

```
p {
  background-color: yellow;
  color: red;
}
```

## Selectors

### tag

* applies to all elements with the specified tag
* only useful for very general styles

html:

```
<p>Lorem ipsum...</p>

<p>Dolor sit amet...</p>
```

css:

```
p {
  styles here...
}
```

### id

* can only be used on one element per page
* an element can only have one ID
* an ID has uses outside of CSS (as an anchor, in javascript)

html:

```
<p id="special">Lorem ipsum...</p>

<p id="cant-also-be-special">Dolor sit amet...</p>
```

css:

```
#special {
  styles here...
}

#cant-also-be-special {
  styles here...
}
```

### class

* can be used on multiple elements
* an element can have multiple space-delimited classes
* recommended that you primarily use classes to style elements
* classes have uses outside of CSS (in javascript)

html:

```
<p class="sorta-special very-flexible">Lorem ipsum...</p>

<p class="sorta-special recommended">Dolor sit amet...</p>
```

css:

```
.sorta-special {
  styles here...
}

.very-flexible {
  styles here...
}

.recommended {
  styles here...
}
```

## Rules

This is a non-exhaustive list just to get you started.

- color
- background-color
- font-size
- border-style
- border-width
- border-color
- text-decoration
- text-transform
- display
- visibility
- opacity


Check these out on [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference) and learn what properties can be applied to them. Take a look at all the others, but don't worry too much about them for now.

Play around with them on jsbin to see what they do and how they differ. Try out the differences between display, visibility, and opacity.


## Order matters

Given the same selector, rules farther down in source order take precedence. 

Given:

```
p {
  color: red;
}

p {
  color: blue;
}
```

p tags would be colored blue

## Location matters

An inline style takes precedence over a rule in a stylesheet or a style tag.


Given:

```
<style>
p {
  color: green;
}
</style>

<p style="color: purple;">Lorem ipsum...</p>
```

that particular <p> tag would be colored purple

## Cascading

A number of CSS rules cascade down to elements nested within them.

html:

```
<div>
  <p>Lorem ipsum <em>dolor</em> sit amet...</p>
</div>
```

css:

```
div {
  font-size: 12px;
}
```

The text in the <p> tag and the <em> tag will be 12px because the style cascades (is inherited) from the div.

Some rules don't cascade.

css:

```
div {
  border-style: solid;
}
```

There will be a border around the <div>, but not around the <p> tag or the <em> tag, because borders do not cascade. 

