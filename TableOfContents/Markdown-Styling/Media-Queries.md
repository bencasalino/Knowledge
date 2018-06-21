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
