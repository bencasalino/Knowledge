# XML

[Guide](https://www.w3schools.com/php/php_xml_parsers.asp)

The XML language is a way to structure data for sharing across websites.
XML is easy to create. It looks a lot like HTML, except that you make up your own tags.

---

## XML Parser

To read and update, create and manipulate an XML document, you will need an XML parser.

In PHP there are two major types of XML parsers:

- Tree-Based Parsers
- Event-Based Parsers

### Tree-Based Parsers

Tree-based parsers holds the entire document in Memory and transforms the XML document into a Tree structure. It analyzes the whole document, and provides access to the Tree elements (DOM). This type of parser is a better option for smaller XML documents, but not for large XML document as it causes major performance issues.

Example of tree-based parsers:

- SimpleXML

- DOM

### Event-Based Parsers

Event-based parsers do not hold the entire document in Memory, instead, they read in one node at a time and allow you to interact with in real time. Once you move onto the next node, the old one is thrown away. This type of parser is well suited for large XML documents. It parses faster and consumes less memory.

Example of event-based parsers:

- XMLReader

- XML Expat Parser

---

# XHTML

HTML came along first, XHTML was designed to fix problems with HTML, and HTML5 solved problems XHTML was designed to fix. They’re all markup languages that provide structure and organization to the content of webpages and applications, but their relevance has shifted as newer versions of HTML have evolved, rising to the challenges of mobile demands, responsive design, and developers who want to accomplish more with less.

## The Most Important Differences from HTML:

Document Structure
XHTML DOCTYPE is mandatory
The xmlns attribute in <html> is mandatory

<html>, <head>, <title>, and <body> are mandatory

- XHTML Elements

- XHTML elements must be properly nested

- XHTML elements must always be closed

- XHTML elements must be in lowercase

- XHTML documents must have one root element

- XHTML Attributes

- Attribute names must be in lower case

- Attribute values must be quoted

- Attribute minimization is forbidden

Some differences between HTML5 and XHTML:

XHTML is hybrid between HTML and XML, whereas HTML5 is a version of HTML.

XHTML and HTML are two different ways of representing markup.
XHTML is almost identical to HTML 4.01. HTML5 is the latest version of HTML.
In XHTML, all tags, once opened, must be closed. HTML is less strict.
XHTML has some restrictions about what tags can be nested inside each other.
XHTML is stricter version of HTML; HTML5 is an upgrade of HTML.
XHTML uses XML parsing requirements. HTML uses its own.
HTML does not have a well-formedness constraint, no errors are fatal. In XHTML, well-formedness errors are fatal.
