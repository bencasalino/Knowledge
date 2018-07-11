## WCAG 2.0

[Web Accessibility Tools ](https://frontendmasters.com/books/front-end-handbook/2018/tools/accessibility.html)

## ARIA

Accessible Rich Internet Applications

## Roles

- Landmark Roles are the big ones (should only be one per site)

```
<header role="banner">
<main role="main">
<aside role="complementary">
<footer role="contentinfo">
```

---

## aria-label

"Read More" links would show in a screen-reader as Read More

```
<a href="test.html" aria-label"Read more about this link"> Read More</a>
```

---

## Skip Links

- used for older screen readers but now roles are better. Jump to important sections on the page.

- "Back to Top" button can be used as a skip link.

```
<ul class="skip-links>
  <li> <a href="#home"> Home </a></li>
  <li> <a href="#about"> About </a></li>
</ul>

<p id="about">About the site </p>
```

How to hide: (can be un-hidden with using "tab")

```
.skip-links {
margin: 0;
padding: 0;
list-style-type: none;
}

.skip-links a {
  position: absolute;
  top: -3em;
}

.skip-links a:focus {
  top: 0;
}
```

---

## Tools

- Color Oracle Mac Tool (to see what color-blind people would see)

* Chrome Web Developer Toolbar ( Turn off all styles in CSS to see what a screen reader might see, also can turn on all alt tags to check.)

- Total Validator (app to DL - check against, shows errors just like HTML Validator - can change between different WCAG Standards. )

- Wave Accessibility Tool (online version shows where errors are, much more visually appealing)

- Accessibility Developer Toolbar (for Chrome)

- Voiceover Utility and Router (Screenreader built into Mac)

[Controlling Captions in vidoes with html/css](https://www.youtube.com/watch?v=DcWsUyhBykE&index=7&list=PLyuRouwmQCjlu6VexWFQNToJ3EaQUva1t)

---

## Validators
