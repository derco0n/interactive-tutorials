Tutorial
--------

###  What is a class
Assumingly you already know about structures, then you'll know that a class isn't that different.
Classes are -like structures- basically user-defined datatype's which consists of other datatypes like int, char and alike which are related with each other.
Classes may also contains functions (or, to use the correct terminology: "methods") to process data from outside or within the class.
Classes are often used to describe and implement a functionality for something you want to use in your program.

### difference compared to a structure
At this point you might think, whats the point about classes when we've got structures:
From a technical point of view, the only difference between a structure and a class is that every member of a structure is public by default whereas every class-member is private by default.
However you can make struct-members private just as you can make a class-members public by using the access-modifiers "public" and "private".

It has been agreed, that structs are usually used to store small passive data with none or few own functionality, whereas classes are used for larger and more complex data-structures which provide more functionality. - But keep in mind that this is just a convention and there is no technical limitation on this.

Unlike structures, classes are non-existend in pure C.

### Use cases / Inheritance
Classes can be used reflect real-objects with their properties and to craft dervied objects from them.
You can, for example, define a class "vehicle" which has a property "color" and "max-speed".
After that you might define the next class "street-vehicle" which derives all properties from "vehicle" and adds its own properties like e.g. "num_wheels".

### Instantiation 
C++ is an object-orientated programming language. In pratice you'll often use non-static classes which will need to be instantiated.
Instantiation is the process that will craft a new object from a class definition into memory. This means you are not limited to one instance of your vehicle-class. You can create as much instances of your class as you like as long your computer has enough memory.

Referring to the vehicle-example from above-, you could for example create three (or more) objects from your class:
- "v1" with a max-speed of "10" and "white" color
- "v2" with a max-speed of "100" and "green" color
- "v3" with a max-speed of "250" and "red" color

### Constructor / Destructor
Classes usually use contructors and destructors:
The constructor is method which is automatically called whenever a new instance is created.
The destructor is method which is automatically called whenever an instance get destroyed

### Defining a class
    //This is how you'll may define a class
    #include <iostream>
    #include <stdlib.h>

    class hello_class {
        private:
        //Private objects and methods

        protected:
        //Protected objects that can be inherited by child objects and are not seen by other, non-child-classes
            std::string _name="";  // Will store a string "name" internally

        public:
        //Public objects and methods
            hello_class() { //default-constructor (takes no argument) has no type but must be named like the class itself
        }  

        hello_class(std::string name) {  // constructor (Takes a string-argument "name") has no type but must be named like the class itself
            this->_name=name; // When instantiated, sets the class-object-variable "name" (note the keyword "this->") to whatever is passed as argument
        }

        void printHello() //Print-hello-method
        {            
            if (this->_name.compare("") != 0){ //Will check if a name was passed to this class
                //name is intialized with something different than ""
                std::cout << "Hello " << this->_name << std::endl; //output "Hello <name>"
            }                 
        }
    };

### Using a class 
    int main (void) {
        //Create some instances of "hello_class"
        hello_class *hello1 = new hello_class("Alice"); //Will return a pointer to the new instance of "hello_class"
        hello_class *hello2 = new hello_class("Bob");  //Will return a pointer to the new instance of "hello_class"
        hello_class *hello3 = new hello_class("Charles");  //Will return a pointer to the new instance of "hello_class"

        hello1->printHello(); //Hello Alice
        hello2->printHello(); //Hello Bob
        hello3->printHello(); //Hello Charles

        return 0;
    }

### Creating a child-class
    class goodbye_class : public hello_class { //This class derives from hello_class
    // Note that this class will have all properties from its base-class
    private:

    public:
        goodbye_class(std::string name):hello_class(name) { 
            //Derived constructor which calls the base-class-constructor.
            //You might do some other things here in the child-class if needed.
        }

    void printGoodBye() //Print-goodbye-method
        {
            if (this->_name.compare("") != 0){
                //name is intialized with something different than ""
                std::cout << "Good Bye " << this->_name << std::endl; //output "Good Bye <name>"
            }
        }
    };

### Using a child-class 
    int main (void) {
        //Create some instances of "goodbye_class"
        goodbye_class *hg1 = new goodbye_class("Alice"); //Will return a pointer to the new instance of "goodbye_class"
        goodbye_class *hg2 = new goodbye_class("Bob");  //Will return a pointer to the new instance of "goodbye_class"
        goodbye_class *hg3 = new goodbye_class("Charles");  //Will return a pointer to the new instance of "goodbye_class"

        //Hello: Note, that "goodbye_class" has this functionality from "hello_class"
        hg1->printHello(); //Hello Alice
        hg2->printHello(); //Hello Bob
        hg3->printHello(); //Hello Charles

        //Goodbye: This is additional functionality provided by "goodbye_class"
        hg1->printGoodBye(); //Good Bye Alice
        hg2->printGoodBye(); //Good Bye Bob
        hg3->printGoodBye(); //Good Bye Charles

        return 0;
    }

Exercise
--------
- Create a class "square", that:
  - takes a float argument "length" in the constructor which stores it within the object
  - implements a method "area" which takes no argument and returns the squares-area as a float value (length * length)
- Use that class in your main program to display the area of a square with an edge length of 33.5


Tutorial Code
-------------
    #include <iostream>
    #include <stdlib.h>

    using namespace std;

    class square {  
        //Your class definition here
    };


    int main (void) {        
        // Your class-instantiation here...
        cout << somesquare->area() << endl;

        return 0;
    }


Expected Output
---------------

    
    1122.25
    


Solution
--------

    #include <iostream>
    #include <stdlib.h>

    using namespace std;

    class square {
        private:
        //Private objects and methods
        float length_;

        protected:
        //Protected objects that can be inherited by child objects and are not seen by other, non-child-classes

        public:
        //Public objects and methods
            square(float length) { //constructor
                this->length_ = length; //store the length internally
        }  

        float area() // will return the square's area
        {
                return this->length_ * this->length_;
        }
    };


    int main (void) {
        square *somesquare = new square(33.5);
        cout << somesquare->area() << endl;

        return 0;
    }


