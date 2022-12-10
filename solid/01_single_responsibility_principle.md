# The Single Responsibility Principle

The Single Responsibility Principle (SRP) is a principle of object-oriented programming (OOP) that states that a class should only have a single responsibility, or a single reason to change. In other words, a class should focus on one specific aspect of the problem domain, and should not be cluttered with unrelated responsibilities or functionality.

> #### Explain The Single Responsibility Principle like I'm five
>
> The Single Responsibility Principle is like a job. Everyone has a different job, and they do their job really well. For example, one person might be really good at making cookies, and another person might be really good at washing dishes. If they each just do their own job, then they will be able to make lots of cookies and wash lots of dishes. But if they try to do each other's job, then they might not be as good at it, and they might not be able to make as many cookies or wash as many dishes. So it's better for everyone to just do their own job and not try to do other people's jobs.

In Ruby, the SRP can be applied by defining separate classes for different responsibilities, and using methods and attributes to encapsulate the relevant data and behavior. For example, instead of having a single Person class that handles both the person's name and age, we could define a Person class and a separate Age class:

```ruby
class Person
  attr_accessor :name

  def initialize(name)
    @name = name
  end
end

class Age
  attr_accessor :age

  def initialize(age)
    @age = age
  end
end

person = Person.new("John")
age = Age.new(25)
```

This approach allows us to focus each class on a specific responsibility, and makes it easier to maintain and modify the code in the future.

This means that a class should not be responsible for multiple, unrelated tasks or responsibilities. Instead, each class should have a clear and well-defined purpose and should only be responsible for the tasks that are necessary to fulfill that purpose.

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

# Define a class called "Employee"
class Employee < Person
  # Define attributes for the Employee class
  attr_accessor :title, :salary

  # Define a constructor method for initializing new Employee objects
  def initialize(name, age, title, salary)
    # Use the super keyword to initialize the name and age attributes from the parent Person class
    super(name, age)
    @title = title
    @salary = salary
  end

  # Define a method for calculating the annual salary for an Employee
  def calculate_annual_salary
    @salary * 12
  end
end

# Create a new Employee object
employee = Employee.new("John", 25, "Software Engineer", 75000)

# Use the Employee's calculate_annual_salary method to calculate their annual salary
annual_salary = employee.calculate_annual_salary
```

In this code, we define two classes: Person and Employee. The Person class is responsible for modeling a person and providing a method for greeting another person. The Employee class is responsible for modeling an employee and providing a method for calculating their annual salary. By separating these two responsibilities into separate classes, we are following the SRP and making our code more modular and maintainable.

In Ruby, this principle can be applied by ensuring that each class has a well-defined and narrowly focused purpose, and by avoiding the inclusion of unnecessary or unrelated functionality.

For example, consider a class that represents a bank account. The Single Responsibility Principle would dictate that this class should be responsible only for storing and manipulating information about the account (e.g. balance, transactions), and not for other tasks such as rendering HTML or sending email notifications. This would help to keep the class focused and easier to maintain.

```ruby
class BankAccount
  attr_accessor :balance

  def initialize(balance)
    @balance = balance
  end

  def deposit(amount)
    @balance += amount
  end

  def withdraw(amount)
    @balance -= amount
  end
end
```

This `BankAccount` class only has a single responsibility, which is to store and manipulate information about the account. It does not include any unrelated functionality such as rendering HTML or sending email notifications. This makes the class more focused and easier to maintain.

More examples

```ruby
# Define a class called "Person" that only has a single responsibility: managing information about a person
class Person
  attr_accessor :name, :age

  def initialize(name, age)
    @name = name
    @age = age
  end
end

# Define a separate class called "EmailSender" that only has a single responsibility: sending emails
class EmailSender
  def send_email(to, subject, body)
    # Send the email
  end
end

# Define a separate class called "Database" that only has a single responsibility: storing data
class Database
  def save(data)
    # Save the data to the database
  end
end

# Create a new Person object
person = Person.new("John", 25)

# Create an EmailSender object and use it to send an email
email_sender = EmailSender.new
email_sender.send_email("jane@example.com", "Hello!", "Hi there!")

