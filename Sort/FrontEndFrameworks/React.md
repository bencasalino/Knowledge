Organize these notes!

Firebase Deploy for React
Steps:
Firebase init
Where to build at→ ./build
Firebase deploy

PORT=8080 npm start ← to change ports

HMR (Hot Module Replacement): ?
Redux: Single source of truth→ State is read-only → Changes are made with pure functions
In other words: the status of the complete application is stored in an object tree within a single store. This helps with debugging the application, and some functionalities are easier to implement. The state is read-only and can only be changed via actions to avoid race conditions (it also helps with debugging). Reducers are written to specify how the states can be transformed by actions.

Reason: ?
Lifecycle Hooks: ?

Components: Everything in react is a component → a reusable piece of the website. React applications are made out of components. A component is a small, reusable chunk of code that is responsible for one job. That job is often to render some HTML.

Gatsby: Static site generator for React.
https://www.gatsbyjs.org/
Pros:
A pre-configured Webpack, meaning you get all the benefits without any of the headaches.
Automatic routing based on your directory structure.
All HTML content is also generated server-side, so you get the best of both worlds.
Static content means no server and super-easy hosting on GitHub Pages.

Storybook: UI Component Framework for React.

Props: Pass information into a tag via a prop ← similar to inline styles HTML attributes. How components “talk” to each other. Props flow downwards from the parent component. This is why people refer to React as having unidirectional data flow.

Note: data flows from parent to child. Props are immutable (fancy word for it not changing)

States: Props shouldn’t change, so state steps up. Normally components don’t have state and so are referred to as stateless. A component using state is known as stateful. State is used so that a component can keep track of information in between any renders that it does. When you setState it updates the state object and then re-renders the component.

States vs Props: Props and State do similar things but are used in different ways. The majority of your components will probably be stateless. Props are used to pass data from parent to child or by the component itself. They are immutable and thus will not be changed. State is used for mutable data, or data that will change. This is particularly useful for user input. Think search bars for example. The user will type in data and this will update what they see.

Concept: “single source of truth / state”

Module Bundler: ? (Webpack/Browserify?) (is graphQL part of Webpack or need to be installed by webpack? )

Component Based Architecture: https://reactjs.org/docs/components-and-props.html

Components:
// create a variable named React ← The object is called the React library.
import React from 'react';
// The methods imported from 'react-dom' are meant for interacting with the DOM.
Note: the DOM is used in React applications, but it isn't part of React. After all, the DOM is also used in countless non-React applications. Methods imported from 'react' are only for pure React purposes, such as creating components or writing JSX elements.
import ReactDOM from 'react-dom';

class MyComponentClass extends React.Component {
render() {
return <h1>Hello world</h1>;
}
}

ReactDOM.render(
<MyComponentClass />,
document.getElementById('app')
);

Component Class: Every component must come from a component class. A component class is like a factory that creates components. If you have a component class, then you can use that class to produce as many components as you want. Every component must come from a component class.

To make a component class, you use a base class from the React library: React.Component.

React.Component:

Virtual DOM: In React, for every DOM object, there is a corresponding "virtual DOM object." A virtual DOM object is a representation of a DOM object, like a lightweight copy. A virtual DOM object has the same properties as a real DOM object, but it lacks the real thing's power to directly change what's on the screen. Manipulating the DOM is slow. Manipulating the virtual DOM is much faster, because nothing gets drawn on-screen. Think of manipulating the virtual DOM as editing a blueprint, as opposed to moving rooms in an actual house.

Once the virtual DOM has updated, then React compares the virtual DOM with a virtual DOM snapshot that was taken right before the update.By comparing the new virtual DOM with a pre-update version, React figures out exactly which virtual DOM objects have changed. This process is called "diffing." Once React knows which virtual DOM objects have changed, then React updates those objects, and only those objects, on the real DOM. In our example from earlier, React would be smart enough to rebuild your one checked-off list-item, and leave the rest of your list alone. This makes a big difference! React can update only the necessary parts of the DOM. React's reputation for performance comes largely from this innovation.

In summary, here's what happens when you try to update the DOM in React:

The entire virtual DOM gets updated.
The virtual DOM gets compared to what it looked like before you updated it. React figures out which objects have changed.
The changed objects, and the changed objects only, get updated on the real DOM.
Changes on the real DOM cause the screen to change.

JSX
JSX - is a syntax extension for JavaScript. It was written to be specifically used with React and looks a lot like HTML.

Syntax Extension/compiling - In this case, it means that JSX is not valid JavaScript and web browsers can’t read it. If a JavaScript file contains JSX code then that file would have to be compiled. That means that before it reaches a web browser a JSX compiler will translate JSX into regular JavaScript. (similar to SASS>CSS)

