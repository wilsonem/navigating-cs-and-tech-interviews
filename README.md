# Technical Interview Topics

Let's be honest, computer science and technical interviews are hard. I'm just a girl trying to create a place to gather a list of topics to review to prep for those interviews and navigate the field of CS as a whole. Feel free to contribute ideas if I'm missing anything! (and I absolutely have)

* [4 Principles of Object Oriented Programming](#principles-of-object-oriented-programming)
* [Java Keywords](#java-keywords)
* Run Time Analysis
* [Data Structures](#data-structures)
  * Arrays
  * HashSets and HashMaps
  * Stacks and Queues
  * Lists, LinkedLists, and ArrayLists
  * Graphs
  * Binary Search Trees
* Sorting
* Greedy Algorithms (?)
* Recursion
* DFS and BFS
* Different Coding Languages

## Principles of Object Oriented Programming

Check out this [CodeBetter.com link](http://codebetter.com/raymondlewallen/2005/07/19/4-major-principles-of-object-oriented-programming/)

### Encapsulation
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

### Data Abstraction
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

### Polymorphism


### Inheritance
Think of having a base class. For example, all birds have feathers, a beak, and lay eggs. However some live in different locations, and some have the ability to swim or sing.


## Java Keywords
### Static
* If a method is dependent on an instance variable in the class, do not make it a static method.
* Static methods belong to the class, while non-static methods belong to objects in the class.
* Getters and setters are not static because they rely on instance variables, while a method that just prints out "hello, world" would be static.
  
  
## Data Structures
Data structures provide ways to help organize stored information. Each has pros and cons, and which you should use depends on the functions that you need.

Big things to consider are the times required for accessing, searching for, inserting, and deleting data from a structure.

### Arrays
A linear data structure, arrays are created with a fixed length. Information is stored in consecutive locations in memory, so it's easy to iterate forwards or backwards using indexes, which can be used to access any item in the array

| Function  | Time | Explanation |
| --------  | ---- | ----------- |
| Accessing | O(1) | One of the best things about arrays, if the location (index) is known, the datum can be accessed in constant time. |
| Searching (with Linear Search) | O(n) | Unfortunately, if we don't know where the datum of interest is, we have to look through our array, index by index. We potentially have to go through the entire array, so this takes linear time. |
| Searching (with Binary Search) | O(nlogn) | **If** we can sort the objects in our array, we can shorten the sort time using binary search to look for our datum. |
| Insertion | O(n) | To insert an object, we must create a new array of size *n*+1, then populate the new array with the old values plus the new value. |
| Deletion  | O(n) | To delete from an array, we must follow a similar procedure as insertion for a new array of size *n*-1. |
