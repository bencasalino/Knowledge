# HTML5 Notes

[HTML HOW TO MAKE... GUIDE](https://www.w3schools.com/howto/default.asp)

## Meta

- `base` - Base URL for all relative URLs
- `head` - tag for all relevant header information
- `link` - for linking local or external css stylesheets
- `meta` - meta info og tags etc.
- `style` - link for internal css stylesheets
- `title` - title tag that appears at top of browser

## Structural

- `header` - Header for its parent’s content
- `nav` - Collection of links
- `main` - Primary site content
- `section` - Group of content with a heading
- `article` - Independently redistributable content with a heading
- `aside` -
- `footer` - Footer for its parent’s content
- `div` -
- `span` -
- `h1`-`h6`
- `ul` -
- `ol` -
- `li` -
- `dl` - Description list, key-value pairs
- `dt` - Term
- `dd` - Description

## Application

- `dialog` -
- `menu` -
- `menuitem` - Command invoked from a menu
- `meter` - Scalar measurement with a range
- `progress`

## Text

- `p` - paragraph tag
- `em` - Emphasis
- `strong` - Strong emphasis
- `b` - Different, no emphasis, eg. product names or keywords
- `i` - Different, no emphasis, eg. foreign or technical terms, thoughts
- `s` - Irrelevant or inaccurate
- `mark` - Highlighted
- `hr` - Thematic break between paragraphs
- `wbr` - Word break opportunity
- `pre` -
- `br` - line break tag
- `cite` -
- `code` - Code snippet
- `kybd` - Inline simulated user-input
- `samp` - Sample computer output
- `var` - Variable in computer output
- `q` - Inline quotation
- `blockquote`
- `data` - Value with a machine-readable value, eg. a UPC
- `a` - anchor tag
- `abbr` - Abbreviation, use “title” attribute for full word
- `small` - Side comments and fine print, eg. legal
- `sub` - Subscript, eg. for math
- `sup` - Superscript, eg. for math
- `del` - Deleted text from an edit
- `ins` - Inserted text from an edit
- `time` - time type tag
- `address` - Contact information for an article
- `ul` - unordered list
- `ol` - ordered list
- `li` - list tag
- `details` - Hideable
- `summary` - Header for details tag

## Media

- `map` - Image map
- `area` - Hotspot inside a map
- `audio` - audio type tag
- `video` - video type tag
- `track` - Defines captioning for audio and video
- `source` - Asset for audio or video
- `figure` - Wraps an image for markup
- `img` - image tag
- `figcaption` - Caption a figure

## Tables

- `table` - table tag
- `caption` - Title of a table, goes right after table
- `tbody` - table body
- `tr` - table row
- `td` - table data
- `th` - Header for a group of cells, defined by scope and headers
- `thead` - Rows defining the heads of columns
- `colgroup` - Group of columns
- `col` - Column that should have a consistent style
- `tfoot` - Rows defining the summary of columns

## Form Helpers

- `form` -
- `input` -
- `output` -
- `keygen` - Sets up public/private key with server
- `button` -
- `fieldset` - Group of controls and labels
- `legend` - Caption for a fieldset
- `datalist` - Has option tags for an input list
- `select` -
- `optgroup` - Group of options in a select element
- `option` -
- `textarea` -

## Input Types

- `text` -
- `color` -
- `date` -
- `datetime` -
- `datetime-local` -
- `email` -
- `month` -
- `number` -
- `range` -
- `search` -
- `tel` -
- `time` -
- `url` -
- `week` -

# Input Attributes

- `accept="audio/*"` -
- `autocomplete="on"` -
- `alt="alt-text"` - Only for image types
- `autofocus="autofocus"` - Gets focus when page loads
- `form="id"` - Form the input belongs to
- `formaction="url"` - Url that will process the input on submit
- `formenctype="application/x-www-form-urlencoded"`
- `formmethod="post"` - For formaction
- `formnovalidate="formnovalidate"` - If this input shouldn’t validate on submit
- `formtarget="_blank"` - Where to display response
- `height="100px"` - Only for image type
- `width="100px"` - Only for image type
- `list="datalist-id"` - Refers to a datalist element that has predefined options for the input
- `min="5"` -
- `max="7"` -
- `maxlength="3"` -
- `multiple="multiple"` -
- `pattern="regexp"` - Validates the input
- `placeholder="text"` - Hint
- `required="require"` - Must be filled out before submitting
- `readonly="readonly"`
- `size="3"` - Width of input element
- `src="u/r/l"` - For image type that will be used as a submit button
- `step="2"` - Intervals for a numeric input
- `disabled="disabled"` -

---

### Multiple Header/Footers

Can a web page contain multiple <header> elements? What about <footer> elements?

Yes to both. The W3 documents state that the tags represent the header(<header>) and footer(<footer>) areas of their nearest ancestor "section". So not only can the page <body> contain a header and a footer, but so can every <article> and <section> element.

W3 recommends having as many as you want, but only 1 of each for each "section" of your page, i.e. body, section etc.

---

<header> is used to contain introductory and navigational information about a section of the page. This can include the section heading, the author’s name, time and date of publication, table of contents, or other navigational information.

<article> is meant to house a self-contained composition that can logically be independently recreated outside of the page without losing it’s meaning. Individual blog posts or news stories are good examples.

<section> is a flexible container for holding content that shares a common informational theme or purpose.

<footer> is used to hold information that should appear at the end of a section of content and contain additional information about the section. Author’s name, copyright information, and related links are typical examples of such content.

---

Four types of @media properties

all, which applies to all media type devices
print, which only applies to printers
screen, which only applies to screens (desktops, tablets, mobile etc.)
speech, which only applies to screenreaders

---

The rel="noopener" is an attribute used in <a> elements (hyperlinks). It prevents pages from having a window.opener property, which would otherwise point to the page from where the link was opened and would allow the page opened from the hyperlink to manipulate the page where the hyperlink is.

- rel="noopener" is applied to hyperlinks.

- rel="noopener" prevents opened links from manipulating the source page.

--- \

## defer vs async (on a script tag)

- Defer --> The defer attribute downloads the script while the document is still parsing but waits until the document has finished parsing before executing it, equivalent to executing inside a DOMContentLoaded event listener. defer scripts will execute in order.

Placing a **defer** script in the <head> allows the browser to download the script while the page is still parsing, and is therefore a better option than placing the script before the end of the body.

- async --> The async attribute downloads the script during parsing the document but will pause the parser to execute the script before it has fully finished parsing. async scripts will not necessarily execute in order.

- default behavior --> If neither attribute is present, the script is downloaded and executed synchronously, and will halt parsing of the document until it has finished executing (default behavior). Scripts are downloaded and executed in the order they are encountered.

Summary:

If the scripts rely on each other, use defer.

If the script is independent, use async.

Use defer if the DOM must be ready and the contents are not placed within a DOMContentLoaded listener.

---
