# conquering-responsive-layouts

In this repository I will taking notes, and completing the challenges from the 21 day course - [Conquering Responsive Layouts](https://courses.kevinpowell.co/conquering-responsive-layouts) by Kevin Powell.
Using this README file, I will be taking down notes, any code snippets I find useful from the examples, as well as problems I ran into during the challenges - mainly for personal use in order to come back in the future.


## Chapters

### [Day 1](#day-1---using-percentages--avoiding-heights)
#### [Percentages vs Fixed widths](#percentages-vs-fixed-widths)
#### [Percentages on the child](#percentages-on-the-child)
#### [Why it's a good idea to avoid heights](#why-its-a-good-idea-to-avoid-heights)
#### [Challenge 1](#challenge-1)
### [Day 2](#day-2---getting-familiar-with-relative-units)
#### [CSS em and rem explained](#css-em-and-rem-explained)
#### [Why you shouldn't set font-sizes using em](#why-you-shouldnt-set-font-sizes-using-em)
### [Day 3](#day-3---enter-max-width)
### [Day 4](#day-4---extra-curricular-activities)
### [Day 5](#day-5---practice-time)
### [Day 6](#day-6---review)
### [Day 7](#day-7---solution-to-challenge-3)
### [Day 8](#day-8---flexbox-basics)
### [Day 9](#day-9---a-deeper-dive-into-flexbox)

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


## Day 4 - Extra curricular activities

## Day 5 - Practice Time!

## Day 6 - Review

## Day 7 - Solution to Challenge #3

## Day 8 - Flexbox Basics

## Day 9 - A deeper dive into flexbox

## Day 10 - Extra curricular activities

## Day 11 - Using flexbox for a navigation

## Day 12 - Getting fancy with navigations

## Day 13 - Break

## Day 14 - Break

## Day 15 - Intro to media queries

## Day 16 - What breakpoints to use?

## Day 17 - The viewport meta tag

## Day 18 - Challenge solution & Mobile-first

## Day 19 - Mobile navigation challenge

## Day 20 - Mobile navigation challenge

## Day 21 - You've done it!