JSX Expressions/Elements - JSX elements are treated as JavaScript expressions. A JSX element can be saved as a variable, passed into a function, stored in an object or array etc.

const myPar = <p> heyo </p>;

JSX attributes- A single element can have attributes just like in HTML (similar to inline styling).

const myImage = <img src=”images/test.jpg” alt=”test” />;

Nested JSX - If a JSX expression takes up more than one line and has multiple associated tags it MUST be wrapped in parentheses. Below the example shows a JSX expression nested “a” tag that has been saved to a variable

const myLink = ( ← expressions can be saved to variables.
<a href=”www.google.com”>
<h1>
Click Me!
</h1>
</a>
); ← needed for “nesting” since it has multiple tags

Note: A JSX expression must have exactly one outermost element. The first opening tag and the final closing tag of a JSX expression must belong to the same JSX element! Can only return ONE parent element.

Note: JSX requires closing tags for all elements, most common examples will include images, br & hr tags.

Comments in JSX: normal // comments will work near/outside of JSX but if comments are desired inside JSX the syntax is { /_ i am a comment _/ } Comments should not go in the top level and will cause syntax errors.

Will work:
const paragraphs = (

  <div id="i-am-the-outermost-element">
    <p>I am a paragraph.</p>
    <p>I, too, am a paragraph.</p>
  </div>
);

Won’t work:
const paragraphs = (

  <p>I am a paragraph.</p>
  <p>I, too, am a paragraph.</p>
);

className: Since class is a reserved word in JavaScript to use class with React we use className instead.

Rendering
Rendering JSX Elements/Expressions - To render a JSX expression means to make it appear on-screen.

ReactDOM is the name of a JavaScript library. This library contains several React-specific methods, all of which deal with the DOM in some way or another.

ReactDOM.render() is the most common way to render JSX. It takes a JSX expression, creates a corresponding tree of DOM nodes, and adds that tree to the DOM. That is the way to make a JSX expression appear on-screen. This is the first argument being passed to ReactDOM.render(). ReactDOM.render()'s first argument should be a JSX expression, and it will be rendered to the screen.

The first argument is appended to whatever element is selected by the second argument.

File Structure:
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(<h1>Hello world</h1>,
document.getElementById('app'));

Variables: can also be passed into the first argument for ReactDOM.render. When you inject JavaScript into JSX, that JavaScript is part of the same environment as the rest of the JavaScript in your file. That means that you can access variables while inside of a JSX expression, even if those variables were declared on the outside.

// Declare a variable:
const name = 'Gerdo';

// Access your variable
// from inside of a JSX expression:
const greeting = <p>Hello, {name}!</p>;

Note: Variables CAN be used in ReactDOM.render()
const theBestString = 'tralalalala i am da best';
ReactDOM.render(<h1>{theBestString}</h1>,
document.getElementById('app'));

Variable Attributes: You can use a variable to set the `height` and `width` attributes:

const sideLength = "200px";

const panda = (
<img
    src="images/panda.jpg"
    alt="panda"
    height={sideLength}
    width={sideLength} />
);

The Virtual DOM and ReactDOM.render() - One special thing about ReactDOM.render() is that it only updates DOM elements that have changed. That means that if you render the exact same thing twice in a row, the second render will do nothing. This is significant! Only updating the necessary DOM elements is a large part of what makes React so successful. This is happening because of the Virtual DOM.

Using “Curly Braces” in JSX vs JavaScript
Note: Any code in between the tags of a JSX element will be read as JSX.

ReactDOM.render(

  <h1>2 + 3</h1>,
  document.getElementById('app')
);
Output → 2 + 3

-VS-

ReactDOM.render(

  <h1>{2 + 3}</h1>,
  document.getElementById('app')
);
Output → 5

Note: The code in between the div tags will be treated as JSX & the code in-between the p tag/{} will be treated as regular JavaScript. The curly braces themselves won't be treated as JSX nor as JavaScript. They are markers that signal the beginning and end of a JavaScript injection into JSX, similar to the quotation marks that signal the boundaries of a string.
const pi = (

  <div>
    <h1>
      PI, YALL!
    </h1>
    <p>
      {Math.PI.toFixed(20)}
    </p>
  </div>
);

