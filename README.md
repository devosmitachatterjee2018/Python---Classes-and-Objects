## Classes ##

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

## Advantages ##
We use class methods in Python for various reasons. 

- **Alternative Constructors**: We can create multiple instances of the class by defining class methods that accept different parameters or initialization mechanisms. This enhances the flexibility and usability of your code.

```
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year

    @classmethod
    def from_vin(cls, vin):
        """Alternative constructor to create a car from a VIN (Vehicle Identification Number)."""
        # Logic to extract make, model, and year from the VIN
        make = vin[:3]
        model = vin[3:6]
        year = vin[9:10]
        return cls(make, model, year)

    @classmethod
    def from_string(cls, car_string):
        """Alternative constructor to create a car from a string representation."""
        make, model, year = car_string.split(',')
        return cls(make.strip(), model.strip(), int(year.strip()))

# Creating instances using the primary constructor
car1 = Car("Toyota", "Camry", 2022)
print(car1.make, car1.model, car1.year)  # Output: Toyota Camry 2022

# Creating instances using alternative constructors
car2 = Car.from_vin("JTDKARFU200001234")
print(car2.make, car2.model, car2.year)  # Output: JTD KAR 0

car3 = Car.from_string("Ford, Mustang, 2018")
print(car3.make, car3.model, car3.year)  # Output: Ford Mustang 2018
```

- **Accessing Class-level Data**: Class methods allows to perform operations that involve shared data among instances or manipulate class attributes. 

```
class Car:
    num_cars = 0  # Class-level variable

    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        Car.num_cars += 1

    def get_car_count(self):
        return Car.num_cars

# Creating instances of the Car class
car1 = Car("Toyota", "Camry", 2022)
car2 = Car("Honda", "Accord", 2021)

# Accessing class-level variable using the class name
print(Car.num_cars)  # Output: 2

# Accessing class-level variable using an instance
print(car1.num_cars)  # Output: 2
print(car2.num_cars)  # Output: 2

# Accessing class-level variable through a method
print(car1.get_car_count())  # Output: 2
print(car2.get_car_count())  # Output: 2
```

- **Encapsulation and Organization**: Class methods help to encapsulate complex or specialized operations that are closely tied to the class. By defining these operations as class methods, you keep the code organized and maintain a clear separation between class-level operations and instance-level operations. This enhances code readability and maintainability.

```
class Car:
    def __init__(self, make, model, year):
        self._make = make  # Encapsulated attribute
        self._model = model  # Encapsulated attribute
        self._year = year  # Encapsulated attribute
        self._fuel_level = 0  # Encapsulated attribute

    def fill_tank(self, liters):
        """Fill the car's fuel tank."""
        self._fuel_level += liters

    def drive(self, distance):
        """Drive the car for a given distance."""
        fuel_needed = distance / 10  # Assuming 10 km per liter fuel consumption
        if fuel_needed <= self._fuel_level:
            self._fuel_level -= fuel_needed
            print("Car is driving...")
        else:
            print("Insufficient fuel!")

    def get_make(self):
        """Getter method for the make attribute."""
        return self._make

    def set_make(self, make):
        """Setter method for the make attribute."""
        self._make = make

# Creating a car instance
car = Car("Toyota", "Camry", 2022)

# Accessing encapsulated attributes using getter and setter methods
print(car.get_make())  # Output: Toyota
car.set_make("Honda")
print(car.get_make())  # Output: Honda

# Performing encapsulated operations
car.fill_tank(20)  # Fill the fuel tank with 20 liters
car.drive(150)  # Drive the car for 150 km
```

- **Utility Functions**: Class methods can be used to define utility functions that are related to the class but don't require access to instance-specific data. These methods can provide useful operations that can be called directly on the class without creating an instance. This promotes code reusability and organization.

```
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year

    def start_engine(self):
        """Start the car's engine."""
        print("Engine started.")

    def stop_engine(self):
        """Stop the car's engine."""
        print("Engine stopped.")

def calculate_distance(time, speed):
    """Calculate the distance traveled based on time and speed."""
    distance = time * speed
    return distance

def is_luxury_car(car):
    """Check if a car is a luxury car based on the make and model."""
    luxury_cars = ["Mercedes", "BMW", "Audi", "Lexus"]
    if car.make in luxury_cars:
        return True
    else:
        return False

# Creating a car instance
car = Car("Toyota", "Camry", 2022)

# Calling utility functions
distance = calculate_distance(2.5, 60)  # Calculate distance traveled in 2.5 hours at 60 km/h
print("Distance traveled:", distance)  # Output: Distance traveled: 150.0

print("Is it a luxury car?", is_luxury_car(car))  # Output: Is it a luxury car? False

# Calling methods of the Car class
car.start_engine()  # Output: Engine started.
car.stop_engine()  # Output: Engine stopped.
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year

    def start_engine(self):
        """Start the car's engine."""
        print("Engine started.")

    def stop_engine(self):
        """Stop the car's engine."""
        print("Engine stopped.")

def calculate_distance(time, speed):
    """Calculate the distance traveled based on time and speed."""
    distance = time * speed
    return distance

def is_luxury_car(car):
    """Check if a car is a luxury car based on the make and model."""
    luxury_cars = ["Mercedes", "BMW", "Audi", "Lexus"]
    if car.make in luxury_cars:
        return True
    else:
        return False

# Creating a car instance
car = Car("Toyota", "Camry", 2022)

# Calling utility functions
distance = calculate_distance(2.5, 60)  # Calculate distance traveled in 2.5 hours at 60 km/h
print("Distance traveled:", distance)  # Output: Distance traveled: 150.0

print("Is it a luxury car?", is_luxury_car(car))  # Output: Is it a luxury car? False

# Calling methods of the Car class
car.start_engine()  # Output: Engine started.
car.stop_engine()  # Output: Engine stopped.
```

- **Polymorphism and Method Overriding**: Class methods support polymorphism, allowing subclasses to override the behavior of a class method inherited from a superclass. This facilitate the implementation of polymorphic behavior in object-oriented programming.

```
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year

    def start_engine(self):
        """Start the car's engine."""
        print("Engine started.")

    def stop_engine(self):
        """Stop the car's engine."""
        print("Engine stopped.")

    def drive(self):
        """Drive the car."""
        print("Car is driving.")


class ElectricCar(Car):
    def start_engine(self):
        """Start the electric car's engine."""
        print("Engine started silently.")

    def stop_engine(self):
        """Stop the electric car's engine."""
        print("Engine stopped silently.")

    def drive(self):
        """Drive the electric car."""
        print("Electric car is driving silently.")


class HybridCar(Car):
    def start_engine(self):
        """Start the hybrid car's engine."""
        print("Engine started quietly.")

    def stop_engine(self):
        """Stop the hybrid car's engine."""
        print("Engine stopped quietly.")

    def drive(self):
        """Drive the hybrid car."""
        print("Hybrid car is driving quietly.")


# Creating car objects
car1 = Car("Toyota", "Camry", 2022)
car2 = ElectricCar("Tesla", "Model S", 2022)
car3 = HybridCar("Toyota", "Prius", 2022)

# Polymorphism and method overriding
car1.start_engine()  # Output: Engine started.
car2.start_engine()  # Output: Engine started silently.
car3.start_engine()  # Output: Engine started quietly.

car1.drive()  # Output: Car is driving.
car2.drive()  # Output: Electric car is driving silently.
car3.drive()  # Output: Hybrid car is driving quietly.

car1.stop_engine()  # Output: Engine stopped.
car2.stop_engine()  # Output: Engine stopped silently.
car3.stop_engine()  # Output: Engine stopped quietly.
```
