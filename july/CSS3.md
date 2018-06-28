## Positioning

- Options
  - `static` - Default, normal document flow, no `top`/`right`/`bottom`/`left`
  - `relative` - New positioning context for absolutely positioned children and itself
  - `absolute` - Relative to context, body if no relative parents
  - `fixed` - Relative to viewport, not in the document flow
- Margins for positioned elements are inside their contexts
- Absolutely positioned elements can be stretched with `top`/`right`/`bottom`/`left`
- Transformed parents make a new positioning context, even fixed elements
- Floats don't allow a height for parent elements. Use `overflow: auto;` to fix.

## Selectors

- `tag` -
- `.class` -
- `#id` -
- `group, selectors` -
- `*` -
- `+` - Next sibling
- `~` - All siblings
- `>` - All children

## Attribute Selectors

- `tag[attribute]` -
- `tag[attribute="value"]` -
- `tag[attribute^="starts-with-value"]` -
- `tag[attribute$="ends-with-value"]`-
- `tag[attribute*="contains-value"]` -

## Pseudo Classes

- `:link` -
- `:visited` -
- `:hover` -
- `:active` -
- `:first-line` -
- `:first-letter` -
- `:focus` -
- `:before {content: "..."}` -
- `:after {content: "..."}` -
- `::selection` -
- `:not(...)` -

## Child Selectors

- `:first-child` -
- `:last-child` -
- `:nth-child(odd | even | 3 | 3n + 4 )` ← Start counting at fourth
- `:first-of-type` -
- `:last-of-type` -
- `:nth-of-type(...)` -

---

## Inheritance

- Nearest ancestor wins in a sheet
- Directly styled element trumps all

What doesn't inherit:

- Margins
- Placement
- Background colors
- Borders

### Specificity

- Tags = 1 point
- Classes = 10 points
- IDs = 100 points
- Inline style = 1000 points

---

#### Rules

- Most points wins
- Last style breaks a tie
- `!important` overrides the score
- Internal stylesheets beat external stylesheets
- Reset browser stylesheets for consistency

## Transforms

- `rotate(90deg)`
- `scale(2)` or `scale(0.5, -2)`
  - Negative numbers flip
  - `scaleX()` or `scaleY()` for one dimension
- `translate(x, y)`
- `skew(x, y)`
- `transform-origin: x y` (changes the axis point for a transform)

## Transitions

- `transition-property: all` (or specific property)
- `transition-duration: 0.5s` (can be different for each property)
- `transition-timing: ease-in | ease-out | ease-in-out | cubic-bezier(1,2,3,4)`
- `transition-delay: 1s`
- `transition: all 0.5s ease-in 1s`

---

## Animations

```css
@keyframe <animation-name> {
  0% {
    /* properties */
  }
  50% {
    /* properties */
  }
  100% {
    /* properties */
  }
}
```

- `animation-name: <animation-name>`
- `animation-duration: 1s`
- `animation-timing-function: ease-in | linear | cubic-bezier`
- `animation-delay: 1s`
- `animation-iteration-count: 10 | infinite`
- `animation-direction: normal | reverse | alternate | reverse-alternate`
- `animation-fill-mode: forwards | backwards | both` (resting state)
- `animation-play-state: running | paused`
- `animation: name duration timing count direction delay fill`

---

## Lists

- `list-style-type: disc | circle | square | none | decimal | decimal-leading-zero | upper-alpha | upper-roman | lower-alpha | lower-roman`
- `list-style-position: inside | outside`
- `list-style-image: url(...)`

## Floats

- `float: left | right | none`
  - Floats to the left or right of a container
- Set a width when using float
- `overflow: hidden` hides under backgrounds
- `clear: left | right | both` (on elements that you want to be pushed by floated elements)

## Box Model

- content > padding > border > margin
- Box model applies to block and inline-block elements (only horizontal for inline-block)
- Percents calculate based on the width of the containing element
- If margins collide, it only uses the larger of the two ("collapsing" them)
- Negative margins remove space
- Don't set height for text areas- set rows and use `height: auto`

### Box Model Properties

- `border: width style color`
  - Styles: `solid | dotted | dashed | double | groove | ridge | inset | outset | none | hidden`
  - `border-radius: top-left top-right bottom-right bottom-left`
    - Can do `height / width` for elliptical shape
- `box-shadow: h-offset v-offset radius spread color`
- `box-sizing: content-box | padding-box | border-box` (what do h/w refer to)
- `overflow: visible | scroll | auto | hidden`
- `height` / `width`
- `min-height` / `max-height`

---

## Text

```css
@font-face {
    font-family: "...";
    src: url(...);
    src: url(...) format("woff");
    url(...) format("svg");
    font-weight: normal;
    font-style: normal;
}
```

### Fonts

- `font-family: font-name`
- `font-style: normal | italic`
  - `<em>` uses italic style
- `font-weight: normal | bold | 100-900`
  - `<strong>` uses font weight
- `font-variant: small-caps`
- `font-size: px | em | rem | %`
- `font: style variant weight size/line-height font-family`

### Text

