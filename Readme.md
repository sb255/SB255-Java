# Java-Operations

## *int to String conversion in Java*

#### *String.valueOf(int i) and Integer.toString(int i) can be used to convert int data type value into a String object*

```java
int x = 100;

String s = String.valueOf(100);

//OR

String s = Integer.toString(100);

```

## *String to int conversion in Java*

#### *Integer.valueOf(String s) returns an instance of Integer class, while Integer.parseInt(String s) returns a variable of int data type!*

```java

String s = "100";

Integer k = Integer.valueOf(s);

//OR

int kk = Integer.parseInt(s);

```

## *int to int[] conversion in Java*

#### *Character.getNumericValue(char c) returns the numerical value of the character!*

```java
int intValue = 123456789;
String stringValue = Integer.toString(intValue);
int[] input = new int[stringValue.length()];
int inputLength = input.length;

for(int i=0; i<inputLength; i++){
    input[i] = Character.getNumericValue(stringValue.charAt(i));
}
```

## *Inheritance and object references:*

*See the CASES mentioned in the main class!*

```java

import java.util.*;


class PreTest {

    public void callMe(){

        System.out.println("Method of SUPER CLASS is called");

    }

}

public class Test extends PreTest {


    public void callMe(){

        System.out.println("Method of SUB CLASS is called");

    }

    public static void main(String[] args){

    /*CASE 1*/   
        Test obj = new Test();
        PreTest obj2 = (PreTest) obj;

        obj2.callMe();
    /*----OUTPUT: Method of SUB CLASS is called----*/    


    /*CASE 2*/
        PreTest obj3 = new PreTest();
        //Test obj4 = (PreTest) obj3;  /*--Not Valid--*/


    /*CASE 3*/
        //Test obj5 = new PreTest();   /*--Not Valid--*/    



    /*CASE 4*/
        PreTest obj6 = new Test();
        obj6.callMe();
    /*----OUTPUT: Method of SUB CLASS is called----*/


   /*CASE 5*/
        PreTest obj7 = new PreTest();
        //Test obj8 = (PreTest) obj7; /*--Even subclass object can not refer to a super class object--*/  


    }

}
```

## *Comparators in Java:*

```java
import java.util.*;

class TestTaker{
	public int id;
        String name;
	public int marks;
	public TestTaker(int id, String name, int marks) {
            this.id = id;
            this.name = name;
            this.marks = marks;
	}
	public int getId() {
            return id;
	}
	public String getName() {
            return name;
	}
	public int getMarks() {
            return marks;
	}
}


public class Test
{
	public static void main(String[] args){


            List<TestTaker> list = new ArrayList<TestTaker>();

            TestTaker obj1 = new TestTaker(1, "David", 91);
            TestTaker obj2 = new TestTaker(2, "Mike", 93);
            TestTaker obj3 = new TestTaker(3, "John", 95);
            TestTaker obj4 = new TestTaker(4, "Sky", 95);
            TestTaker obj5 = new TestTaker(5, "Leo", 99);

            list.add(obj1);
            list.add(obj2);
            list.add(obj3);
            list.add(obj4);
            list.add(obj5);

            Collections.sort(list,new MarksComparator());  

            for(TestTaker t : list){
                System.out.println(t.getId()+" "+t.getName()+" "+t.getMarks());
            }

	}
}

class MarksComparator implements Comparator{  
    public int compare(Object obj1,Object obj2){  
        TestTaker t1=(TestTaker)obj1;  
        TestTaker t2=(TestTaker)obj2;  

        if(t1.marks==t2.marks)  
            return t1.name.compareTo(t2.name);   
        else if(t1.marks>t2.marks)  
            return -1;  
        else  
            return 1;  
    }   
}


class NameComparator implements Comparator{  
    public int compare(Object obj1,Object obj2){  
        TestTaker t1=(TestTaker)obj1;  
        TestTaker t2=(TestTaker)obj2;  

    return t1.name.compareTo(t2.name);  
    }  
}
```
## *Ways to write Comparators in Java:*

*Approach 1 is also known as Anonymous comparator*

```java
/*---- Approach 1 ----*/    

/*-- Using Anonymous comparators --*/        

Collections.sort(list, new Comparator() {

    public int compare(Object obj1,Object obj2){  
        TestTaker t1=(TestTaker)obj1;  
        TestTaker t2=(TestTaker)obj2;  

        if(t1.marks==t2.marks)  
            return t1.name.compareTo(t2.name);   
        else if(t1.marks>t2.marks)  
            return -1;  
        else  
            return 1;  
        }});



/*---- Approach 2 ----*/     

Collections.sort(list,new MarksComparator());

/*-- Then write a separate Class --*/

class MarksComparator implements Comparator{  
    public int compare(Object obj1,Object obj2){  
        TestTaker t1=(TestTaker)obj1;  
        TestTaker t2=(TestTaker)obj2;  

        if(t1.marks==t2.marks)  
            return t1.name.compareTo(t2.name);   
        else if(t1.marks>t2.marks)  
            return -1;  
        else  
            return 1;  
    }   
}
```

## *Generics in Java:*

```java
public class Test{

    public static <E extends Number> int addObjects(E a, E b){

        return (a.intValue() + b.intValue());
        /* intValue is a methos of Number class */

    }

    public static void main(String[] args){

        System.out.println(addObjects(10, 20));

    }

}
```
```java
public class Test{

    public static <E extends Comparable> E addObjects(E a, E b){

        if(a.compareTo(b)>0)
            return a;


        if(a.compareTo(b)<0)
            return b;

        else
            return a;

    }

    public static void main(String[] args){

        System.out.println("The larger value is: "+addObjects("Hello", "Jack"));

    }

}
```

## *Regular Expressions in Java:*

> `\d` represents any digit in regular expression but `\` is also a character in java so to convert `\` into a literal we add another `\` so that `\d` can be considered as literal in regular expression!

Check all these regular expressions on a Java program

| SN | Java Regex String | Description
| :----: | :---: | :---:
| 1 | `[A-Za-z]` | It matches a single character with all the uppercase and lowercase characters
| 2 | `[A-Za-z]?` | It matches zero or one character with all the uppercase and lowercase characters
| 3 | `[A-Za-z]*` | It matches zero or more than zero characters with all the uppercase and lowercase characters
| 4 | `[^A-Za-z]+` | It matches a single or more characters with everything except A-Za-z
| 5 | `[^A-Za-z]{2}` | It matches exactly two characters with everything except A-Za-z
| 6 | `[A-Za-z0-9]` | It matches all the uppercase and lowercase alphanumeric characters
| 7 | `[A-Za-z0-9]{1,5}` | It matches minimum 1 and maximum 5 uppercase and lowercase alphanumeric characters
| 8 | `[A-Za-z !,?._'@]+` | It matches 1 or more than 1 lowercase and uppercase alphabets along with special characters
| 9 | `[-+.^:,]` | It matches a single character with all the special characters
| 10 | `.` | It matches with a character of any kind
| 11 | `\\d{1}` | It matches with a single digit
| 12 | `\\d{1,3}` | It matches with a numerical value having 1 to 3 digits
| 13 | `[\\d]{1}` | It matches with a single digit
| 14 | `[0-5]` | It matches with a single digit ranging from 0 to 5
| 15 | `\\s` | It matches with single white space character
| 16 | `[\\s]` | It matches with single white space character
