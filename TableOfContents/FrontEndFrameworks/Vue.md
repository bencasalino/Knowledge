Organize these notes!

https://github.com/learn-vuejs/vue-patterns#string-template-or-es6-template-literal

Vue.js - Front End Framework Notes

Resources/Tools/Setup/Install

Do not use a fat arrow function in props or computed --- it disallows you to use “ .this “ elsewhere in the code

To get rid of the /#/ you need firebase to render as a single page app that will make it /fart.
Otherwise /fart thinks you are litterally looking to load the file /fart

The @/components is actually part of webpack not Vue. Its webpack that is looking for the @ sign otherwise use relative file paths.
https://github.com/kylecoberly/knowledge/wiki/Vue ← kyle’s knowledge base
A “View” is used to route something usaly a compoentn
Compoentnt is somthing that get pased into and then does an event

Component Library

Linting/Testing

Client/Server - Setup/Connection
Decupabled Client/Server Setup
[] build ← contains vue logo, webpack config files, other js files ?
[]config ← index.js and 2 env files

[] src
[] assets
Vue-Logo.png
[] components
TheHeader.vue
HelloWorld.vue
Template → html goes here
Script
export default {
name: 'HelloWorld',
data() {
return {
msg: 'Welcome to Your Vue.js App', ← part of default loaded template
};
},
};

Style → <style scoped>
App.vue
Template

<div id="app">
<img src="./assets/logo.png">
<HelloWorld/>

  </div>

Script ← how to import the HelloWorld.vue Component
import HelloWorld from './components/HelloWorld';

export default {
name: 'App',
components: {
HelloWorld,
},
};

Style ← css goes here

main.js ← import vue, import app, new Vue component App ← connected/component to App.vue
index.html ← file with id=app / contains all metadata and title library imports

[] static ← .gitkeep file
.babelrc
.editorconfig
.eslintrcjs
.eslintigonre
postcssrc.js
node_modules
package-lock.json
package.json
readme.md

Template Syntax/Setup/Linting
// Suppress all Vue logs and warnings
Vue.config.silent = false

Interpolations
Text/Raw HTML - v-html vs v-text: The HTML directive will render actual html if desired while the text directive will render any html tags that are also in the directive.

    Attributes
    Javascript Expressions

Directives
Arguments - some directives take an argument denoted by a colon after the directive name.
Modifiers - are special postfixes denoted by a dot, which indicate that a directive should be bound in a special way. For example the .prevent modifiers tells the v-on directive to call event.preventDefault() on the triggered event.

    Shorthands  ( : and @ ) - but : and @ are valid chars for attribute names and all Vue.js supported browsers can parse it correctly.

Computed Properties & Watchers
Computed Properties

    Computed Caching vs Methods

    Computed vs Watched Property

    Computed Setter

    Watchers/Watch option

Class & Style Bindings
Binding HTML Classes
Object Syntax
Array Syntax
Component Syntax

    Binding Inline Styles
    	Object Syntax
    	Array Syntax
    	Auto-prefixing
    	Multiple Values

Directives / Conditional Rendering
v-if
v-if on a <template>
v-else-if
Controlling reusable elements with key
V-show → will output
v-if vs v-show
v-if with v-for

V-model
V-bind → an attribute that is also called a directive.

V-pre → will render HTML similare to v-text.
V-once → disables re-rendering. Will only render something in the browser one time. If you try to change it again via dev-tools it will not re render again.
V-cloak→ wait to render only once the instance is loaded. Wil not “flicker” the {{ tesx }} handelbars while the page is loading,

V-html → tells vue to actually render html code and not escape it ( only use if you know the source is clean, can leave site vulnerable to scripting attacks if the user has the option to decide what link can go where.
v-for
v-on:submit.prevent="onSubmit">

Shorthands V-
The v- prefix serves as a visual cue for identifying Vue-specific attributes in your templates. This is useful when you are using Vue.js to apply dynamic behavior to some existing markup, but can feel verbose for some frequently used directives. At the same time, the need for the v- prefix becomes less important when you are building a SPA where Vue.js manages every template. Therefore, Vue.js provides special shorthands for two of the most often used directives, v-bind and v-on:

: and @ → are valid chars for attribute names and all Vue.js supported browsers.

V-bind
//full syntax
<a v-bind:hrel=”url”> … </a>

// shorthand
<a :href=”url”> … </a>

// full syntax
<a v-on:click=”doSomething”> … </a>

// shorthand
<a @click=”doSomething”> … </a>

V-if full example:

<div id="app-3">
  <span v-if="seen">Now you see me</span>
</div>

var app3 = new Vue({
el: '#app-3',
data: {
seen: true
}
})

Directive Name
Shortcut
Purpose
V-if, v-else-if, v-else
none
Conditional rendering
v-bind
:
Bind attributes dynamically, or pass props
v-on
@
Attaches an event listener to the element
v-model
none
Create two way data binding
v-pre
nonde
Skip compiling to boost performance
v-once
none
Don’t rerender
v-show
none

List Rendering
Mapping Array elements with v-for→ item in items
v-for with an object
Key
Array change detection
Mutation methods
push()
pop()
shift()
unshift()
splice()
sort()
reverse()
Replacing an Array
Displaying Filtered/Sorted Results
v-for with a range
V-for on a template
V-for with v-if
V-for with a component

Form Validation/Event Handling
Input Field Modifiers
.lazy → By default v-model syncs the input with the data after each input event. You can add the lazy modifier to instead sync after change events. v-model.lazy

.number→ If you want the user input to automatically typecast as a number. v-model.number

.tirm → if you want the input to be trimmed automatically. (whitespace) v-model.trim

Components
Need to be declared before use in app
Vue instances take same options as an object.
Can be be declare inside other components.
Data objects must be a function.
Paradigm: data-down/actions-up
Child components can validate types and are required to be passed in.
A property is only relative if its declared when constructed.

Router/Vuex State Management

Router

Vuex
Define:
Fetch parent →
Saving in state →
Passing a prop →
Store - where the Vuex lives??
Single source of truth → State management
State is scoped to the component → vuex lets all the components access it
The parent state owns the prop →
Mutations → change the state or mutate it
Actions → do a thing!

Lifecycle Hooks
Created →
Mounted →
Updated →
Destroyed →

API-Fetch/Axios
Axios: is a great http client library. It uses promises by default and runs on both the client and the server (which makes it appropriate for fetching data during server-side rendering). It’s also quite easy to use with Vue. Because it uses promises, you can combine it with async/await to get an amazingly concise and easy-to-use API, as I will demonstrate here.

Vuex

State management library

Single source of truth

Vue.js Appstravaganza
What is Vue.js?
Player Score Counter
Generate Simple App
Add Bootswatch
Up Button For Player 1
Down Button For Player 1
Up Button For Player 2
Down Button For Player 2
Todo App
Generate Simple App
Add Bootswatch
Form to add todo
Add todo to list when form submitted
Show todos in a list on page
Click a todo to mark it as done
Delete button for todo
Watch todos for changes and save to localStorage
Load todos from localStorage on page load
Reddit Client
Generate App with Router
Add Bootswatch
fetch posts from reddit
Add posts to page
Make it look kind of like reddit!
Add favorite button to post
Add favorites page to show favorites
Save favorites to localStorage
Load favorites on page load
Movie Search
Generate App with Router
Add Bootswatch
Add form to search for movies by title
fetch movies when form submitted
Add movies to page
Click movie to go to movie page
Create movie route
fetch single movie on movie page
