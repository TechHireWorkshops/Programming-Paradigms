# Programming Paradigms

## What are programming paradigms?

Programming paradigms are the different ways that we can classify programming languages based on different criteria. Some languages can be of several paradigms depending on the classification system.

Some paradigms are defined by syntax, some by how the code is grouped into units, some by how state is managed, and some by the execution model. 

Some argue that languages themselves are not defined by paradigms, as paradigms are simply patterns of writing code, and we decide on what paradigms to use based on how we choose to write code.  However, most languages are designed in such a way that they naturally dictate that the code follow certain paradigms. Very few languages or programs are pure, meaning they have aspects or multiple paradigms.

## The largest distinction - Declarative vs. Imperative

### Imperative Programming

Imperative programming is the type of coding that's we're most familiar with.  In imperative programming, the coders writes the steps that they want to program to follow.  This might sound obvious, and it might be hard to think of what the alternative to this would be.  We'll see that in a moment.

In imperative programming, we make direct changes to the properties of what we're working with. We change state with assignment statements explicitly. 

### Declarative Programming

In declarative programming, the programmer declares the desired result, but doesn't write the steps the language needs to take to achieve this. This sounds a little strange, but is more common than you think.

Let's look at this function meant to see if a certain element is contained in an array:

```javascript

	const isItInThere=(arr,element)=>{
		for(let i = 0; i<arr.length;i++){
			if (arr[i]===element){
			return true
			}
		}
		return false
	}

```

This is an imperative function. We define what the program is meant to do in detail: We tell it to loop through the array, check each element in the array against the desired element, and return either true or false depending on if we find it.

Let's look at the declarative version of this:

``` javascript
	const isItInThere=(arr, element)=>{
		return arr.includes(element)
	}
```

In this case, we don't direct the program on how to search for the element, we just tell it what we want to find and let it do it's thing.

Declarative programming is often easier to write than imperative, though it's often less efficient.

## Declarative Paradigms

### Logic Programming

