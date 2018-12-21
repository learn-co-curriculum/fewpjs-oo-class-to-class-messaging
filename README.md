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
Each message involes a few things:

- A message requires two classes, one that initiates the message and
  the other that responds and behaves accordingly.

- The class that initiates a message needs to have access to the class that
  is receiving it. This is often achieved by assigning an instance of one 
  class to the property of another. The sender of a message is the one that
  maintains the dependency between the two classes.
  
  Take the following two classes, for example:

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

Above, a `Car` instance is created with an `engine` property. In the `Car`
class, `turnKey()` implements `this.engine.start()`. `Car` is now
dependent on the `start()` method contained within `Engine`. It is through
the `turnKey()` method that `Car` can now communicate with `Engine`. 

Every time `subaru.turnKey()` is called, the `subaru` instance is sending a
message to its personal instance of `Engine`.

## Describing Classes by their Role in Messaging

Depending on how classes interact and collaborate, some might only send messages,
some might only receive, and others may do both. Based on their behavior,
we sometimes refer to classes as being one of three types: Actor, Server, and Agent.

In the previous example, the `Car` class _acts_ on the `Engine` class, and so is
considered an _Actor_. The `Engine` class _serves_ the requested behavior, and
is referred to as a _Server_. A class that can both act on something in another
class _and_ serve something on request is called an _Agent_.

## The Benefits of Thinking that Classes Send Messages

Thinking in terms of messages being sent from one class to another
emphasizes the importance of the structure of an Object Oriented application.
All relationships between classes are dependencies. Thinking in messages informs 
us of the exact _type_ of relationship two classes share. As an application
grows, we end up thinking less about specific classes and their functions
and more about how those classes interact and form a larger whole.

Classes and their messages together can be represented visually, which can help us
design from a general perspective before we even begin writing code. Imagine, for
instance, we wanted to design an application to help organize a library's
books. The end result might involve many classes and dependencies. Drawing out
a map of classes and messages we might start with something like the following:

<img src="https://curriculum-content.s3.amazonaws.com/fewpjs/fewpjs-class-relationships/library_shelf_books_author_genre.png" width= 50% alt="image representing dependencies"/>

## Conclusion

It isn't necessary to think in terms of messages. We can still build OO
applications without knowing what things are called. However, this terminology
helps to further our understanding of Object Oriented design.
