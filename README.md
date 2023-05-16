## Classes ##

Classes are used to define blueprints for creating objects that encapsulate data (attributes/variables) and behavior (methods/bfunctions) related to a specific entity.

- Classes are defined using the keyword `class` followed by the class name.
- The `__init__` method is a special method used as a constructor to initialize the object's attributes.

## Methods ##

Methods are functions defined within a class that are used to perform operations on the object's data.

- The first parameter of a method is conventionally named `self` and refers to the instance of the object calling the method.
- Methods can access and modify the object's attributes using `self.attribute_name`.

## Objects ##

Objects are referred to as specific instances of a class.

- Objects are created from a class using the class name followed by parentheses. 
- Any arguments required by the `__init__` method can be passed within the parentheses.
- Each object created from a class has its own set of attributes and can access the methods defined in the class.

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



