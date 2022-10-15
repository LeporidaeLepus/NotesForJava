# Java

## Naming Conventions

Variables and method names:

- Use lowercase for the first word, and capitalize the first letter of each subsequent word in the name.

Class names:

- Capitalize the first letter of each word in the name.

Constants:

- Capitalize all letters in constants, and use underscores to connect words.  

## Variables

### char

- Single quotes `''` are only used for Characters.

### floating-point number

- floating-point numbers are not stored with complete accuracy.
  - Don't use floating-point valus for equality checking.
- By default, a floating-point literal is treated as double type value.
- The double types values are more accurate than the float type values.

#### double

- You can make a number double by appending the letter D or d.

#### float

- You can make a number float by appending the letter F or f.

### long

- To denote an integer **literal** of the long type, append it with the letter L or l. (L is preferred)

### constans

- **final** datatype CONSTANTNAME = VALUE;

&nbsp;

## Datatypes

### Conversion Rules

When performing a binary operation involving two operands of different types:

- double > float > long > int

### Type Casting

- Implicit casting:
  - type widening
- Explicit casting:
  - type narrowing;
  - fraction part is truncated
  > e.g. `int i = (int) 3.9;`

range inreases --> :  
byte < short < int < long < float < double

> Common Error: Unintended Integer Division
>
> ```java
> int num1 = 1;
> int num2 = 2;
> double ave = (num1 + num2) / 2;
> ```

Casting in an Augmented Expression:

- In Java, an augmented expression of the form x1 op= x2 is implemented as x1 = (T)(x1 op x2), where T is the type for x1.

&nbsp;

## Control Statements

### Switch

```java
switch(switch-expression){
    case value1: statement(s)1;
    case value2: statement(s)2;
    ......
    default: statement(s)-for-default;
}
```

&nbsp;

## Array

When  an  array  is  created,  its  elements  are assigned the default value of 0 for the numeric primitive data types:

- `'\u0000'` for `char` types, and
- `false` for `boolean` types.

### Copying Arrays

`arr1 = arr2` can only copy the reference of an array but not the contents. To copy the contents of an array:

- using `for` loop
- the ***arraycopy*** utility: `System.arraycopy(sourceArray, src_pos, targetArray, tar_pos, length);`

### Passing Arrays to Methods

In Java, passing a variable to methods is **passing the value** of the variable to methods, *the origin variable will not be changed*;  
While passing arrays to methods is **passing the reference** to methods, the memory will be changed if we change an array in methods and *the original array will be changed*.

&nbsp;

## Scanner

```java
Scanner input = new Scanner(System.in);
DATATYPE variable = input.next();
DATATYPE variable = input.nextLine();
......
```

&nbsp;

## String

> ### Instance Methods *vs.* Static Methods
>
> - **Instance methods can only be invoked from a specific instance.**
> - **Static Methods can be invoked without using an object.** (e.g. Math)

- String is a **reference type.**
- String cannot be changed.

### Compare

- `obj1 == obj2` compares not only the value but also the memory.
- Using `obj1.equals(obj2)` to campare objects' value.

```java
String s1 = "Hello";
String s2 = new String("Hello");
System.out.println(s1 == s2);       // false
System.out.println(s1.equals(s2));  //true
```

### methods

`str.length();`  
`str.charAt();`

These methods return a new string:  

`str.concat();`  
`str.trim();`  
`str.toLowerCase();`  
`str.toUppercase();`  
`str.substring(begin, *end*)`

Conversion String <-> numbers:  
`Integer.parseInt(str);`  
`Double.parseDouble(str);`

&nbsp;

## Class

- Data field
- Constructor
- Methods

### `this` Keyword

Common usage:  

1. reference a class's *hidden data field*.
2. enable a constructor to invoke another constructor of the same class.
   > e.g.  
   >
   > ```java
   > public ClassName (int var){
   >    this.ClassName();
   >    this.var = var;
   >    ......
   > }
   > ```

### Modifier

**private / public / protected / static / final / abstract** ......  

> Note: Data and methods are defaulted as `private`.

**`protector`**:

- Can be applied on data and methods in a class
- A prtocted data or method in a public class can be accessed by *any class in the same package*
- or its *subclasses* which are not in the same package.

**`final`**:

Modifiers are used on classes and class members (data and methods), except `final` can also be used on **local variables** in a methods which will be consider as a constant inside a method.

- A `final` class **cannot be extended**
- A `final` method **cannot be overriden** by its subclasses
- A `final` variable is a constant

#### Static

- **Static variables:** shared by all the instances of the class.  
- **Static methods:** not tied to a specific object.
- **Static constants:** final variables shared by all the instances of the class. (`static final`)

### Immutable

- **Immutable Object**:  
  the contents of an object cannot be changed once the object is created.
