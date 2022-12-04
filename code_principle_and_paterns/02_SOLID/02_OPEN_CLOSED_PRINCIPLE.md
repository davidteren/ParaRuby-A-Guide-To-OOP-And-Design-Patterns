## Open/Closed Principle (OCP)


The Open/Closed Principle (OCP) is a principle of object-oriented design that states that software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification. This means that new functionality can be added to existing classes without changing their existing code. This allows for code reusability and maintainability, as well as flexibility to accommodate future changes in requirements. To implement the OCP, developers can use techniques such as [abstraction](../99_GLOSSARY/ABSTRACTION.md), [polymorphism](../99_GLOSSARY/POLYMORPHISM.md), and [inheritance](../99_GLOSSARY/INHERITANCE.md).

> ### Explain Open/Closed Principle (OCP) like I'm five
>
> The Open/Closed Principle is like a box. You can put things inside the box and take things out, but you can't change the box itself. This is good because you can use the same box over and over again and it will still work the same way. And if you want to put a different kind of thing in the box, you can just make a new box that is the same size but has a different shape or color. This way, you can keep using the old box and the new box without having to change anything.



One code example of the Open/Closed Principle (OCP) is a payment gateway class that uses the strategy pattern to process different types of payment methods:

```ruby
class PaymentGateway
  def initialize(payment_method)
    @payment_method = payment_method
  end

  def process(amount)
    @payment_method.process(amount)
  end
end

class CreditCardPayment
  def process(amount)
    # Code to process credit card payment goes here
    puts "Processing credit card payment for #{amount}..."
  end
end

class DebitCardPayment
  def process(amount)
    # Code to process debit card payment goes here
    puts "Processing debit card payment for #{amount}..."
  end
end

class PayPalPayment
  def process(amount)
    # Code to process PayPal payment goes here
    puts "Processing PayPal payment for #{amount}..."
  end
end

# Example usage

payment_gateway = PaymentGateway.new(CreditCardPayment.new)
payment_gateway.process(100)
# Output: Processing credit card payment for 100...

payment_gateway = PaymentGateway.new(DebitCardPayment.new)
payment_gateway.process(200)
# Output: Processing debit card payment for 200...

payment_gateway = PaymentGateway.new(PayPalPayment.new)
payment_gateway.process(300)
# Output: Processing PayPal payment for 300...
```

In this code example, the PaymentGateway class is open for extension, as it allows developers to easily add support for new payment methods by implementing the appropriate interfaces. However, the PaymentGateway class is closed for modification, as the existing methods and interfaces should not be changed in order to maintain backward compatibility and avoid breaking existing code.


Another code example of the OCP is a logging class that uses the decorator pattern to log messages to different types of destinations:

```ruby
class Logger
  def initialize(logger)
    @logger = logger
  end

  def log(message)
    @logger.log(message)
  end
end

class FileLogger
  def log(message)
    # Code to log message to file goes here
    File.open("log.txt", "a") do |file|
      file.puts(message)
    end
  end
end

class DatabaseLogger
  def log(message)
    # Code to log message to database goes here
    Log.create(message: message)
  end
end

class MessageQueueLogger
  def log(message)
    # Code to log message to message queue goes here
    MessageQueue.enqueue(message)
  end
end

# Example usage

logger = Logger.new(FileLogger.new)
logger.log("This is a message.")
# Output: Log message added to log.txt

logger = Logger.new(DatabaseLogger.new)
logger.log("This is a message.")
# Output: Log message added to database

logger = Logger.new(MessageQueueLogger.new)
logger.log("This is a message.")
# Output: Log message added to message queue

```

Here is an advanced code example that demonstrates the Open/Closed Principle (OCP) in Ruby:

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
describe Shape do
  let(:shape) { Shape.new }

  it "calculates the area" do
    expect(shape).to respond_to(:area)
  end

  it "raises a NotImplementedError when the area method is called" do
    expect{ shape.area }.to raise_error(NotImplementedError, "Method not implemented")
  end
end

describe Circle do
  let(:radius) { 2 }
  let(:circle) { Circle.new(radius) }

  it "initializes with a radius" do
    expect(circle.instance_variable_get(:@radius)).to eq(radius)
  end

  it "calculates the area" do
    expect(circle.area).to eq(Math::PI * (radius ** 2))
  end
end

describe Square do
  let(:side) { 2 }
  let(:square) { Square.new(side) }

  it "initializes with a side length" do
    expect(square.instance_variable_get(:@side)).to eq(side)
  end

  it "calculates the area" do
    expect(square.area).to eq(side ** 2)
  end
end

describe Shapes do
  let(:shapes) { Shapes.new([]) }

  it "initializes with an array of shapes" do
    expect(shapes.instance_variable_get(:@shapes)).to eq([])
  end

  it "calculates the total area of all shapes in the collection" do
    circle = Circle.new(2)
    square = Square.new(2)

    shapes = Shapes.new([circle, square])
    expect(shapes.total_area).to eq(12.566370614359172)
  end
end

```

In this code example, the Shape, Circle, and Square classes demonstrate the Open/Closed Principle (OCP) by being open for extension and closed for modification. The Shape class is open for extension, as it allows developers to easily create new shapes by inheriting from the Shape class and implementing the appropriate methods. However, the Shape class is closed for modification, as the existing methods and interfaces should not be changed in order to maintain backward compatibility and avoid breaking existing code. The Shapes class is also open for extension, as it allows developers to easily add support for new shapes by implementing the appropriate interfaces. However, the Shapes class is closed for modification, as the existing methods and interfaces should not be changed in order to maintain backward compatibility and avoid breaking existing code.
