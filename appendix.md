# APPENDIX

- [APPENDIX](#appendix)
  - [Random](#random)
  - [Arrays](#arrays)
  - [String](#string)
  - [List](#list)
  - [Set](#set)
  - [Map](#map)
  - [Queue](#queue)
  - [Stack](#stack)

## Random

java.util.Random

```java
import java.util.Random

Random random = new Random();
// generate new random integer from 0 to N-1
int rand_int = random.nextInt(N);
// generate new random doule
double rand_double = random.nextDouble();
```

Math.random

```java
import java.util.*;

// generate random doule
double random = Math.random();  // 0 <= random <1 
```

## Arrays

```java
import java.util.Arrays;

// sort
<T>[] a = Arrays.sort(T[] a, Comparator<? super T> c);
<T>[] a = Arrays.sort(T[] a, int fromIndex, int toIndex, Comparator<? super T> c);
// aslist
List<T> list = Arrays.asList(T[] a);
// toString
Object[] objArr = new Object[] { 1, 2, 3, 4 };
System.out.println(Arrays.toString(objArr));  // [1, 2, 3, 4]
Object[] nullArr = null;
System.out.println(Arrays.toString(nullArr)); //null
```

## String

```java
import java.util.*;

String str;
int len = str.length();
char ch = str.charAt(index);
int index = str.indexOf((int)ch); //Returns the index within this string of the first occurrence of the specified character.
boolean isEmpty = str.isEmpty();
String[] strs = str.split(String regex);

// Returns the string representation of the Object argument.
String toStr = String.valueOf(Object obj);
double d;
String doubleToString = d.toString();

// Convert a String to an Array and an ArrayList
String[] strSplit = str.split("");
ArrayList<String> strList = new ArrayList<String>(Arrays.asList(strSplit));

// Convert a String to other object
int i = Integer.parseInt(str); 
Integer i=Integer.valueOf(str); 
```

## List

## Set

## Map

## Queue

## Stack
