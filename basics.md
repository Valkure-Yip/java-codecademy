# Java basics - codecademy tutorial



main func:

```java
public class HideAndSeek {
  public static void main(String[] args) {
    System.out.println("Let's play hide and seek.");
  }
}
```

console print:

```java
System.out.println() // newline
System.out.print() // no line break
```



compile cmd:

```bash
$ javac Welcome.java
```

produce `Welcome.class`

run compiled (no suffix!):

```bash
$ java Welcome
```



### primitive types

- **byte**: The `byte` data type is an 8-bit signed two's complement integer. It has a minimum value of -128 and a maximum value of 127 (inclusive). The `byte` data type can be useful for saving memory in large [arrays](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/arrays.html), where the memory savings actually matters. They can also be used in place of `int` where their limits help to clarify your code; the fact that a variable's range is limited can serve as a form of documentation.
- **short**: The `short` data type is a 16-bit signed two's complement integer. It has a minimum value of -32,768 and a maximum value of 32,767 (inclusive). As with `byte`, the same guidelines apply: you can use a `short` to save memory in large arrays, in situations where the memory savings actually matters.
- **int**: By default, the `int` data type is a 32-bit signed two's complement integer, which has a minimum value of -231 and a maximum value of 231-1. In Java SE 8 and later, you can use the `int` data type to represent an unsigned 32-bit integer, which has a minimum value of 0 and a maximum value of 232-1. Use the Integer class to use `int` data type as an unsigned integer. See the section The Number Classes for more information. Static methods like `compareUnsigned`, `divideUnsigned` etc have been added to the [`Integer`](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html) class to support the arithmetic operations for unsigned integers.
- **long**: The `long` data type is a 64-bit two's complement integer. The signed long has a minimum value of -263 and a maximum value of 263-1. In Java SE 8 and later, you can use the `long` data type to represent an unsigned 64-bit long, which has a minimum value of 0 and a maximum value of 264-1. Use this data type when you need a range of values wider than those provided by `int`. The [`Long`](https://docs.oracle.com/javase/8/docs/api/java/lang/Long.html) class also contains methods like `compareUnsigned`, `divideUnsigned` etc to support arithmetic operations for unsigned long.
- **float**: The `float` data type is a single-precision 32-bit IEEE 754 floating point. Its range of values is beyond the scope of this discussion, but is specified in the [Floating-Point Types, Formats, and Values](https://docs.oracle.com/javase/specs/jls/se7/html/jls-4.html#jls-4.2.3) section of the Java Language Specification. As with the recommendations for `byte` and `short`, use a `float` (instead of `double`) if you need to save memory in large arrays of floating point numbers. This data type should never be used for precise values, such as currency. For that, you will need to use the [java.math.BigDecimal](https://docs.oracle.com/javase/8/docs/api/java/math/BigDecimal.html) class instead. [Numbers and Strings](https://docs.oracle.com/javase/tutorial/java/data/index.html) covers `BigDecimal` and other useful classes provided by the Java platform.
- **double**: The `double` data type is a double-precision 64-bit IEEE 754 floating point. Its range of values is beyond the scope of this discussion, but is specified in the [Floating-Point Types, Formats, and Values](https://docs.oracle.com/javase/specs/jls/se7/html/jls-4.html#jls-4.2.3) section of the Java Language Specification. For decimal values, this data type is generally the default choice. As mentioned above, this data type should never be used for precise values, such as currency.
- **boolean**: The `boolean` data type has only two possible values: `true` and `false`. Use this data type for simple flags that track true/false conditions. This data type represents one bit of information, but its "size" isn't something that's precisely defined.
- **char**: The `char` data type is a single 16-bit Unicode character. It has a minimum value of `'\u0000'` (or 0) and a maximum value of `'\uffff'` (or 65,535 inclusive).



#### `String`: object

compare objects: `.equals()`

```java
String person1 = "Paul";
String person2 = "John";
String person3 = "Paul";
 
System.out.println(person1.equals(person2));
// Prints false, since "Paul" is not "John"
 
System.out.println(person1.equals(person3));
// Prints true, since "Paul" is "Paul"
```



#### `==` vs `equals()`

[Difference Between == and .equals() Method in Java - GeeksforGeeks](https://www.geeksforgeeks.org/difference-between-and-equals-method-in-java/#:~:text=In%20simple%20words%2C%20%3D%3D%20checks,that%20has%20overridden%20this%20method.)

In simple words, == checks if both objects point to the same memory location whereas .equals() evaluates to the comparison of values in the objects.

If a class does not [override the equals method](https://www.geeksforgeeks.org/overriding-equals-method-in-java/), then by default, it uses the equals(Object o) method of the closest parent class that has overridden this method.

```java
String s1 = "HELLO";
String s2 = "HELLO";
String s3 =  new String("HELLO");

System.out.println(s1 == s2); // true
System.out.println(s1 == s3); // false
System.out.println(s1.equals(s2)); // true
System.out.println(s1.equals(s3)); // true
```

**Explanation:** Here, we create two objects, namely s1 and s2. 

- Both s1 and s2 refer to same objects.

- When we use the == operator for s1 and s2 comparison, the result is true as both have the same addresses in the string constant pool.

- Using equals, the result is true because it’s only comparing the values given in s1 and s2.

Java String Pool

| s1 = “HELLO” |
| ------------ |
| s2 = “HELLO” |

Java Heap

s3 = “HELLO”



### `final` keyword

To declare a variable with a value that cannot be manipulated, we need to use the `final` keyword

```java
final int yearBorn = 1968;
yearBorn = 1990; // error: cannot assign a value to final variable yearBorn
```



## Class

structure

```java
public class Store {
  // instance fields
  String productType;
  int inventoryCount;
  double inventoryPrice;
  
  // constructor method
  public Store(String product, int count, double price) {
    productType = product;
    inventoryCount = count;
    inventoryPrice = price;
  }
  
  // main method
  public static void main(String[] args) {
    Store lemonadeStand = new Store("lemonade", 42, .99);
    Store cookieShop = new Store("cookies", 12, 3.75);
    
    System.out.println("Our first shop sells " + lemonadeStand.productType + " at " + lemonadeStand.inventoryPrice + " per unit.");
    
    System.out.println("Our second shop has " + cookieShop.inventoryCount + " units remaining.");
  }
}
```



constructor overload:

```java
public class Car {
  String color;
  int mpg;
  boolean isElectric;
 
  // constructor 1
  public Car(String carColor, int milesPerGallon) {
    color = carColor;
    mpg = milesPerGallon;
  }
  // constructor 2
  public Car(boolean electricCar, int milesPerGallon) {
    isElectric = electricCar;
    mpg = milesPerGallon;
  }
}
```



`.toString()` method: 自定义`System.out.println(obj)`的表现

When we define a *toString()* method for a class, we can return a `String` that will print when we print the object:

```java
class Car {
 
    String color;
 
    public Car(String carColor) {
        color = carColor;
    }
 
    public static void main(String[] args){
        Car myCar = new Car("red");
        System.out.println(myCar);
    }
 
   public String toString(){
       return "This is a " + color + " car!";
   }
}
```

When this runs, the command `System.out.println(myCar)` will print `This is a red car!`, which tells us about the Object `myCar`.



### this` keyword

The `this` keyword is a reference to the current object. 



### static methods & variables

- Static methods and variables are associated with the class as a whole, not objects of the class.
- Static methods and variables are declared as static by using the `static` keyword upon declaration.
- Static methods cannot interact with non-static instance variables. This is due to static methods not having a `this` reference.
- Both static methods and non-static methods can interact with static variables.

Math **static method:**

```java
double randomNumber = Math.random();
// Stores a random decimal between 0.0 and 1.0 in randomNumber

```

We didn’t need to create a `Math` object (like `Math myMathObject = new Math()`) in order to use that method. We could just call it using the class name.

notice that our `main()` methods have been `static` this whole time. When Java runs your program, it calls that the main method of your class — `YourClassName.main()`.

**static variable:**

```java
public class Dog{
 
  // Static variables
  public static String genus = "Canis";
 
  //Instance variables
  public int age;
  public String name;
 
  public Dog(int inputAge, String inputName){
    this.age = inputAge;
    this.name = inputName;
  }
}
```

you can still access static variables from a specific object of the class. However, no matter what object you use to access the variable, the value will always be the same. You can think of it as all objects of the class sharing the same variable

尽量不用this关键词来访问static variable， 除非有本地变量同名



### inheritance

```java
public class Ramen extends Noodle {
  Ramen() {  
    super(30.0, 0.3, "flat", "wheat flour");  
  }
```

<img src="https://content.codecademy.com/courses/learn-java/revised-2019/access-modifiers-chart.png" alt="public is visible everywhere; protected is visible in the class, the package, and child classes; a member with no modifier is visible in the class and package; private is visible only in the class itself" style="zoom:20%;" />



**`final`**

If we add `final` before a parent class method’s access modifier, we disallow any child classes from changing that method.

```java
final public boolean isTasty() {

  return true;

}
```



### polymophism





## Conditional control

`&&, ||`:

On some occasions, the compiler can determine the truth value of a logical expression by only evaluating the first `boolean` operand; this is known as *short-circuited evaluation*. Short-circuited evaluation only works with expressions that use `&&` or `||`.



## Array

```java
double[] prices = {13.15, 15.87, 14.22, 16.66};
```

array package：

```java
import java.util.Arrays;
```

Print array with `Arrays.toString()`

```java
String[] topics = sampleFeed.getTopics();
System.out.println(topics);
System.out.println(Arrays.toString(topics));
```

```
[Ljava.lang.String;@2aae9190
[Opinion, Tech, Science, Health]
```

**Creating an Empty Array**

We can also create empty arrays and then fill the items one by one. Empty arrays have to be initialized with a fixed size:

```java
String[] menuItems = new String[5];
```

Once you declare this size, it cannot be changed!

When we use `new` to create an empty array, each element of the array is initialized with a specific value depending on what type the element is:

| Data Type | Initialized Value |
| --------- | ----------------- |
| int       | `0`               |
| double    | `0.0`             |
| boolean   | `false`           |
| Reference | `null`            |

For example, consider the following arrays:

```java
String[] my_names = new String[5];
int[] my_ages = new int[5];
```

Because a String is a reference to an Object, `my_names` will contain five `null`s. `my_ages` will contain five `0`s to begin with.

### main function String[] args

```java
public class HelloYou {
  public static void main(String[] args) {
    System.out.println("Hello " + args[0]);  
  }
}
```

```bash
$ java HelloYou Laura
```

Output:

```
Hello Laura
```



## ArrayList

```java
import java.util.ArrayList;
```

To create mutable and dynamic lists, we can use Java’s `ArrayList`s. `ArrayList`s allow us to:

- Store object references as elements
- Store elements of the same type (just like arrays)
- Access elements by index (just like arrays)
- Add elements
- Remove elements

`<` and `>` to declare the type of the `ArrayList`. These symbols are used for *generics*. 

**do not use primitive types for generics**

```java
// This code won't compile:
ArrayList<int> ages;
 
// This code will compile:
ArrayList<Integer> ages;
```

```java
// Declaring:
ArrayList<Integer> ages;
// Initializing:
ages = new ArrayList<Integer>();
 
// Declaring and initializing in one line:
ArrayList<String> babyNames = new ArrayList<String>();
```

**ArrayList.add(item)**

```java
ArrayList<Car> carShow = new ArrayList<Car>();
 
carShow.add(ferrari);
// carShow now holds [ferrari]
carShow.add(thunderbird);
// carShow now holds [ferrari, thunderbird]
carShow.add(volkswagen);
// carShow now holds [ferrari, thunderbird, volkswagen]
```

```java
// Insert object corvette at index 1
carShow.add(1, corvette);
// carShow now holds [ferrari, corvette, thunderbird, volkswagen]
 
// Insert object porsche at index 2
carShow.add(2, porsche);
// carShow now holds [ferrari, corvette, porsche, thunderbird, volkswagen]
```

**ArrayList.size()**

```java
ArrayList<String> shoppingCart = new ArrayList<String>();
 
shoppingCart.add("Trench Coat");
System.out.println(shoppingCart.size());
// 1 is printed
shoppingCart.add("Tweed Houndstooth Hat");
System.out.println(shoppingCart.size());
// 2 is printed
shoppingCart.add("Magnifying Glass");
System.out.println(shoppingCart.size());
// 3 is printed
```

**ArrayList.get(idx)**

```java
ArrayList<String> shoppingCart = new ArrayList<String>();
 
shoppingCart.add("Trench Coat");
shoppingCart.add("Tweed Houndstooth Hat");
shoppingCart.add("Magnifying Glass");
 
System.out.println(shoppingCart.get(2));
```

**ArrayList.set(idx, item)**

```java
shoppingCart.add("Trench Coat");
shoppingCart.add("Tweed Houndstooth Hat");
shoppingCart.add("Magnifying Glass");
 
shoppingCart.set(0, "Tweed Cape");
```

**ArrayList.remove(item)**

```java
shoppingCart.add("Trench Coat");
shoppingCart.add("Tweed Houndstooth Hat");
shoppingCart.add("Magnifying Glass");
 
shoppingCart.remove("Trench Coat");
```

**ArrayList.indexOf(item)**

## Loop

### for-each loop

```java
for (String inventoryItem : inventoryItems) {
  // Print element value
  System.out.println(inventoryItem);
 
}
```

Our enhanced loop contains two items: an enhanced `for` loop variable (`inventoryItem`) and a list to traverse through (`inventoryItems`).

We can read the `:` as “in” like this: for each `inventoryItem` (which should be a `String`) in `inventoryItems`, print `inventoryItem`.

If we try to assign a new value to the enhanced `for` loop variable, the value stored in the array or `ArrayList` will not change. This is because, for every iteration in the enhanced loop, the loop variable is assigned **a copy of the list element**.



### remove element from ArrayList during loop

all elements will shift left by 1, DO NOT increment index after removal

```java
int i = 0; // initialize counter
 
while (i < lst.size()) {
  // if value is odd, remove value
  if (lst.get(i) % 2 != 0){
    lst.remove(i);
  } else {
    // if value is even, increment counter
    i++;
  }
}
```

```java
for (int i = 0; i < lst.size(); i++) {
  if (lst.get(i) == "value to remove"){
    // remove value from ArrayList
    lst.remove(lst.get(i));
    // Decrease loop control variable by 1
    i--;    
  }
}
```



## String method

- `length()`
- `concat()`
- `equals()`
- `indexOf()`
- `charAt()`
- `substring()`
- `toUpperCase()` / `toLowerCase()`
- `compareTo():int`

We can also compare `String` values lexicographically (think dictionary order) using the `.compareTo()` method. When we call the `.compareTo()` method, each character is in the `String` is converted to Unicode; then the Unicode character from each `String` is compared.

```java
String flavor1 = "Mango";
String flavor2 = "Peach";
 
System.out.println(flavor1.compareTo(flavor2)); 
```

Our program above will output `-3`.

When we use `.compareTo()`, we must pay attention to the return value:

- If the method returns `0`, the two `String`s are equal.
- If the value is less than `0`, then the `String` object is lexicographically less than the `String` object argument.
- If the value is greater than `0`, then the `String` object is lexicographically greater than the `String` object argument.

## Access & Scope

`public` & `private`

### `this` keyword

The `this` keyword is a reference to the current object. 

