# Dijit Claro Stylus Conversion

This repository contains a port of Dijit's Claro theme (as of Dojo version 1.10.4)
from [Less](http://lesscss.org/) to [Stylus](http://learnboost.github.com/stylus/).

**Note:** conversions for earlier Dojo versions (back to 1.7) are available on separate branches:

* [1.7 branch](https://github.com/kfranqueiro/dijit-claro-stylus/tree/1.7)
* [1.8 branch](https://github.com/kfranqueiro/dijit-claro-stylus/tree/1.8)
* [1.9 branch](https://github.com/kfranqueiro/dijit-claro-stylus/tree/1.9)

## Usage

Make sure Stylus is installed...

```
npm install -g stylus
```

...then inside the top level of this repository, run:

```
stylus . form layout
```

## Notes

The results of this conversion have been checked for accuracy via the
following processes:

* Compared CSS output of both LESS and Stylus for (near-)matching values
* Compared diffs between the previous and current Dojo version's LESS against
  the corresponding diffs between the previous and current versions in this repository
* Visually compared using `dijit/themes/themeTester.html`

## Differences

The intent of this conversion is generally to maintain parity with the CSS output
by Claro's LESS resources.  To some extent there are minor differences, including
blank lines, line breaks between multiple selectors, and off-by-one differences
from BIFs such as `saturate`, `lighten`, and `darken`.

Any notable or intentional differences between Claro's LESS resources and the
Stylus resources in this conversion are explained below.

### Disabled Text Input Styles

There was a noticeable difference in the result of 2 calculations for disabled
textbox/textarea styles for WebKit in `form/Common.css`, which have had their
source values tweaked such that the resulting output matches the output from
Claro's `form/Common.less`.

### The `alpha-white-gradient` Mixin

The input argument format to the `alpha-white-gradient` mixin differs from the
overloaded set of mixins in Claro's `variables.less`, in order to allow a
single mixin to handle any number of arguments.

In `variables.styl`, the `alpha-white-gradient` mixin expects an optional
direction followed by any number of tuples containing 2 values, the first
being an alpha value and the second being the position within the gradient
at which to apply it.  For example:

    alpha-white-gradient((0.3 0%), (0 100%))

Or, with a direction:

    alpha-white-gradient(left, (0.3 0%), (0 100%))

Note that this does not affect the CSS output at all, only the `styl` files.

## License

The contents of this repository are available under the same dual
modified BSD / AFL 2.1 license as the Dojo Toolkit.