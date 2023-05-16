## Classes ##

Classes are used to define blueprints for creating objects that encapsulate attributes (variables) and methods (functions) related to a specific entity.

## Objects ##

Objects are referred to as specific instances of a class.

## Methods ##

Methods are functions defined within a class that are used to perform operations on the object's data.

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
`<!--` Create instances of the Car class `-->`
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



