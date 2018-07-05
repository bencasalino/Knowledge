#OOP in JS

##Encapsulation
The core idea in object-oriented programming is to divide programs into smaller pieces and make each piece responsible for managing its own state. Separating interface from implementation is a great idea. It is usually called **encapsulation**.

This way, some knowledge about the way a piece of the program works can be kept **local** to that piece.
Someone working on the rest of the program does not have to remember or even be aware of that knowledge. Whenever these local details change, only the code directly around it needs to be updated.

Public vs Private & JS
Properties that are part of the interface are called **public**. The others, which outside code should not be touching, are called **private**. Many languages provide a way to distinguish public and private properties and prevent outside code from accessing the private ones altogether. JavaScript, once again taking the minimalist approach, does not—not yet at least. There is work underway to add this to the language.

**NOTE:**
It is also common to put an underscore (\_) character at the start of property names to indicate that those properties are private.

---
