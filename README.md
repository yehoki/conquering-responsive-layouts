# conquering-responsive-layouts

In this repository I will taking notes, and completing the challenges from the 21 day course - [Conquering Responsive Layouts](https://courses.kevinpowell.co/conquering-responsive-layouts) by Kevin Powell.
Using this README file, I will be taking down notes, any code snippets I find useful from the examples, as well as problems I ran into during the challenges - mainly for personal use in order to come back in the future.

## Chapters

- [Day 1 - Using percentages & avoiding heights](#day-1---using-percentages--avoiding-heights)
  * [Percentages vs Fixed widths](#percentages-vs-fixed-widths)
  * [Percentages on the child](#percentages-on-the-child)
  * [Why it's a good idea to avoid heights](#why-its-a-good-idea-to-avoid-heights)
  * [Challenge 1](#challenge-1)
- [Day 2 - Getting familiar with relative units](#day-2---getting-familiar-with-relative-units)
  * [CSS em and rem explained](#css-em-and-rem-explained)
  * [Why you shouldn't set font-sizes using em](#why-you-shouldnt-set-font-sizes-using-em)
- [Day 3 - Enter max-width](#day-3---enter-max-width)
  * [Adding in a max-width](#adding-in-a-max-width)
  * [Challenge 2](#challenge-2)
- [Day 4 - Extra curricular activities](#day-4---extra-curricular-activities)
  * [CSS Units: vh, vw, vmin, vmax](#css-units-vh-vw-vmin-vmax)
- [Day 5 - Practice Time!](#day-5---practice-time)
  * [Challenge 3](#challenge-3)
- [Day 6 - Review](#day-6---review)
  * [Why you shouldn't use 'em's for font-size](#why-you-shouldnt-use-ems-for-font-size)
  * [A Tale of width and max-width](#a-tale-of-width-and-max-width)
- [Day 7 - Solution to Challenge #3](#day-7---solution-to-challenge-3)
- [Day 8 - Flexbox Basics](#day-8---flexbox-basics)
  * [Flexbox basics](#flexbox-basics)
  * [An introduction to flexbox](#an-introduction-to-flexbox)
  * [Adding space in-between columns](#adding-space-in-between-columns)
  * [Flexbox challenge 1](#flexbox-challenge-1)
- [Day 9 - A deeper dive into flexbox](#day-9---a-deeper-dive-into-flexbox)
  * [Reducing the amount of HTML needed](#reducing-the-amount-of-html-needed)
  * [Adding a hero image](#adding-a-hero-image)
  * [Column widths and flexbox](#column-widths-and-flexbox)
  * [Ensuring the image is responsive](#ensuring-the-image-is-responsive)
  * [Flexbox challenge 2](#flexbox-challenge-2)
- [Day 10 - Extra curricular activities](#day-10---extra-curricular-activities)
  * [A deeper dive into flexbox](#a-deeper-dive-into-flexbox)
- [Day 11 - Using flexbox for a navigation](#day-11---using-flexbox-for-a-navigation)
  * [Flexbox challenge 3](#flexbox-challenge-3)
- [Day 12 - Getting fancy with navigations](#day-12---getting-fancy-with-navigations)
  * [Fancier up our navigation with flexbox](#fancier-up-our-navigation-with-flexbox)
  * [More improvements to the navigation](#more-improvements-to-the-navigation)
  * [Centering things the easy way](#centering-things-the-easy-way)
  * [Flexbox challenge 4](#flexbox-challenge-4)
- [Day 13 - Break](#day-13---break)
- [Day 14 - Break](#day-14---break)
- [Day 15 - Intro to media queries](#day-15---intro-to-media-queries)
  * [Media query basics](#media-query-basics)
  * [Adding one to our layout](#adding-one-to-our-layout)
- [Day 16 - What breakpoints to use?](#day-16---what-breakpoints-to-use)
  * [How to decide what breakpoints to use?](#how-to-decide-what-breakpoints-to-use)
  * [The 100% correct way to do CSS breakpoints](#the-100--correct-way-to-do-css-breakpoints)
- [Day 17 - The viewport meta tag](#day-17---the-viewport-meta-tag)
- [Day 18 - Challenge solution & Mobile-first](#day-18---challenge-solution--mobile-first)
- [Day 19 - Mobile navigation challenge](#day-19---mobile-navigation-challenge)
  * [Navigation challenge](#navigation-challenge)
- [Day 20 - Mobile navigation challenge](#day-20---mobile-navigation-challenge)
- [Day 21 - You've done it!](#day-21---you-ve-done-it)
  * [Links to other resources](#links-to-other-resources)
  * [Your final challenge](#your-final-challenge)

## Day 1 - Using percentages & avoiding heights

### Percentages vs Fixed widths

Using a fixed width with pixels, causes us to create a constant size i.e. this will always be the same and is not responsive at all based on the environment we are in.
An example here, was setting a `width: 900px;` on the parent element, where on a normal screen it works just fine, however the moment we go to a smaller display we get side scrolling in order to all of the content.

If we however take this same content, and remove the width - it will be responsive.

By default, everything is reponsive without extra CSS. But why?
The default width any block element has is 100%, namely 100% of the parent element.

**TLDR**: Working with percentages for the width makes our life much easier.

### Percentages on the child

As we saw, we previously set the width of a parent element - let's try it now for a child element. As previously mentioned, the default width of any block element is 100% of it's parent element.

First, setting a child with a constant width, in the example it was `width: 750px;` for the child and `width: 80%;` for the parent, since CSS is making sure we don't lose any information, the child element will overflow outside of the parent, and cause side-scrolling.

If we go to setting percentages on the child width, the percentages will correspond to the parent elements width.
So, if we have the parent with `width: 80%;` - this is `80%` of the body, and then the child with `width: 50%;`, we get that the child has `50%` of `80%` of the body, which in turn is `40%` of the body.

A lot of the times, setting the width on the child can be avoided depending on the context, but more on that later down the line.

### Why it's a good idea to avoid heights

Kevin's note under the video: `This is a general rule. There are times when you want to use height, but for the most part, they cause more issues than they solve.` Let's see why:

Setting heights in CSS cause all sorts of problems, whether it's with pixels or percentages. But what is the solution? Generally speaking, if you *think* you need to give something a height - **don't**.
As we previously saw with setting constant widths, websites are naturally responsive without any extra CSS. The problem is not with CSS itself - it's something what we did to make the website not responsive.

In the example, we can add more padding to the element which in turn will give us more background, however instead of using pixels for padding we should get used to making responsive padding as well.
So we will use the `em` and `rem` properties. A quick referesher of what they are:

- `em` is a relative unit of measurement used to size elements on the web page, and it is relevant to its parent element as `1 em` is equal to the font size set in the parent element. 
Example: The parent element has `font-size: 20px;`, and in the child we set `font-size: 2em;` - this in turn gives us `font-size:40px;`.

- `rem` stands for `root em` on the other hand is relative to the `root` element - which is usually the `<html>` element. As with `em`, when setting it, it makes it relative but not to the parent element - but instead to the very first element which surrounds it.

To finish it off, it's important to **ONCE AGAIN** note that websites are by **DEFAULT** responsive - if they are not responsive after adding `CSS` to it, it's our fault and it's our responsibility to fix it.

### Challenge 1

In this challenge, we applied everything from before in Day 1:

- We began with a set height on the parent `container` which caused the text to overflow. Removing this height allowed us to make sure the text fits within the child, and hence within the parent.

- Adding padding to the child element using `em` units, made the padding responsive to scaling.

- Finally, setting the child element's width to a percentage, corresponds to a percentage of the parent's width and hence makes the text responsive to resizing based on how big the parent ends up.

## Day 2 - Getting familiar with relative units

### CSS em and rem explained

This lesson was a recap of what has been said before about `em` and `rem` units. I took some notes in the Day 1 section already so just adding onto those here.

In general, when dealing with font-sizes it is much better to use `rem` as it stays consistent, since `em` relates to the direct parent we can sometimes get lost where it's corresponding.

When using `rem` with margins or padding it behaves slightly different. When we used `em` for properties like `margin` or `padding`, it looks at the value of the font-size within the same element.

So for example, consider this:

```CSS
div {
    font-size: 2.5em;
    margin-botton: 1em;
}
```
We will get that the bottom margin is equal to `2.5em` since it's 1 unit of the current font-size.

However, like with `font-size`, `rem` units always look at the root, and so they will always look at what the `<html>` element's properties are.

One *trick* for responsive buttons as an example, is setting their `font-size` property, and then setting the `padding` using `em` units - this way when we rescale the font-size, we will also rescale the padding on the button.

### Why you shouldn't set font-sizes using em

As we previously saw, `em` units look directly at their parent unit when comparing the size, in our case this would be font size.
Now, imagine you set something like this:
```CSS
ul {
    font-size: 1.5em;
}
```
Although it seems fine, we are just making sure that an unordered list has a font-size of 1.5 times it's parent, this can scale dramatically if we end up with a list of lists - each new list inside the old list will amplify the size of their text by 1.5.

If we want to set the font-size of objects uniquely in a multiple children elements, we can use `rem` units instead. Even though it might force us to write more CSS, it will make sure we are consistent throughout.

As we saw previously, one area where we should use `em` units instead of `rem` would be when setting the `padding` and `margin` properties on child elements. 
When using `em` units for `margin` or `padding` it references directly to the child's `font-size` value, meaning as we zoom in or out it will scale depending on the font-size; whereas if we were to use `rem` units, this would always be depending on the `<html>` element font-size.

***TLDR***: Use `rem` units for `font-size`, use `em` units for `margin` and `padding`, and **BE CAREFUL** when using `em` units within a deep-nested child element.


## Day 3 - Enter max-width

### Adding in a max-width

Sometimes, when we get to bigger sizes, when we define width on an element, as we increase the screen width, it keeeeeeeps on widening. We might get a div that goes from the very left of our screen to the very right, and it's not pretty - especially if our content inside the div doesn't take up all that space.
Well, the `max-width` property in CSS allows to set a maximum width of an object, once set to a value even if we grow our screen it does not exceed that value no matter what.

Consider this example:
```CSS
.div-class {
  width: 80%;
  max-width: 600px;
}
```
Here, we have an *ideal* width of 80% to be at all times, **HOWEVER** only up to a width of `600px` - which solves our problem.

Also, since we have `width` and `max-width` properties it's quite obvious that `min-width` also exists. However, similar to heights and setting constant values for widths - avoid it unless you have to use it, otherwise it will fight against being responsive.

### Challenge 2

So, in this challenge we will be using everything from Day 3, and Challenge 1 and a bit more - just for a challenge! 

As this chapter was mainly about max-width, and how it responds with increasing widths of the screen, we simply tried combining the first challenge with what was learnt here.

Personal notes learnt from Kevin's solution:
- Always try to reuse already made classes if we share properties. Use cascade to your advantage. Oh and it makes the CSS that much more readable.
- `margin: 0 auto;` lets you center things horizontally very easily.

## Day 4 - Extra curricular activities

For this one, firstly there is some extra content about viewport units in the Discord server.
Secondly, in the CSS units video, setting font-size with these units has some accessibility issues doing so, so unless it's a personal project - try to avoid them for setting font-size.

### CSS Units: vh, vw, vmin, vmax

The `vh` unit represents the current viewport height, and `vw` units represent the current viewport width. These however change in mobile designs, as then the viewport is including the search bar for a mobile browser, and so causes content to overflow - be careful and use media queries if necessary!

`vmax` and `vmin` units look for the largest and smallest values for both width and height - whichever one wins out.

An idea to think of for dynamic layouts, is using `vh` or `vw` units for the padding of an element, which will respond as we change our layout display.

## Day 5 - Practice Time!

### Challenge 3

## Day 6 - Review

### Why you shouldn't use 'em's for font-size

### A Tale of width and max-width

## Day 7 - Solution to Challenge #3

## Day 8 - Flexbox Basics

### Flexbox basics

### An introduction to flexbox

### Adding space in-between columns

### Flexbox challenge 1

## Day 9 - A deeper dive into flexbox

### Reducing the amount of HTML needed

### Adding a hero image

### Column widths and flexbox

### Ensuring the image is responsive

### Flexbox challenge 2

## Day 10 - Extra curricular activities

### A deeper dive into flexbox

## Day 11 - Using flexbox for a navigation

### Flexbox challenge 3

## Day 12 - Getting fancy with navigations

### Fancier up our navigation with flexbox

### More improvements to the navigation

### Centering things the easy way

### Flexbox challenge 4

## Day 13 - Break

## Day 14 - Break

## Day 15 - Intro to media queries

### Media query basics

### Adding one to our layout

## Day 16 - What breakpoints to use?

### How to decide what breakpoints to use?

### The 100% correct way to do CSS breakpoints

## Day 17 - The viewport meta tag

## Day 18 - Challenge solution & Mobile-first

## Day 19 - Mobile navigation challenge

### Navigation challenge

## Day 20 - Mobile navigation challenge

## Day 21 - You've done it!

### Links to other resources

### Your final challenge