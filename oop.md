# Object Orientated Programming

Object-oriented programming (OOP) is a programming paradigm that is based on the concept of "objects", which are data structures that contain both data and behavior. In Ruby, OOP is implemented through the use of classes, which define the structure and behavior of objects. These classes can be organized into hierarchies through inheritance, where a subclass can inherit characteristics and behavior from a parent class. OOP allows for code to be more modular, reusable, and maintainable, as objects can be easily created and manipulated, and common behavior can be defined and inherited across classes.

> Explain Object Orientated Programming (OOP) like I'm five
>
> OOP is like when you have a bunch of toys that you like to play with. For example, you might have a toy car, a toy airplane, and a toy robot. Each of these toys is a little bit different, but they all have some things in common. For example, they might all have wheels or they might all be able to move around. This is OOP because each toy is like its own "object" and they all have the same things (like wheels or movement) because they are part of the same "class" (toys). So when you want to make your toys do something, you can just tell them what to do and they'll do it because they all have the same abilities. It's like they all know the same magic words.

### Here is an example of OOP in Ruby:

```ruby
# Define a class called 'Dog'
class Dog
  # Define an instance variable called 'name'
  # This variable will store the dog's name
  attr_accessor :name

  # Define a constructor method that sets the dog's name
  def initialize(name)
    @name = name
  end

  # Define a method called 'bark' that prints the dog's name and a bark sound
  def bark
    puts "#{@name}: Woof!"
  end
end

# Create a new instance of the Dog class
dog = Dog.new("Buddy")

# Call the 'bark' method on the dog instance
dog.bark
```

This code creates a `Dog` class with a `name` instance variable and a `bark method. A new` Dog`object is then created and the`bark\` method is called on it, which prints the dog's name and a bark sound.

### Here's another example of OOP in Ruby:

```ruby
# Define a class called "Person"
class Person
  # Define attributes for the Person class
  attr_accessor :name, :age

  # Define a constructor method for initializing new Person objects
  def initialize(name, age)
    @name = name
    @age = age
  end

  # Define a method for greeting another Person object
  def greet(other_person)
    puts "Hi #{other_person.name}, I'm #{@name} and I'm #{@age} years old."
  end
end

# Create two new Person objects
p1 = Person.new("John", 25)
p2 = Person.new("Jane", 28)

# Have p1 greet p2
p1.greet(p2)

```

In this code, we define a class called `Person` that has two attributes, `name` and `age`, and a method called `greet` that allows a `Person` object to greet another `Person` object. We then create two instances of the `Person` class and use the `greet` method to have one `Person` object greet the other. This example demonstrates how OOP allows us to model real-world objects and their interactions in a more intuitive and flexible way.

|   | [Index](./) |   |
| - | ----------- | - |
