ß# css-best-practices

Notes on CSS best practices

## CSS Style guides

- [CSS Tricks Styleguies](http://css-tricks.com/css-style-guides)
- [CSS Tricks SASS styleguides](http://css-tricks.com/sass-style-guide/)
- [Trello CSS Guide](https://gist.github.com/bobbygrace/9e961e8982f42eb91b80)
- [Trello CSS Guid again](http://blog.trello.com/heres-the-official-trello-css-guide/)

## Code smells in CSS - CSS Wizardy

http://csswizardry.com/2012/11/code-smells-in-css

Large projects that spans for years where maintainability is a real issue:

> "when you’re working on one site for months on end, you can’t afford poor code, be it CSS or otherwise, and any bad code needs righting."


### Smells

Undoing styles (apart from in a reset):

Well done CSS should inherit and cascade from previously things defined. ΩßInherit, never undo, having to remove styles might mean that you applied them too early. 

> "As soon as I see CSS that undoes previous styling, I can be pretty sure that it’s because something was poorly architected and that order in which things were built/written needs a rework."

Magic numbers:

a value that is used 'because it just works' (see the 36px example for the top style on the drop down). Since 'it just works', it is hard to communicate to other developers where the number came from, when someone else is working in our code, then can either delete the magic number (back to square one) or just work her way around it (hacking on top of a hack, increasing the entropy in the code, see http://pragprog.com/the-pragmatic-programmer/extracts/software-entropy.

> "As soon as I see magic numbers in CSS I start asking questions. Why is this here? What does it do? Why does that number work? How can you achieve the same without that magic number?"

Qualified selectors:

Selectors who are needlessly prepended to an element, like:

    ul.nav{}
    a.button{}
    div.header{}

Qualified selectors are bad because:

- They totally inhibit reusability on another element
- They increase specificity
- They increase browser workload

Instead of qualified selectors:

use (which can be applied to different elements and facilitates swapping styles when the markup of the site changes):

``` css
.nav{}
.button{}
.header{}
```

Hard coded absolute values:

The only example is the absolute value on the line height, which should use a relative value of `1.333`:

```
    line-height: 1.333;
```


> "Hard-coded values are not very future proof, flexible or forgiving, and thus should be avoided. The only things that should ever really have hard-coded values are things like sprites which will always need to be a certain size no matter what. As soon as I see a hard-coded unit in a stylesheet I want to know why it was required and how it could be avoided."


Brute forcing:

> "This one is in a similar vein to hard-coded numbers, but a little more specific. Brute forcing CSS is when you use hard-coded magic numbers and a variety of other techniques to force a layout to work."

``` css
.foo {
    margin-left: -3px;
    position: relative;
    z-index:99999;
    height:59px;
    float:left;
}
```

Dangerous selectors:

selectors with far too broad reach, like applying a very specific selector to all `div` elements.

Reactive `!important`:

> "`!important` should only ever be used proactively, not reactively."

Like when you know (beforehand) that something should always **always** take precedence (for example, errors should always be red, no matter what):

```css
.error-text {
    color: #c00!important;
}
```

Reactive `!important`:

using `!important` to get out of a specific problem, forcing thing in reaction to an issue, is a bad thing.

IDs:

basically… never use them (but see: http://css-tricks.com/bad-code-dogmatism-etc)

An ID is 255 times more specific than one class… "http://codepen.io/chriscoyier/pen/lzjqh This means you’d need 256 chained classes to override one ID

[ ^^ This is not the case anymore L.C. ]

Loose class names:

one that isn't specific enough for its intended purpose (the `.card`> example)

The first problem:

ambiguity 

> Let’s imagine it means credit card; this class would have been much better had it been `.credit-card-image{}`. A lot longer, yes; a lot better, hell yes!


The second problem:

can be far to common and prone to be reassigned/redefined.

Loose class names:

> All this can be avoided by using much stricter class names. Classes like `card` and `.user` and suchlike are far too loose, making them hard to quickly understand, and easy to accidentally reuse/override."


## Bad Code, Dogmatism, etc..

Revolves around the idea of never using ID's to style things.

Chris Coyier then says:

> Avoiding ID's altogether has lead to a better CSS authoring experience for me. I probably should have framed it more like that, but hey.

Then towards the end:

> I also feel Jeffrey has a deeper perspective on this as Harry or I might. As we talked about on ShopTalk show, Jeffrey worked through some eras where markup was extremely nasty and helped usher in an age of clean markup that we're used to seeing today. I can understand being nervous if he feels things move back the other direction.

http://css-tricks.com/bad-code-dogmatism-etc/

## Avoid nested selectors for more modular CSS - Intermediate

http://thesassway.com/intermediate/avoid-nested-selectors-for-more-modular-css

## Writing DRY vanilla CSS - CSS Wizardry – CSS

http://csswizardry.com/2013/07/writing-dryer-vanilla-css/
