# Technical Interview Topics

Let's be honest, computer science and technical interviews are hard. I'm just a girl trying to create a place to gather a list of topics to review to prep for those interviews and navigate the field of CS as a whole. Feel free to contribute ideas if I'm missing anything! (and I absolutely have)

* [4 Principles of Object Oriented Programming](#principles-of-object-oriented-programming)
* [Java Keywords](#java-keywords)
* Run Time Analysis
* [Data Structures](#data-structures)
  * [Arrays](#arrays)
  * [Hash Tables, HashSets, and HashMaps](#hash-tables-hashsets-and-hashmaps)
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

**Note: If you have any good videos that really helped you understand how a data structure works, add it or let me know and I'll put it on here!**

### Arrays

```
// Empty int array
int[] myEmptyArray = new int[];

// Array of size n
int[] myArray = new int[n];

// Array with specific items in it
int[] myArrayWithItems = new int[]{ 1,2,3,4,5 };

// To insert something, if 0 <= i < n
myArray[i] = 6;
```

A linear data structure, arrays are created with a fixed length. Information is stored in consecutive locations in memory, so it's easy to iterate forwards or backwards using indexes, which can be used to access any item in the array. Because of this, for loops go hand-in-hand with arrays.

| Function  | Time | Explanation |
| --------  | ---- | ----------- |
| Access | O(1) | One of the best things about arrays, if the location (index) is known, the datum can be accessed in constant time. |
| Search (with Linear Search) | O(n) | Unfortunately, if we don't know where the datum of interest is, we have to look through our array, index by index. We potentially have to go through the entire array, so this takes linear time. |
| Search (with Binary Search) | O(nlogn) | **-If-** we can sort the objects in our array, we can shorten the sort time using binary search to look for our datum. |
| Insert | O(n) | To insert an object, we must create a new array of size *n*+1, then populate the new array with the old values plus the new value. |
| Delete  | O(n) | To delete from an array, we must follow a similar procedure as insertion for a new array of size *n*-1. |

I personally like to think of arrays like a row of cubbies. If you know where something is, you just reach in and grab it, otherwise you must look through each one. To "delete" or "add" a cubby, you have to find a new row of cubbies of the right size, and move everything over, again going through each cubby once.

### Hash Tables, HashSets, and HashMaps
HashSets and HashMaps are great tools for technical interviews! However, it's important to understand the difference between the two before using them. For some quick background, HashSets and HashMaps rely on hashing functions, which essentially assigns an integer "key" to each input, which is calculated based on the input itself. The key is then used to place the item in a slot of a table corresponding to the key

If different items somehow recieve the same "key" a collision will occur because both objects will be put in the same spot - there are 2 main ways to handle this:

1. **Chaining**: If a collision occurs, append the colliding items together in a list.

2. **Open Addressing**: If a value already exists at the corresponding spot, search for the next empty spot in the table and put the value there.
   
   
But that isn't as important for technical interviews. HashSets and HashMaps are great for getting items in constant time without knowing a specific index or location on the items. Items can also be easily added and removed. The downside to both is that items are more difficult to iterate through if that's necessary, and if *space* is a concern, HashSets and HashMaps may not be ideal. Also, if items are not hashed well (ie. all items have the same hash, and therefore end up chained together in one long list) search, insert, and delete are inflated back to linear time because you may have to go through all of the stored items.

| Function | Time (avg) | Time (worst case) | Explanation |
| -------- | ---------- | ----------------- | ----------- |
| Search   | O(1)       | O(n)              | Given an item to find/access, by running it through the same hash function, we can determine where it would've been stored and check to see if that item does indeed exist there. If items all get the same hash, the function must then go through each item stored in the table or list and determine if the item exists. |
| Insert   | O(1)       | O(n)              | Same idea as search, can generate a hash for the item and place it in the corresponding spot. |
| Delete   | O(1)       | O(n)              | Same idea as search and insert. |
   
#### HashSets
HashSets can only store unique items. If you try to add a duplicate, the add method will return `false`. It's good for holding a collection of items and for checking if you already have something in your collection or not.

```
// HashSet of ints
HashSet<Integer> myHashSet = new HashSet<Integer>();

// Adding to your HashSet
myHashSet.add(5);
myHashSet.add(2);

// Checking if our HashSet contains a value
boolean containsAFive = myHashSet.contains(5); // containsAFive = true
boolean containsASix = myHashSet.contains(6);  // containsASix = false

// Get the number of items in our HashSet
int numItems = myHashSet.size()  // numItems = 2;

// Remove an item
boolean removedTwo = myHashSet.remove(2);        // removedTwo = true
boolean removedTwoAgain = myHashSet.remove(2);   // removedTwoAgain = false, it didn't exist in our set to remove
```

#### HashMaps
HashMaps, unlike HashSets, rely on **Key-Value Pairs**. For a typical HashMap, duplicate values can be stored as long as they have unique keys attached to them. However, if you tried to add a key-value pair when the key already exists in the map, it would overwrite the key-value pair at that spot.

It's very easy to check if a HashMap contains a specific key, though much more difficult to check if a specific value exists within a map. If you'll be frequently looking for certain values, you'll want to store those values as keys - if that doesn't work well for you, you may need to consider a different data structure.

```
// HashMap mapping ints to Strings
HashMap<Integer, String> myHashMap = new HashMap<Integer, String>();

// Put new key-value pairs in our map
myHashMap.put(2, "hello");

// Check if the map contains certain keys or values
boolean containsKeyTwo = myHashMap.containsKey(2);     // containsKeyTwo = true
boolean containsValHi = myHashMap.containsValue("hi")  // containsValHi = false

// Get the value attached to a specfic key
String val = myHashMap.get(2);

// Remove a key-value pair
boolean removed = myHashMap.remove(2);   // removed = true

// other functions include size(), keySet(), replace(key, val), etc
```