# Create a Database object and use it to save data
database = Database.new
database.save({name: "John", age: 25})
```

In this code, we define three separate classes, each with a clear and focused responsibility. The Person class is responsible for managing information about a person, the EmailSender class is responsible for sending emails, and the Database class is responsible for storing data. This approach helps to promote code that is more modular, reusable, and maintainable.

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

# Define a separate class called "PersonValidator" to handle validation
class PersonValidator
  # Define a method for validating a Person object
  def validate(person)
    # Check if the person's name and age are valid
    if person.name.nil? || person.age.nil?
      raise "Invalid person: name and age are required"
    end
  end
end

# Create a new Person object
p1 = Person.new("John", 25)

# Create a new PersonValidator object
validator = PersonValidator.new

# Validate the Person object using the PersonValidator
validator.validate(p1)
```

In this code, we define two classes: Person and PersonValidator. The Person class is responsible for modeling a person's name and age, and has a greet method for greeting another person. The PersonValidator class is responsible for validating a Person object, and has a validate method that checks if the person's name and age are valid. By separating the validation logic into a separate class, we are following the Single Responsibility Principle and ensuring that each class has a clear and well-defined responsibility. This can improve the maintainability and reusability of the code.

### Advanced code Examples of Single Responsibility Principle in Ruby with inheritance

Here is an advanced code example of the Single Responsibility Principle (SRP) in Ruby with inheritance:

A Person class that manages a person's name and age, and a Student class that inherits from Person and adds a student ID, a Teacher class that inherits from Person and adds a subject and salary, and a Course class that manages a course's name, teacher, and students:

```ruby
class Person
  attr_accessor :name, :age

  def initialize(name, age)
    @name = name
    @age = age
  end
end

class Student < Person
  attr_accessor :id

  def initialize(name, age, id)
    super(name, age)
    @id = id
  end
end

class Teacher < Person
  attr_accessor :subject, :salary

  def initialize(name, age, subject, salary)
    super(name, age)
    @subject = subject
    @salary = salary
  end
end

class Course
  attr_accessor :name, :teacher, :students

  def initialize(name, teacher, students)
    @name = name
    @teacher = teacher
    @students = students
  end

  def add_student(student)
    @students << student
  end

  def remove_student(student)
    @students.delete(student)
  end
end
```

In this example, the Person class only manages a person's name and age, the Student and Teacher classes only manage additional attributes specific to students and teachers, and the Course class only manages a course's name, teacher, and students. This promotes code that is more modular and maintainable.

Here is an advanced code example of the Single Responsibility Principle (SRP) in Ruby with inheritance, featuring a Calculator class that provides methods for performing arithmetic operations, a ScientificCalculator class that inherits from Calculator and adds methods for scientific functions, and a History class that manages a history of calculations:

```ruby
class Calculator
  def add(a, b)
    a + b
  end

  def subtract(a, b)
    a - b
  end

  def multiply(a, b)
    a * b
  end

  def divide(a, b)
    a / b
  end
end

class ScientificCalculator < Calculator
  def square_root(a)
    Math.sqrt(a)
  end

  def logarithm(a)
    Math.log(a)
  end

  def exponent(a, b)
    a ** b
  end

  def factorial(a)
    (1..a).inject(:*) || 1
  end
end

class History
  def self.add(calculation)
    @history ||= []
    @history << calculation
  end

  def self.clear
    @history = []
  end

  def self.print
    @history.each do |calculation|
      puts calculation
    end
  end
end
```

## Here are two examples of the Single Responsibility Principle (SRP) in Ruby on Rails:

1. A Product model that manages a product's name, price, and quantity, and a ShoppingCart controller that manages a list of products and their total price:

```ruby
class Product < ActiveRecord::Base
  validates :name, presence: true
  validates :price, presence: true, numericality: true
  validates :quantity, presence: true, numericality: { only_integer: true }
end

class ShoppingCartController < ApplicationController
  def add_product
    product = Product.find(params[:product_id])
    cart = session[:shopping_cart] ||= []
    cart << product
  end

  def remove_product
    product = Product.find(params[:product_id])
    cart = session[:shopping_cart]
    cart.delete(product) if cart
  end

  def total
    cart = session[:shopping_cart]
    @total = 0
    if cart
      cart.each do |product|
        @total += product.price
      end
    end
  end
end

```

1. A BankAccount model that manages a bank account's balance and transactions, and a Statement controller that generates a statement of transactions:

