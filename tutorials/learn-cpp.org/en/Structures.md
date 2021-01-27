Tutorial
--------

###  What is a structure

If you start programming code in C++ you'll sooner or later be facing a situation in which you'll need to store coherent data in a structured way.
This is what structures are beeing used for.

A structure is basically a user-defined datatype which consists of other datatypes like int, char and alike which are related with each other and may also contain functions.

### difference compared to a class
Classes are a concept of an object-orientated language like C++.
Unlike classes, structures also exist in pure C. It is logical, that C++ provides structures for backwards compatibility.

The only technical difference between a structure and a class is that every member of a struct is public by default whereas every class-member is private by default.
However you can make struct-members private just as you can make a class-members public by using the access-modifiers "public" and "private".

It has been agreed, that structs are usually used to store small passive data with none or few own functionality, whereas classes are used for larger and more complex data-structures which provide more functionality. - But keep in mind that this is just a convention and there is no technical limitation on this.

### Defining a structure
    //This is how you'll usually define a structure    
    using namespace std;
    struct MyOwnStructure { // keyword "struct" followed by a name, followed by braces containing the datatypes you like, followed by a semicolon
    //The following members are public by default
        int poperty_one;
        int property_two;
        char property_three;
        bool property_four;
        //...
    private:
    // The following members are private
        int private_property_one;
    };

### Using a structure 
    int main (void) {
        MyOwnStructure demo1; //Declare demo1 of type MyOwnStructure
        MyOwnStructure demo2; //Declare demo2 of type MyOwnStructure

        //set demo1's with values
        demo1.property_one = 1;
        demo1.property_two = 2;
        demo1.property_three = 'a';
        demo1.property_four = false;

        //set demo2's values
        demo2.property_one = 3;
        demo2.property_two = 4;
        demo2.property_three = 'b';
        demo2.property_four = true;

        cout << "Demo1: " << demo1.property_one << demo1.property_two << demo1.property_three << demo1.property_four << endl;
        cout << "Demo2: " << demo2.property_one << demo2.property_two << demo2.property_three << demo2.property_four << endl;
        /*
        Will output
        Demo1: 12a0
        Demo2: 34b1
        */
        return 0;
    }


Exercise
--------

- Create a structure named "person" with the following fields
  - name (should be string)
  - age (should be int)
  - do_programming (should be bool)
- declare two objects "p1" and "p2" of your structure's datatype
- set the values for "p1" as follows:
    - name: alice
    - age: 20
    - do_programming: true
- set the values for "p2" as follows:
    - name: bob
    - age: 18
    - do_programming: false
- "cout" their informations in the scheme "name (age)" => e.g. tim (23) by getting the values from your structure-objects


Tutorial Code
-------------

    #include <iostream>
    using namespace std;
    
    //Your structure here...

    int main (void){
        //Declaring person's
        //Your code here...

        //Setting person 1's values
        //Your code here...

        //Setting person 2's values
        //Your code here...

        //Printing out
        //Your code here...
        //cout << name << " (" << age << ")" << endl;
        

        return 0;
    }

Expected Output
---------------

    
    alice (20)
    bob (18)
    


Solution
--------

    #include <iostream>
    using namespace std;
    
    struct person { 
        string name;
        int age;
        bool do_programming;
    };

    int main (void){
        //Declaring person's
        person p1;
        person p2;

        //Setting person 1's values
        p1.name = "alice";
        p1.age = 20;
        p1.do_programming = true;

        //Setting person 2's values
        p2.name = "bob";
        p2.age = 18;
        p2.do_programming = false;

        //Printing out
        cout << p1.name << " (" << p1.age << ")" << endl;
        cout << p2.name << " (" << p2.age << ")" << endl;

        return 0;
    }