![](https://qph.fs.quoracdn.net/main-qimg-f880ac7afe84ebdf06bba8c4927cd413)

Logic programming, also known as constraint programming, is a paradigm of programming where program statements express rules and statements or truth or equality.  These languages follow the rules of formal logic.

We define the rules and relationships between our variables and concepts, and the rules on how to evaluate them.  We can then query the program for values that match our criteria, or for the truth value of certain statements.

The most popular language that relies on logic programming is Prolog, which has been around since 1972.  You probably won't see much use of logic programming, though it does has applications in AI.

### Function-Oriented Programming

![](https://i.pinimg.com/736x/1e/4d/ea/1e4dea25c0bad79bb2224b57d316682f.jpg)

Function-oriented programming, or functional programming, is a programming approach that aims to simplify code and increase readability. JavaScript is a language that makes use of functional programming. It's characterized as programs that contain pure functions, where functions are composed, where the program does not rely on shared state, and where data is immutable.  What do these concepts mean?

#### Avoiding Shared State

Functional programming does not use a shared state within the application.  The application state flows through the series of function calls and is only passed through arguments.  This can allow cleaner code when we don't have to worry about the order in which state variables are being used.  We can list and call functions in any order we please, as we don't have to worry about different functions running at the same time cross-contaminating state.

#### Immutable Data

Functional programming avoids mutating data.  This is to avoid loss or confusion between functions.  For more info on this, take a look [here](https://medium.com/javascript-scene/the-dao-of-immutability-9f91a70c88cd).  Beware that in Javascript, `const` does not mean that an object is truly immutable.

#### Pure Functions

Pure functions are functions where the output of the function relies only on the input of the function.  This means, generally, that the functions does not rely on outside factors, like state or globally-scoped variables.  Pure functions also do not produce side effects, which means that it does not modify anything outside of the function.  Pure functions take an argument, work on it, and return something.

#### Function Composition

Functions within a functional programming paradigm are higher order functions.  The aspect of higher-order functions relevant here is that they can accept other functions as arguments or return other functions.  This allows the functional programmer to combine multiple functions together. In functional programming, the application generally exists as a series of small modular functions that are called from other functions and/or passed as arguments.

Let's look at an example of functional composition from [this article](https://medium.com/better-programming/functional-programming-in-javascript-introduction-and-practical-examples-d268e44395b2).  Say we want a function that converts dollar to cents.  We could write these functions:

```
const divideBy100 = num => num / 100;

const roundTo2dp = num => num.toFixed(2);

const addDollarSign = str => '$' + String(str);

const addSeparators = str => {
  // add commas before the decimal point
  str = str.replace(/(?<!\.\d+)\B(?=(\d{3})+\b)/g, `,`);
  // add commas after the decimal point
  str = str.replace(/(?<=\.(\d{3})+)\B/g, `,`);
  return str;
};
```

We can then combine these functions like so:

```
const centsToDollars=(x) => 
  addSeparators(
    addDollarSign(
      roundTo2dp(
        divideBy100(x)
      )
    )
  );
```

And then use our new combined function, centsToDollars. We can combine each of the smaller modular functions into larger ones, making our code more flexible.


## Imperative Paradigms

### Procedural Programming

Procedural programming, also called inline programming, is a style of programming where the coder writes a list of step-by-step instructions for the program to carry out. It is built around defining procedures, or routines, for the program to follow. Procedural programming is really another way to say imperative programming. 

Procedural programming is a large idea, and many parts of it are also features of other paradigms.  Like functional programming, it embraces the ideas of modularity and reusability. Procedure is another word for function.

Unlike functional programming, procedural programming can use a shared state between its procedures.  Functional programming also emphasized higher-order functions that make use of separate functions, whereas procedural programming tends to combine all of the steps in a process into once function.

Purely procedural programming is rarely in modern languages, but elements of it are involved in almost all other paradigms.  It is wordy and very explicit, and very closely reflects the actual steps the computer is doing in carrying out tasks.

### Object-Oriented Programming

![](https://memegenerator.net/img/instances/36100319.jpg)

Object-Oriented Programming is a programming paradigm in which each of the programs concerns are separated into objects. Objects are structures that contain pertinent data, and methods that are used to process data.  Objects can communicate and interact with each other.

OOP languages often model real-world concepts or things as objects within the language.  If you were building an app like airBnB, you might have an object for each rental on the site. Each of these objects would contain data, like the owner of the rental, the price of the rental, and the dates and availability.  It would also contain methods that can be used to change the object.  There may be a method to change available dates, or a method to add new pictures to the rental.

The users of the app would also be objects, with their names, email addresses, and credit card information stored as object.  In addition to methods used to edit themselves, these objects would also have methods to communicate with other objects, like the rentals.  There would be a method that communicates between the user object and the rental object to book stays, and method that works between user objects to send messages or leave ratings.

Many data types and interfaces within an OOP language are objects themselves.  In Java (and many other languages), arrays themselves are objects.  They can hold data (the elements that we put into the array), and have methods attached to them, like .length, which reads the length of the array and returns it.

In Object-Oriented Programming, we almost always define classes.  These are blueprints for the objects we will be creating.  We can then call on those classes to *instantiate* specific objects of that class' type.

![](https://miro.medium.com/max/1260/0*sJcCz-q5pIZbgmsK.png)

The main principles of Object-Oriented Programming include:

- Encapsulation
- Inheritance
- Abstraction
- Polymorphism

#### Encapsulation

Encapsulation in Object-Oriented Programming is related directly to the definition of an object.  Encapsulation means that the state and methods of each object are bound together within the object and class, and cannot by default be accessed from outside of the object (though we can allow that if we wish).  Usually, some methods within an object are publicly available, and if we wish to change an object, we must call on these methods and let the object take care of it.

The practice of encapsulation can increase security, as less information is publicly available, and can avoid unintentional data corruption.

#### Abstraction

Abstraction is closely related to encapsulation.  Abstraction is the practice of only revealing uses and data of objects to the parts of the code that needs to use it.  Like we discussed above, objects hide much of their data from other objects (and from the app's users).  It is the idea of only revealing an object's (or app's) functionality, and not its implementation.

#### Inheritance

![](https://www.astateofdata.com/wp-content/uploads/2019/10/Python-Object-Oriented-Programming-Inheritance-Schema.png)

In OOP, we can create sub-classes that descend from parent classes.  These sub-classes inherit all of the data and method from their parent class, and can add additional data and methods that are specific to that subclass.

Think back to geometry, where we learned that a polygon is a shape with straight sides, a rectangle is a polygon with 4 sides and 4 right angles, and a square is a rectangle where all the sides are the same length.  This is the concept of inheritance.  The square is a sub-class of the rectangle (with its own extra features), which is in turn a subclass of a polygon (with its own extra features).

#### Polymorphism

Polymorphism is the ability of objects or functions to take more than one form depending on their context.

There are two main types of polymorphism:

- Static polymorphism
- Dynamic Polymorphism

##### Static Polymorphism

This is polymorphism that is resolved during compiling.  A common type of static polymorphism is **method overloading**, where we can write multiple methods with the same name but different lists of arguments.  an example:

```
class Calculator {
    void add(int a, int b) {
         System.out.println(a+b);
    }
    void add(int a, int b, int c) {
         System.out.println(a+b+c);
    }
}
public class Demo {
   public static void main(String args[]) {
       Calculator calculator = new Calculator();
       // method with 2 parameters is called
       calculator.add(10, 20); //output: 30
       // method with 3 parameters is called
       calculator.add(10, 20, 30); //output: 60
   }
}
```

##### Dynamic Polymorphism

Also known as run-time polymorphism, dynamic polymorphism is usually seen when both a class and a subclass have the same method, and one or the other needs to be selected.  an example:

```
class Person {    
   public void teach(){
      System.out.println("Person can't teach");
   }
}

class Teacher extends Person {
   public void teach() {
      System.out.println("Teacher can teach in a school");
   }
}

public class TestTeacher {
   public static void main(String args[]) {
      Person person = new Person(); //Person reference and object
      Person another_person = new Teacher(); //Person reference, Teacher object
      Teacher teacher = new Teacher(); //Teacher reference and obj.
      
      person.teach();
      //output: Person can't teach
      
      teacher.teach();
      //output: Teacher can teach in a school
       
      another_person.teach();
      //output: Teacher can teach in a school
      // Here you can see Teacher object's method is executed even though the Person reference was used 
   }
}
```