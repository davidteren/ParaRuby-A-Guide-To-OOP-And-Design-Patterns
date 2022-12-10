## LSP 

### EXAMPLE 1

> #### BAD
Here is an example of bad Ruby code that violates the Liskov Substitution Principle (LSP), which is one of the principles of the SOLID design principles:

```ruby
class Animal
  def initialize(name)
    @name = name
  end

  def speak
    raise NotImplementedError
  end
end

class Cat < Animal
  def speak
    puts "#{@name} says meow"
  end
end

class Dog < Animal
  def speak
    puts "#{@name} says bark"
  end
end

class Parrot < Animal
  def initialize(name, can_speak)
    super(name)
    @can_speak = can_speak
  end

  def speak
    if @can_speak
      puts "#{@name} says squawk"
    else
      raise "This parrot cannot speak"
    end
  end
end

```
This code violates the LSP because the Parrot class is not a substitution for the Animal class. In particular, the Parrot class has a can_speak attribute that determines whether it can speak or not, and the speak method raises an exception if the parrot cannot speak. This means that if we have a list of Animal objects that includes Parrot objects, we have to check whether each Parrot object can speak before calling the speak method on it, or else it will raise an exception.

To fix this, we can make the Parrot class a true substitution for the Animal class by removing the can_speak attribute and the special behavior of the speak method. For example:

> #### Good

```ruby
class Animal
  def initialize(name)
    @name = name
  end

  def speak
    raise NotImplementedError
  end
end

class Cat < Animal
  def speak
    puts "#{@name} says meow"
  end
end

class Dog < Animal
  def speak
    puts "#{@name} says bark"
  end
end

class Parrot < Animal
  def speak
    puts "#{@name} says squawk"
  end
end

```
This code follows the LSP because the Parrot class is a true substitution for the Animal class. In particular, the Parrot class does not have a can_speak attribute and the speak method does not have any special behavior. This means that we can treat a Parrot object just like any other Animal object, and we can call the speak method on it without having to check whether it can speak or not.

---