## Liskov Substitution Principle (LSP)

The Liskov Substitution Principle (LSP) is a principle of object-oriented design that states that objects in a program should be replaceable with instances of their subtypes without affecting the correctness of the program. In other words, if a class is a subtype of another class, then objects of the subtype class should be able to be used wherever objects of the parent class are used without causing any problems. This allows for flexibility and maintainability in object-oriented design, as well as code reusability and extensibility. To implement the LSP, developers can use techniques such as [polymorphism](../99_GLOSSARY/POLYMORPHISM.md) and [inheritance](../99_GLOSSARY/INHERITANCE.md).

> ### Explain the Liskov Substitution Principle (LSP) like I'm five
> 
> The Liskov Substitution Principle is like a game of hide and seek. In hide and seek, there are different types of people who can play, like kids and adults. And even though kids and adults are different, they can still play the same game together. For example, if a kid is hiding, then an adult can still go and find them. And if an adult is hiding, then a kid can still go and find them. So even though kids and adults are different, they can still play hide and seek together without causing any problems. In object-oriented programming, the different types of people are like classes, and the game of hide and seek is like a program. The Liskov Substitution Principle says that objects of different classes should be able to be used together in a program without causing any problems.



Here are some Liskov Substitution Principle (LSP) code examples:

```ruby
# Define a base Shape class
class Shape
  # Define a method to calculate the area
  def area
    raise NotImplementedError, "Method not implemented"
  end
end

# Define a Circle class that inherits from Shape
class Circle < Shape
  # Initialize a circle with a radius
  def initialize(radius)
    @radius = radius
  end

  # Override the area method to calculate the area of a circle
  def area
    Math::PI * (@radius ** 2)
  end
end

# Define a Square class that inherits from Shape
class Square < Shape
  # Initialize a square with a side length
  def initialize(side)
    @side = side
  end

  # Override the area method to calculate the area of a square
  def area
    @side ** 2
  end
end

# Define a Shapes class that can calculate the total area of a collection of shapes
class Shapes
  # Initialize a shapes collection with an array of shapes
  def initialize(shapes)
    @shapes = shapes
  end

  # Calculate the total area of all shapes in the collection
  def total_area
    @shapes.map(&:area).sum
  end
end

# Example usage

# Create a circle with radius 2
circle = Circle.new(2)

# Create a square with side length 2
square = Square.new(2)

# Create a shapes collection with the circle and square
shapes = Shapes.new([circle, square])

# Calculate the total area of all shapes in the collection
puts shapes.total_area
# Output: 12.566370614359172

```

```ruby
RSpec.describe Shapes do
  let(:circle) { Circle.new(2) }
  let(:square) { Square.new(2) }
  let(:shapes) { Shapes.new([circle, square]) }

  it "calculates the total area of a collection of shapes" do
    expect(shapes.total_area).to eq(16.566370614359172)
  end
end
```

In this example, the Circle and Square classes both inherit from the Shape class, and they each implement the area method in a way that is specific to their respective shape.

| [Previous](02_OPEN_CLOSED_PRINCIPLE.md) | [Index](..%2FREADME.md) | [Next](04_INTERFACE_SEGREGATION_PRINCIPLE.md) |
|-----------------------------------------|-------------------------|-----------------------------------------------|
