
## Advantages ##
We use class methods in Python for various reasons. 
Alternative Constructors: Class methods provide a way to define alternative constructors for a class. By creating class methods that accept different parameters or initialization mechanisms, you can provide additional ways to create instances of the class. This enhances the flexibility and usability of your code.

Accessing Class-level Data: Class methods have access to class-level variables and attributes. This allows you to perform operations that involve shared data among instances or manipulate class attributes. Class methods provide a convenient way to access and modify class-level data without needing an instance of the class.

Encapsulation and Organization: Class methods help to encapsulate complex or specialized operations that are closely tied to the class. By defining these operations as class methods, you keep the code organized and maintain a clear separation between class-level operations and instance-level operations. This enhances code readability and maintainability.

Utility Functions: Class methods can be used to define utility functions that are related to the class but don't require access to instance-specific data. These methods can provide useful operations that can be called directly on the class without creating an instance. This promotes code reusability and organization.

Polymorphism and Method Overriding: Class methods support polymorphism, allowing subclasses to override the behavior of a class method inherited from a superclass. This allows for specialized behavior in subclasses while maintaining a consistent interface defined by the superclass. Class methods facilitate the implementation of polymorphic behavior in object-oriented programming.

Methods are functions defined within a class that are used to perform operations on the object's data.

- The first parameter of a method is conventionally named as `self` and refers to the instance of the object calling the method.
- Methods can access and modify the object's attributes using `self.attribute_name`.## Classes ##

Classes are used to define blueprints for creating objects that encapsulate data (attributes/variables) and behavior (methods/bfunctions) related to a specific entity.

- Classes are defined using the keyword `class` followed by the class name.
- The `__init__` method is a special method used as a constructor to initialize the object's attributes.

## Objects ##

Objects are referred to as specific instances of a class.

- Objects are created from a class using the class name followed by parentheses. 
- Any arguments required by the `__init__` method can be passed within the parentheses.
- Each object created from a class has its own set of attributes and can access the methods defined in the class. 

## Methods ##

Methods are functions defined within a class that are used to perform operations on the object's data.

- The first parameter of a method is conventionally named `self` and refers to the instance of the object calling the method.
- Methods can access and modify the object's attributes using `self.attribute_name`.

## Example Code ##

```
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.mileage = 0

    def drive(self, distance):
        self.mileage += distance
        print(f"The {self.make} {self.model} has been driven {distance} miles.")

    def display_info(self):
        print(f"Make: {self.make}")
        print(f"Model: {self.model}")
        print(f"Year: {self.year}")
        print(f"Mileage: {self.mileage} miles")
```
```
# Create instances of the Car class
car1 = Car("Toyota", "Camry", 2020)
car2 = Car("Ford", "Mustang", 2018)Create instances of the Car class)


car1 = Car("Toyota", "Camry", 2020)
car2 = Car("Ford", "Mustang", 2018)
```
```
# Call object methods
car1.drive(100)        # Output: The Toyota Camry has been driven 100 miles.
car2.drive(50)         # Output: The Ford Mustang has been driven 50 miles.

car1.display_info()    # Output:
                       # Make: Toyota
                       # Model: Camry
                       # Year: 2020
                       # Mileage: 100 miles

car2.display_info()    # Output:
                       # Make: Ford
                       # Model: Mustang
                       # Year: 2018
                       # Mileage: 50 miles     
```



