# Class to Class Messaging

## Learning Goals

- Recognize common terminology for describing Object Oriented relationships

## Introduction

In Object Oriented design, we can have many classes interacting with each other.
The _interaction_ typically involves one class utilizing behaviors or properties
of another class. These interactions are often referred to as **_messages_** in
Object Orientation.

In this lesson, we're going to discuss some of the common terms used when
describing an Object Oriented app. These terms can help us to better define
_what_ a particular class is doing and _how_ it does what it does.

## Details of a Message

In OO design, we define the interactions, the _messaging_, between classes.
Each message requires a few things:

- A message requires two classes, one that initiates the message and
  the other that responds and behaves accordingly.

- The class that initiates a message needs to have access to the class that
  is responding. In most of the labs in this section, this is achieved by
  assigning an instance of one class to the property of another.

```js
class Engine {
	constructor() {
		this.running = false;
	}

	// start assigns the `running` property to true, then returns this property
	start() {
		this.running = true;
		return this.running;
	}
}

class Car {
	constructor(engine = new Engine()) {
		this.engine = engine;
	}

	// this method will call `start()` on the engine instance, returning what `start()` returns
	turnKey() {
		return this.engine.start();
	}
}

let subaru = new Car();

subaru.turnKey();
// => True
```

Above, a `Car` instance is created with an `engine` property. `Car` has the
ability to send a message to `engine`, calling `start()`. It does this through
`turnKey()`.

## Describing Classes by their Role in Messaging

Depending on how classes interact and collaborate, we sometimes refer to classes
as being one of three types: Actor, Server, and Agent.

In the previous example, the `Car` class _acts_ on the `Engine` class, and so is
considered an _Actor_. The `Engine` class _serves_ the requested behavior, and
is referred to as a _Server_. A class that can both act on something in another
class _and_ serve something on request is called an _Agent_.

## The Benefit of Thinking in Messages

Thinking of class relationships as _messages_ sent from one class to another
emphasizes _how_ an Object Oriented app should function.

Classes are _encapsulations_ of related data and behavior. Messages You can
imagine them as independent _cells_. Each cell has its own _cell wall_, intended
to protect the code inside from being used in a way we do not want.

Messages are similar. _We_ define how a class can interact with the outside.
Each interaction is a **message**, only relevant to the actor and server.
Messages are isolated. A method like `turnKey()` in the `Car` and `Engine`
example can't be used for any other purpose other than having a `Car` act on an
`Engine`.

## Conclusion

It isn't necessary to think in terms of messages. We can still build OO
applications without knowing what things are called. However, this terminology
helps to further our understanding of Object Oriented design.
