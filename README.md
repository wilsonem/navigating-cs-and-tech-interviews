# Technical Interview Topics
Just a place to gather a list of topics to review for technical interviews. Feel free to contribute ideas if I'm missing anything!

* [4 Principles of Object-Oriented Programming](#Principles-of-Object---Oriented-Programming)
* [Java Keywords](#java-keywords)
* Stacks and Queues
* Arrays
* LinkedLists
* HashSets and HashMaps
* Graphs
* DFS and BFS
* Binary Search Trees
* Greedy Algorithms (?)
* Recursion

## Principles of Object-Oriented Programming

Check out this [CodeBetter.com link](http://codebetter.com/raymondlewallen/2005/07/19/4-major-principles-of-object-oriented-programming/)

#### Encapsulation
Access to data within classes should be restricted to accessors (get) and mutators (set).
```
public class Person {
  private String firstName;
  
  public String getFirstName() {
    return this.firstName();
  }
  
  public void setFirstName(String name) {
    this.firstName = name;
  }
}
```

#### Data Abstraction
Abstraction is breaking down complex systems into simpler pieces. Think of describing the general population by 1 person.
Each person has a name, height, age, and can do tasks like walking and eating.
```
public class Person {
  private String name;
  private int age;
  private double height;
  private boolean canRead;
  
  public String getName() {
    return this.name;
  }
  
  public void setName(String newName) {
    this.name = newName;
  }
  
  // ...
  
  public static void walk() {
    // code that makes the person walk
  }
  
```

#### Polymorphism

#### Inheritance


## Java Keywords
* Static
  * If a method is dependent on an instance variable in the class, do not make it a static method.
  * Static methods belong to the class, while non-static methods belong to objects in the class.
  * Getters and setters are not static because they rely on instance variables, while a method that just prints out "hello, world" would be static.
  
  
  
