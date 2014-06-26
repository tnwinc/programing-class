# Lesson 3 - Intermediate CSS

## Comments

CSS only has multi-line comments:

```
/*
  this is a comment
*/

/* you can comment out code, and the rules will not be applied */

/*
.foo {
  color: red
}
*/
```

## Reset / Normalize

Browsers implement default styles for elements differently. An H1 in Chrome might be a different font-size than in Firefox and the margin around a p tag might differ between Safari and IE. Instead of fighting with these differences throughout your CSS, it's best to use a strategy that resets or normalizes the styles across browsers at the beginning of your styles.

### Reset

The most common strategy is resetting CSS so that all elements are pretty much the same, removing margins and padding and other styles that are known to differ between browser's default styles.

[http://www.cssreset.com](http://www.cssreset.com) has a number of the most common resets used. When you apply one of these, all elements will have the same font-size and no margin or padding. Lists will not have bullets. If you want those styles back, you have to add them back yourself.

### Normalize

The idea behind normalizing CSS is that you don't wipe out the default browser styles. Instead, you ensure that those styles are consistent between browsers. So, for example, all H1s will have a font-size of 30px and all p tags will have a margin of 10px. This way, if you want a decent default set of styles, you don't have to create them yourself and they'll be the same between browsers.

Check out [normalize.css here](http://necolas.github.io/normalize.css/).

## Selectors

### multiple

To select multiple elements and apply the same styles, separate the selectors with commas:

```
.foo,
.bar {
  background-color: green;
}
```

### descendant

To select elements nested inside another element, use the descendant selector, by separating the ancestor from the descendant with a space:

```
.foo li {
  background-color: blue;
}
```

The above will apply the given styles to any li tags nested under an element with the class 'foo.' The markup could look like this:

```
<ul class="foo">
  <li>Item</li>
  <li>Item</li>
  <li>Item</li>
</ul>
```

or like this:

```
<div class="foo">
  <div>
    <div>
      <ul>
        <li>Item</li>
        <li>Item</li>
        <li>Item</li>
      </ul>
    </div>
  </div>
</div>
```

### universal

The universal selector is a special selector that selects all elements in the given scope.

```
* {
  color: red;
}
```

gives all elements on the page red text.

```
.foo * {
  color: blue;
}
```

gives all elements nested under an element with the class 'foo' blue text.

The is a very powerful selector and can have performance implications, since the browser has to do a lot of work to find all elements on the page. It's also generally not what you want for a given style. It's best to be more specific with your selectors.

### pseudo-selectors

Pseudo-selectors don't select elements, but target an element when it's in a particular state, position, etc.

```
a:hover {
  color: lightblue;
}
```

will make a tags blue when you hover over them.

```
textarea:focus {
  border-color: red;
}
```

will give a textarea a red border when you select it to type into.

```
li:first-child {
  background: green;
}
```

will select the li only if it is the first descendant nested inside of its parent element.

There are many different pseudo-selectors. [This reference on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes) has a list of them.

## Rules

### background-image

Elements can be given a background image that appears behind the element's content.

```
.foo {
  background-image: url('path/to/image.png');
}
```

There are a couple rules specific to background images that can also be applied.

```
.foo {
  background-repeat: repeat;
  background-position: 0 0;
}
```

The rules shown above are the default rules, stating that the background image should repeat in both directions and be positioned 0 pixels from the left, top corner. [Check out MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/background) to view more details.

#### background-image vs img tag

You might wonder when to use an img tag and when to use a background image on an element. The general rule is:

* Use an img tag when the image is part of the content
* Use a background image when the image is decoration/styling

### element dimensions

Elements can have their width and height specified:

```
.foo {
  width: 200px;
  height: 100px;
}
```

The values can also be percentages:

```
.foo {
  width: 50%;
  height: 25%;
}
```

The percentage is relative to the width or height of the element's parent. If the parent is the body, or the parent itself has a flexible width, the width of .foo could change along with the width of the browser. To ensure the element stays within certain constraints, you can specify min and max width and height.

```
.foo {
  width: 50%;
  min-width: 100px;
}
```

.foo will be 50% of its parents width, but won't go smaller than 100px wide.


### margin

Margin specifies the area around an element, separating it from other elements.

```
.foo {
  margin: 20px;
}
```

.foo will be buffered 20px on all sides.

You can also specify margins for specific sides:

```
.foo {
  margin-left: 20px;
}
```

Now .foo will only have a 20px margin on its left side.

#### vertical margins collapse

The vertical margins between elements collapse into each other. So if you have the following markup:

```
<p>Some text...</p>
<p>More text...</p>
```

and the following CSS:

```
p {
  margin: 10px;
}
```

The vertical space between the two paragraphs will be just 10px, not 20px.

Combined with other positioning techniques, this isn't always the case. We'll worry about that later, but for now, it's good to be aware that margin collapsing can happen.

### padding

Padding is similar to margin; it adds space around the element. The difference is that an element's background-color and/or background-image is included in its padding, but not its margin.

```
.foo {
  background-color: red;
  margin: 20px;
  padding: 20px;
}
```

You will see a red background color behind the element and its padding area, but not where the margin is.

## Box Model

Things like an element's width, margin, padding, and border make up its box model. It's important to understand the box model in order to be able to lay elements out in CSS.

I'd recommend reading [this MDN article](https://developer.mozilla.org/en-US/docs/Web/CSS/box_model), checking out some other resources online (search for 'css box model'), and playing around with widths, heights, margins, padding, and borders in jsbin to get a good feel for how the box model works.

### Shorthand rules

Most rules with dashes also have a shorthand syntax. For example, you can specify a background like so:

```
.foo {
  background-image: url('some-image.png');
  background-repeat: no-repeat;
  background-position: 30px 50px;
}
```

or you can use the shorthand to accomplish the same thing:

```
.foo {
  background: url('some-image.png') no-repeat 30px 50px;
}

```

Order doesn't necessarily matter in this case, but the values that should be together need to stay together.

This is valid:

```
.foo {
  background: 30px 50px url('some-image.png') no-repeat;
}
```

but this is not:

```
.foo {
  background: 30px url('some-image.png') no-repeat 50px;
}
```

because the values for background-position need to stay together.

Some rules have multiple shorthand syntaxes depending on how many values you give it:

```
.foo {
  margin: 10px;
}
```

is shorthand for:

```
.foo {
  margin-top: 10px;
  margin-right: 10px;
  margin-bottom: 10px;
  margin-left: 10px;
}
```

```
.foo {
  margin: 10px 20px;
}
```

is shorthand for:

```
.foo {
  margin-top: 10px;
  margin-right: 20px;
  margin-bottom: 10px;
  margin-left: 20px;
}
```

``
.foo {
  margin: 10px 20px 30px;
}
```

is shorthand for:

```
.foo {
  margin-top: 10px;
  margin-right: 20px;
  margin-bottom: 30px;
  margin-left: 20px;
}
```

``
.foo {
  margin: 10px 20px 30px 40px;
}
```

is shorthand for:

```
.foo {
  margin-top: 10px;
  margin-right: 20px;
  margin-bottom: 30px;
  margin-left: 40px;
}
```

The basic rules are:

| 10px | all |
| 10px 20px | vertical horizontal |
| 10px 20px 30px | top horizontal bottom |
| 10px 20px 40px 50px | top right bottom left |
