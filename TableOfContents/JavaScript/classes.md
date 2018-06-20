#### Overview

Classes are templates for objects.

Javascript calls a constructor method when we create a new instance of a class.

Inheritance is when we create a parent class with properties and methods that we can extend to child classes.

We use the extends keyword to create a subclass.

The super keyword calls the constructor() of a parent class.

Static methods are called on the class, but not on instances of the class.

#### Classes

JavaScript is an object-oriented programming (OOP) language we can use to model real-world items. In this lesson, you will learn how to make classes. Classes are a tool that developers use to quickly produce similar objects.

Take, for example, an object representing a dog named halley. This dog's name (a key) is "Halley" (a value) and has an age (another key) of 3 (another value). We create the halley object below:

```
let halley = {
  _name: 'Halley',
  _behavior: 0,

  get name() {
    return this._name;
  },

  get behavior() {
    return this._behavior;
  },

  incrementBehavior() {
    this._behavior++;
  }
}
```

Now, imagine you own a dog daycare and want to create a catalog of all the dogs who belong to the daycare. Instead of using the syntax above for every dog that joins the daycare, we can create a Dog class that serves as a template for creating new Dog objects. For each new dog, you can provide a value for their name.

As you can see, classes are a great way to reduce duplicate code and debugging time.

After we lay the foundation for classes in the first few exercises, we will introduce inheritance and static methods — two features that will make your code more efficient and meaningful.

```
// example class
class Dog {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }

  get name() {
    return this._name;
  }
  get behavior() {
    return this._behavior;
  }

  incrementBehavior() {
    this._behavior ++;
  }
}
```

```
const halley = new Dog('Halley');
console.log(halley.name); // Print name value to console
console.log(halley.behavior); // Print behavior value to console
halley.incrementBehavior(); // Add one to behavior
console.log(halley.name); // Print name value to console
console.log(halley.behavior); // Print behavior value to console
```

---

#### Constructor

In the last exercise, you created a class called Dog, and used it to produce a Dog object.

Although you may see similarities between class and object syntax, there is one important method that sets them apart. It's called the constructor method. JavaScript calls the constructor() method every time it creates a **NEW instance** of a class.

```
class Dog {
  constructor(name) {
    this.name = name;
    this.behavior = 0;
  }
}
```

- Dog is the name of our class. By convention, we capitalize and CamelCase class names.

- JavaScript will invoke the constructor() method every time we create a new instance of our Dog class.

- This constructor() method accepts one argument, name.

- Inside of the constructor() method, we use the this keyword. In the context of a class, this refers to an instance of that class. In the Dog class, we use this to set the value of the Dog instance's name property to the name argument.

- Under this.name, we create a property called behavior, which will keep track of the number of times a dog misbehaves. The behavior property is always initialized to zero.

```
class Surgeon {
  constructor(name, department) {
    //SETS name and department properties equal to your input parameters.
    this.name = name;
    this.department = department;
  }
}
```

#### Instance

Now, we're ready to create class instances. An instance is an object that contains the property names and methods of a class, but with unique property values. Let's look at our Dog class example.

```
class Dog {
  constructor(name) {
  this.name = name;
  this.behavior = 0;
}
}
```

```
const halley = new Dog('Halley'); // Create new Dog instance

console.log(halley.name); // Log the name value saved to halley
// Output: 'Halley'
```

Another example:

```
class Surgeon {
  constructor(name, department) {
    this.name = name;
    this.department = department;
  }
}

const surgeonCurry = new Surgeon('Curry', 'Cardiovascular');
const surgeonDurant = new Surgeon('Durant', 'Orthopedics');
```

#### Methods

At this point, we have a Dog class that spins up objects with name and behavior properties. Below, we will add getters and a method to bring our class to life.

Class method and getter syntax is the same as it is for objects **except you can not include commas between methods**.

```
class Dog {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }

  get name() {
    return this._name;
  }

  get behavior() {
    return this._behavior;
  }

  incrementBehavior() {
    this._behavior++;
  }
}
```

In the example above, we add getter methods for name and behavior.

**NOTE:** we also prepended our property names with underscores (\_name and \_behavior), which indicate these properties should not be accessed directly.

Under the getters, we add a method named .incrementBehavior(). When you call .incrementBehavior() on a Dog instance, it adds 1 to the \_behavior property.

**Between each of our methods, we did not include commas.**

```
let nikko = new Dog('Nikko'); // Create dog named Nikko
nikko.incrementBehavior(); // Add 1 to nikko instance's behavior
let bradford = new Dog('Bradford'); // Create dog name Bradford
console.log(nikko.behavior); // Logs 1 to the console
console.log(bradford.behavior); // Logs 0 to the console
```

---

### Inheritance

(Parent Class / Super class and Child Class / Sub Class )

When multiple classes share properties or methods, they become candidates for inheritance — a tool developers use to decrease the amount of code they need to write.

With inheritance, you can create a **parent class** (also known as a **superclass**) with properties and methods that multiple **child classes** (also known as **subclasses**) share. The child classes inherit the properties and methods from their parent class.

See image in Assets folder:

This shit makes zero sense.
https://www.codecademy.com/courses/learn-javascript-classes/lessons/classes/exercises/inheritance-iii?action=resume_content_item&course_redirect=introduction-to-javascript