- **Immutable Class**:  
  For a class to be immutable, it must mark all data fields private and provide no mutator methods and no accessor methods that would return a reference to a mutable data field object.

### Wrapper Classes

Boolean / Integer / Character / Double / Float / Long / Short / Byte

- **`MAX_VALUE`**
- **`MIN_VALUE`**
- **`ClassName.valueOf(String str);`**  
  e.g. `Double.valueOf(str)`
- **`WrapperClassName.parseClass(String str)`**  
  e.g. `Integer.parseInt(str)`

1. The wrapper classes do not have no-arg constructors.  
2. The instances of all wrapper classes are immutable

&nbsp;

>### The Date Clss
>
>`java.util.Date()`
>`java.util.Date().toString(): String`
>`java.util.Date().getTime(): long`

&nbsp;

>### The Random Class
>
>`Math.random()`
>`java.util.Random()`

&nbsp;

## Methods

### Passing Parameters

- Pass by reference:  
  Any changes to the array that occur inside the method body **will affect** the original array that was passed as the argument becasue the memory will be changed.
- Pass by value of primitive data types:  
  The actual value is passed. Changing the value of the local parameter inside the method does **not affect** the value of the variable outside the method.

&nbsp;

## Inheritance

If no inheirtance is specified when a class is defined, the superclass of the class is `Object`.

**Superclass:**  

The keyword **`super`** refers to the superclas of the current class in which super appears and can be used in two ways:

1. To call a superclass construcor
   - a superclass's constructor will not be inheirated in subclasses,  
   - but can be invoked  
  `super()`  
  `super(<parameters>)`
   - superclass's constructor is always invoked
     - if a constructor didn't invoke (1) an overloaded constructor or (2) its superclass's constructor, (3) the compiler will puts `super()` as the first statement in constructor automatally.
    > **constructor chaining**:  
    > constructing an instance of a class incokes all the superclasses's constructors along the inheritance chain.
2. To call a superclass method

**Subclass:**

`@Overrided`  
A subclass modiffy the implementation of a method defined in the superclass is called **method overriding**. The method overided is marked with `@Overrided`.  

- an instance method can be overridden only if it is accessible
- if a method defined in a subclass is **private** in its superclass, the two methods are completely unrelated
- a **static method** can be inherited , but **cannot** be overridden
- a subclass cannot weaken the accessibility of a method defined in the superclass
  - e.g. if a method is defined as `public` in the superclass, it must be defined `public` in the subclass.

> **toString()**  
> A default implementation of `toString()` returns a stirng with a format like `[ClassName]@[number]`
>
> - [ClassName] is the class name of which the the object is an instance
> - [number] is the numer representing this object
>
>   **Special Case:**  
>   Each wrapper class ovrerrides the `toString()` (also `equals()` and `hashCode()`) defined in the Object Class.

### Polymorphism

**type**: a class defines a type  
**subtype**: a type defined by a class's subclass  
**supertype**: a type defined by a class's superclass  

- A variable of a supertype can refer to a subtype object.  
- An object of a subtype can be used wherever its supertype value is required.  

### Dynamic Binding

Suppose `Object o` is an instance of `Class C` which is the most specify class in a chain of inheritance. If `o` invokes a method `m()`, the JVM searches the implemention for the method `m()` along this chain **from the most specify class to the most general class**. Once an implement is found, the search stops and the **first-found** implemention is invoked.

> #### Method Matching v.s. Binding
>
> | **Matching** | Dynamic Binding |
> | ------ | ------|
> | The **compiler** finds a matching method according to **parameters'** type, number and order **at compilation time**.| A method may be implemented in several classes. **The JVM** dynamically binds the implementation of the method **at runtime**. |

### Casting Object within an inheritance hierachy

```java
SuperClass o = new Subclass();  //Implicit casting
SubClass sub = o;   //compiler error
SubClass sub = (SubClass)o;   //Expicit casting
```

- Explicit casting must be used when casting an object from a superclass to a subclass, and may not always succeed.

#### The **`instanceof`** Operator

Used to test wehter an obect is an instance of aclass.

```java
if (object instanceof Class) {}
```

> **equals()**  
> This method campares the contents of two objects.
>
> ```java
> //default implementation: 
> public boolean equals(Object obj){
>   return this == obj;
> }
> ```
>
> but as mentioned before, each wrapper class ovrerrides the `equals()` method.  
> One way to overrides the `equals()` method in our own classes:
>
> ```java
> @Overrides
> public boolean equals(Object o){
>   if (o instanceof OurClass){
>      return featureToCampared == ((OurClass)o).featureToCompared;
>   } 
>   else
>     return false;
> }
> ```
> 
> **`==` v.s. `equals()`**  
> == | equals()
> ------ | ------
> used for camparing two **primitive data type values** of for detrming whether two objects have the **same reference** | intented to test whether two objects have the **same contents**
> stronger | weaker

&nbsp;

## Exception Handling
