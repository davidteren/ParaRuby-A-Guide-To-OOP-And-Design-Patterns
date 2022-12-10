## ISP 

### EXAMPLE 1

> #### BAD
Here is an example of bad Ruby code that violates the Interface Segregation Principle (ISP), which is one of the principles of the SOLID design principles:
```ruby
class Animal
  # Violates the ISP because it forces all subclasses to implement
  # methods that they may not need or use
  def eat
    raise NotImplementedError
  end

  def sleep
    raise NotImplementedError
  end

  def speak
    raise NotImplementedError
  end
end

class Cat < Animal
  def eat
    puts "#{@name} is eating"
  end

  def sleep
    puts "#{@name} is sleeping"
  end

  def speak
    puts "#{@name} says meow"
  end
end

class Fish < Animal
  # Violates the LSP because it does not implement the speak method
  def eat
    puts "#{@name} is eating"
  end

  def sleep
    puts "#{@name} is sleeping"
  end
end
```
This code violates the ISP because the Animal class defines a set of methods that all subclasses must implement, even if some of the subclasses do not need or use those methods. For example, the Fish class does not have the ability to speak, but it still has to implement the speak method in order to satisfy the Animal class's interface. This makes the code less flexible and harder to maintain, because if we want to add a new method to the Animal class's interface, we have to update all of the subclasses to implement the new method, even if some of the subclasses do not need or use the new method.

To fix this, we can create separate interfaces for different groups of methods, and make the subclasses implement only the interfaces that they need or use. For example:

> #### Good

```ruby
class Animal
  # Defines an interface for animals that can eat
  def eat
    raise NotImplementedError
  end
end

class Sleepable
  # Defines an interface for animals that can sleep
  def sleep
    raise NotImplementedError
  end
end

class Speakable
  # Defines an interface for animals that can speak
  def speak
    raise NotImplementedError
  end
end

class Cat < Animal
  include Sleepable
  include Speakable

  def eat
    puts "#{@name} is eating"
  end

  def sleep
    puts "#{@name} is sleeping"
  end

  def speak
    puts "#{@name} says meow"
  end
end

class Fish < Animal
  # Implements only the Animal interface, because it cannot sleep or speak
  def eat
    puts "#{@name} is eating"
  end
end

```

This code follows the ISP because the Animal, Sleepable, and Speakable classes define separate interfaces for different groups of methods, and the subclasses implement only the interfaces that they need or use. For example, the Fish class only implements the Animal interface, because it cannot sleep or speak, and it does not have to implement the Sleepable or Speakable interfaces. This makes the code more flexible and easier to maintain, because we can add new methods to the interfaces without affecting the subclasses that do not need or use those methods.

---


