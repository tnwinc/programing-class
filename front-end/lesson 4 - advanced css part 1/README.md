# Lesson 4 - Advanced CSS Part 1

## Resources

* [CSS Tricks](http://css-tricks.com/)
* [Learn CSS Layout](http://learnlayout.com/)
* [Codecademy](http://www.codecademy.com/)

## Specificity

This is an important concept for understanding which selector wins out when you have multiple that point to the same element(s). [Chris Coyier of CSS Tricks explains it better than I can](http://css-tricks.com/specifics-on-css-specificity/).

## Fonts

### Typefaces

There are many different types of fonts, or more accurately, typefaces. The three you'll probably be most interested in are:

* [serif](http://en.wikipedia.org/wiki/Serif)
* [sans-serif](http://en.wikipedia.org/wiki/Sans_serif)
* [monospace](http://en.wikipedia.org/wiki/Monospaced_font)

### font-family

When you specify a font, whether it shows up or not depends on whether a user has that font installed on their system. Helvetica Neue is a nice sans-serif font, but it's unlikely to be on a Windows computer. The best way to handle fonts is to have fallbacks. Put the font you really want first and fall back to other acceptable, if not ideal, fonts.

```css
.foo {
  font-family: 'Helvetica Neue', Arial, sans-serif;
}

.bar {
  font-family: 'Some Awesome Serif Font', 'Times New Roman', Times, Georgia, serif;
}
```

It's also possible to use custom fonts that you or a font service provide. I'll leave you to research them as extra credit if you're interested.

### font-size and ems

Fonts can be specified in units other than pixels (`px`). `em` is a more relative unit of measure. It changes based on the base font size (specified by the user in their settings or by the nearest ancestor of an element that has a font-size specified) and by the font-family.

[Check out CSS Tricks](http://css-tricks.com/css-font-size/) for more info.

Note that `em` can be used for more than just font-size. It can be used anywhere you can specify something with pixels, like for a margin or padding.

## Colors

CSS offers many options for specifying colors. These can be used anywhere colors can be used: `color`, `background-color`, `border-color`, etc.

| name  | hex     | rgb                | hsl                 |
| ----- | ------- | ------------------ | ------------------- |
| black | #000000 | rgb(0, 0, 0)       | hsl(0, 0, 0)        |
| green | #008000 | rgb(0, 128, 0)     | hsl(120, 100%, 50%) |
| aqua  | #00ffff | rgb(173, 216, 230) | hsl(180, 100%, 50%) |

rgb and hsl also have varieties where you can specify their alpha value (opacity). It's super useful when you want to alter the opacity of just the text or the background and not the entire element.

```css
rgba(0, 0, 0, 0.5) /* black at 50% opacity */

hsla(120, 100%, 50%, 0.75) /* green at 75% opacity */
```

## Positioning

Positioning is an imporant part of laying out a page with CSS. Here are a couple articles that explain it well:

* [CSS Positioning 101](http://alistapart.com/article/css-positioning-101)
* [Absolute, Relative, Fixed Positioning: How Do They Differ?](http://css-tricks.com/absolute-relative-fixed-positioining-how-do-they-differ/)

## Overflow

When a nested element is larger than its parent, it overflows. You can control this with the `overflow` rule. [Read up on it on CSS Tricks](http://css-tricks.com/the-css-overflow-property/). Stop when you get the section titled 'Float Clearing.' We'll get to floats next time.