Event Listeners in JSX: You create an event listener by giving a JSX element a special attribute. (Valid React event name list → https://reactjs.org/docs/events.html#supported-events ) Note: that in HTML, event listener names are written in all lowercase, such as onclick or onmouseover. In JSX, event listener names are written in camelCase, such as onClick or onMouseOver.
<img onClick={myFunc} />

JSX Conditionals: you can not inject an if statement into a JSX expression, the code will break. if.js works, because the words if and else are not injected in between JSX tags. The if statement is on the outside, and no JavaScript injection is necessary.This is a common way to express conditionals in JSX.

let message;

if (user.age >= drinkingAge) {
message = (
<h1>
You are old enough!
</h1>
);
} else {
message = (
<h1>
You are too young
</h1>
);
}

ReactDOM.render(
message,
document.getElementById('app')
);

Ternary Operator in JSX:
const headline = (

  <h1>
    { age >= drinkingAge ? 'Buy Drink' : 'Do Teen Stuff' }
  </h1>
);

&& Conditional in JSX: && works best in conditionals that will sometimes do an action, but other times do nothing at all. Every time that you see && in this example, either some code will run, or else no code will run

const tasty = (

  <ul>
    <li>Applesauce</li>
    { !baby && <li>Pizza</li> }
    { age > 15 && <li>Brussels Sprouts</li> }
    { age > 20 && <li>Oysters</li> }
    { age > 25 && <li>Grappa</li> }
  </ul>
);

.map in JSX:
const people = ['Rowe', 'Prevost', 'Gare'];

const peopleLis = people.map(person =>
// expression goes here:

  <li>{person}</li>
);

// ReactDOM.render goes here:
ReactDOM.render(<ul>{peopleLis}</ul>, document.getElementById('app'));

Keys: When you make a list in JSX, sometimes your list will need to include something called keys:

<ul>
  <li key="li-01">Example1</li>
  <li key="li-02">Example2</li>
  <li key="li-03">Example3</li>
</ul>

A key is a JSX attribute. The attribute's name is key. The attribute's value should be something unique, similar to an id attribute. keys don't do anything that you can see! React uses them internally to keep track of lists. If you don't use keys when you're supposed to, React might accidentally scramble your list-items into the wrong order. Not all lists need to have keys. A list needs keys if either of the following are true:

The list-items have memory from one render to the next. For instance, when a to-do list renders, each item must "remember" whether it was checked off. The items shouldn't get amnesia when they render.

A list's order might be shuffled. For instance, a list of search results might be shuffled from one render to the next.

If neither of these conditions are true, then you don't have to worry about keys. If you aren't sure then it never hurts to use them!

React.createElement - You can write React code without using JSX at all! The majority of React programmers do use JSX, and we will use it for the remainder of this tutorial, but you should understand that it is possible to write React code without it. When a JSX element is compiled, the compiler transforms the JSX element into the method that you see above: React.createElement(). Every JSX element is secretly a call to React.createElement().

const h1 = <h1>Hello world</h1>;
can be rewritten without JSX, like this:
const h1 = React.createElement(
"h1",
null,
"Hello, world"
);

Setup/Installing

Install globally (steps in order descending)
npm install -g create-react-app

Creates a react app
Create-react-app appName

cd into the folder
cd appName

This starts the app on localhost (runs the build, watches the build and runs the server)
Npm start

When ready to upload to Heroku for example.
Npm build

Makes all config files/settings visible for getting access/unlocking/unpacking/expanding
Npm run eject

Run tests file
Npm test

Components
File Setup:
src > components:
Top → imports “react”
middle→ components wanted
Bottom → where to render each component at.

Index.js File:
Top → import ‘react’
Middle → component/class
Bottom → exports to “index” js

React/CSS/Styled Components

Styled Components in React → Rather than adding styles to existing components, you instead create components that embody the styles. This allows for declarative and reusable components that are halfway between a regular HTML element and a fully-fledged React Component. This philosophy, as well as the GraphQL-esque string interpolation, take a bit of getting used to, but seeing as it’s nearly twice as popular as the second-place CSS-in-JS library, it’s safe to say there’s something here worth looking at.

Differences between JavaScript/Modules
https://alligator.io/react/react-css/

State Management/Redux:
This is where State Management comes in. Instead of storing your state (in other words, your data) bit by bit in each component, you store it in a single global store that then dispatches it to your React components:

GraphQL/Apollo/Redux? → alternative to Restful API’s

Whereas a REST API exposes multiple REST routes that each give you access to a predefined dataset (say, /api/posts, /api/comments, etc.), GraphQL exposes a single endpoint that lets the client query for the data it needs.

Think of it as making multiple trips to the butcher shop, bakery, and grocery store, versus giving someone a shopping list and sending them on their way to all three.

This new strategy becomes especially significant when you need to query multiple data sources. Just like with our shopping list example, you can now get data back from all these sources with a single request.

GraphQL itself is just a protocol, but its best implementation right now is probably the Apollo library, which works well with Redux. There is still a lack of instructional material around GraphQL and Apollo, but hopefully the Apollo documentation can help you get started.
