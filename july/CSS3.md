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
