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
