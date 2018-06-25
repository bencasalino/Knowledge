### Defining And Using CSS Variables

Variables follow the same scope and inheritance rules like any other CSS definition.

The easiest way to use them, is to make them globally available, by adding the declarations to the :root pseudo-class, so that all other selectors can inherit it.

```
// root psuedo class - all other selectors can inherit
:root{
    --awesome-blue: #2196F3;
}
```

### Accessing CSS Vars

To access the value inside a variable we can use the var(...) syntax.
**NOTE:** that names are case sensitive, so --foo != --FOO.

```
.some-element{
    background-color: var(--awesome-blue);
}
```

###### Naming and readability:

```
:root {
  --primary-color: #b1d7dc;
  --accent-color: #ff3f90;
}

html {
  background-color: var(--primary-color);
}

h3 {
  border-bottom: 2px solid var(--primary-color);
}

button {
  color: var(--accent-color);
  border: 1px solid var(--accent-color);
}

:root {
  --tiny-shadow: 0 2px 1px 0 rgba(0, 0, 0, 0.2);
  --animate-right: translateX(20px);
}
li {
  box-shadow: var(--tiny-shadow);
}
li:hover {
  transform: var(--animate-right);
}
```

### Dynamically Changing Variables

When a custom property is declared multiple times, the standard cascade rules help resolve the conflict and the lowermost definition in the stylesheet overwrites the ones above it.

The example below demonstrates how easy it is to dynamically manipulate properties on user action, while still keeping the code clear and concise.

```
.blue-container {
  --title-text: 18px;
  --main-text: 14px;
}
.blue-container:hover {
  --title-text: 24px;
  --main-text: 16px;
}
.green-container:hover {
  --title-text: 30px;
  --main-text: 18px;
}
.title {
  font-size: var(--title-text);
}
.content {
  font-size: var(--main-text);
}
```