```ruby
class BankAccount < ActiveRecord::Base
  validates :balance, presence: true, numericality: true

  def deposit(amount)
    self.balance += amount
  end

  def withdraw(amount)
    self.balance -= amount
  end
end

class StatementController < ApplicationController
  def generate
    @account = BankAccount.find(params[:account_id])
    @transactions = @account.transactions.order(created_at: :desc)
  end
end

```

Here are some RSpec tests for the BankAccount and StatementController classes:

```ruby
describe BankAccount do
  let(:account) { BankAccount.new }

  it "has a balance" do
    expect(account).to respond_to(:balance)
  end

  it "validates the presence of the balance" do
    expect(account).to validate_presence_of(:balance)
  end

  it "validates the numericality of the balance" do
    expect(account).to validate_numericality_of(:balance)
  end

  describe "#deposit" do
    it "increases the balance by the specified amount" do
      expect { account.deposit(100) }.to change(account, :balance).by(100)
    end
  end

  describe "#withdraw" do
    it "decreases the balance by the specified amount" do
      account.deposit(100)
      expect { account.withdraw(50) }.to change(account, :balance).by(-50)
    end
  end
end

describe "POST /products" do
  it "creates a new product" do
    post "/products", params: { product: { name: "Product A", price: 10, quantity: 5 } }
    expect(response).to have_http_status(:created)
    expect(Product.last).to have_attributes(name: "Product A", price: 10, quantity: 5)
  end

  it "returns an error if the product is invalid" do
    post "/products", params: { product: { name: "Product A", price: -10, quantity: 5 } }
    expect(response).to have_http_status(:unprocessable_entity)
    expect(response.body).to include("Validation failed")
  end
end

describe "POST /shopping_cart/add_product" do
  let(:product) { Product.create(name: "Product A", price: 10, quantity: 5) }

  it "adds a product to the shopping cart" do
    post "/shopping_cart/add_product", params: { product_id: product.id }
    expect(response).to have_http_status(:ok)
    expect(session[:shopping_cart]).to eq([product])
  end
end

describe "POST /shopping_cart/remove_product" do
  let(:product) { Product.create(name: "Product A", price: 10, quantity: 5) }

  it "removes a product from the shopping cart" do
    session[:shopping_cart] = [product]
    post "/shopping_cart/remove_product", params: { product_id: product.id }
    expect(response).to have_http_status(:ok)
    expect(session[:shopping_cart]).to be_empty
  end
end

describe "GET /shopping_cart/total" do
  let(:product) { Product.create(name: "Product A", price: 10, quantity: 5) }

  it "calculates the total price of products in the shopping cart" do
    session[:shopping_cart] = [product]
    get "/shopping_cart/total"
    expect(response).to have_http_status(:ok)
    expect(response.body).to eq("10")
  end
end
```

```ruby
describe Product do
  let(:product) { Product.new }

  it "has a name" do
    expect(product).to respond_to(:name)
  end

  it "validates the presence of the name" do
    expect(product).to validate_presence_of(:name)
  end

  it "has a price" do
    expect(product).to respond_to(:price)
  end

  it "validates the presence of the price" do
    expect(product).to validate_presence_of(:price)
  end

  it "validates the numericality of the price" do
    expect(product).to validate_numericality_of(:price)
  end

  it "has a quantity" do
    expect(product).to respond_to(:quantity)
  end

  it "validates the presence of the quantity" do
    expect(product).to validate_presence_of(:quantity)
  end

  it "validates the numericality of the quantity" do
    expect(product).to validate_numericality_of(:quantity).only_integer
  end
end

describe ShoppingCartController do
  let(:product) { Product.create(name: "Product A", price: 10, quantity: 5) }

  it "adds a product to the shopping cart" do
    post :add_product, params: { product_id: product.id }
    expect(session[:shopping_cart]).to eq([product])
  end

  it "removes a product from the shopping cart" do
    session[:shopping_cart] = [product]
    post :remove_product, params: { product_id: product.id }
    expect(session[:shopping_cart]).to be_empty
  end

  it "calculates the total price of products in the shopping cart" do
    session[:shopping_cart] = [product]
    get :total
    expect(assigns(:total)).to eq(10)
  end
end
```

| [Previous](the\_five\_principles.md) | [Index](../) | [Next](02\_open\_closed\_principle.md) |
| ------------------------------------ | ------------ | -------------------------------------- |