- `text-transform: uppercase | lowercase | none`
- `text-shadow: right down blue color`
- `text-align: left | right | justify | center`
- `text-indent: 5rem` (first line)
- `line-height`
- `letter-spacing`
- `word-spacing`

## Colors

- Hex
- RGB
- RGBA
- HSL
  - Hues: 0/360 = red, 120 = green, 240 = blue
- HSLA
  - Hues: 0/360 = red, 120 = green, 240 = blue

---

## Media Queries

```css
@media <type> and (<feature>: <value>) {
  /* CSS */
}
```

Resources:

[CSS Tricks Media Query Guide](https://css-tricks.com/snippets/css/media-queries-for-standard-devices/)

[MQ Tester](http://mqtest.io/)

[MDN Media Queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Media_features)

Media Queries are defined by the @media followed by a media type.

Media types: all (default) , print, screen, speech.
Multiple media types can be used at once and should be separated by commas. TV and projection are now deprecated types.

```
@media screen, print {
  /*  styles for screen and print devices */
}
```

Media features: width, height, aspect-ratio, orientation and resolution.

Range features: min-width, max-width, min-height,max-height, min-aspect-ratio etc.

In the following simple example, the default background color is red, but screen devices with a viewport width that’s 650px or less will have a background color of blue instead:

```
body {
  background: red;
}

@media screen and (max-width: 650px) {
  body {
    background: blue;
  }
}
```

**NOTE:** When specifying a media type AND media feature, we need to

Media type only:

```
@media print {
  /* styles for print media only */
}
```

Media feature only:

```
@media (max-width: 65rem) {
  /* styles for any device that has a display width of 65rem or less */
}
```

Multiple Media Features (most common):

```
/* Extra-small */
@media screen and (max-width: 360px) {
  /* ... */
}

/* Small */
@media screen and (min-width: 361px) and (max-width: 480px) {
  /* ... */
}

/* Medium-only */
@media screen and (min-width: 481px) and (max-width: 960px) {
  /* ... */
}
```

**NOTE:** Multiple media queries can be separated by commas, in which case the commas act as logical "or" operators and the query becomes a list of queries.

In the following example, the media query will be true id the device has an orientation of "portrait" OR id the viewport has a min-width of 3rem and a max-aspect-ratio of 2/1.

```
@media (orientation: portrait), (min-width: 3rem) and (max-aspect-ratio: 2/1) {
  /* ... */
}
```

NOT Logical Operator:
You can use the NOT logical operator at the beginning of a query to toggle the truthiness of the whole query. The not operator is useful to apply styles when certain conditions are NOT met by the browser or device. Note that with not the media type is not optional. Also, not doesn't negate an entire query list (queries separated with commas), but only one query.

---

### Media Queries Level 4

pointer, any-pointer, hover, any-hover, overflow-line, overflow-block, update.

---

### Types

- `all`
- `print`
- `screen`
- `speech`

### Features

- `aspect-ratio (min, max)`
- `color (min, max)` (number of color bits)
- `color-index (min, max)` (number of colors)
- `device-aspect-ratio (min, max)` (written as 3/2)
- `device-height (min, max)`
- `device-width (min, max)`
- `grid` (vs. bitmap, eg TTY)
- `height (min, max)` (rendering area, not device)
- `monochrome (min, max)` (bits per pixel on a monochrome device)
- `orientation` (portrait or landscape)
- `resolution (min, max)` (in dpi, with units)
- `scan` (progressive or interlace, tv only)
- `width (min, max)` (rendering area, not device)

### Operators

- `and`
- Comma-separated lists (`or`)
- `not`
- `only` (inlined, used to prevent loading a responsive stylesheet in an old browser)

## Responsive Design

- Don't use floats
- Use less padding & margins
- No big bold fonts
- Use `display: none` on media queries to hide content
- Use `background-image` to serve up different images
- Good starting breakpoints: `480px`, `768px`
- Use `box-sizing: border-box`
- Set `max-width` for images

---

#CSS Specificity Rules

The rules to win the specificity wars are:

-Inline style beats ID selectors. ID selectors are more specific than classes and attributes (::hover, ::before…). Classes win over element selectors.

-A more specific selector beats any number of less specific selectors. For instance, .list is more specific than div ul li.

-Increasing the number of selectors will result in higher specificity. .list.link is more specific than .list and .link.
-If two selectors have the same specificity, the last rule read by the browser wins.

-Although !important has nothing to do with the specificity of a selector, it is good to know that a declaration using !important overrides any normal declaration. When two conflicting declarations have the !important keyword, the declaration with a greater specificity wins.

[Specificity Calculator](http://specificity.keegan.st/)
[CSS Units Demo](https://alberictrancart.github.io/css-units-demo/)

#BEM

BEM (Block, Element, Modifier) naming convention

Basic explanation would be:
Elements that are standalone are called Blocks.

Secondly, elements that are not standalone (they rely on parent) are called Elements (in this case it is modal\_\_element).

Thirdly, there're modifiers, they're used to make small change to existing element (eg. change color).

The syntax for modifier is : block\_\_element--modifier

---
