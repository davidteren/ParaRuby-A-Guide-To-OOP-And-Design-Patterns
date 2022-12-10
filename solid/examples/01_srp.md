# SRP Examples

## EXAMPLE 1

> **BAD**

```ruby
class ReportGenerator
  # Violates the Single Responsibility Principle (SRP)
  # because it does multiple things (fetching data,
  # formatting data, and printing the report)
  def generate(date, format)
    data = fetch_data(date)
    report = format_data(data, format)
    print(report)
  end

  def fetch_data(date)
    # code to fetch data from a database
  end

  def format_data(data, format)
    # code to format the data as a string
  end

  def print(report)
    # code to print the report
  end
end

```

This code violates the Single Responsibility Principle (SRP) because the generate method does multiple things: it fetches data, formats the data, and prints the report. This makes the code difficult to maintain and reuse, because if we want to change the way the data is fetched, formatted, or printed, we have to change the generate method, which does all of these things.

> **GOOD**

To fix this, we can separate the code into different classes, each with a single responsibility. For example:

```ruby
class ReportGenerator
  def initialize(data_fetcher, formatter, printer)
    @data_fetcher = data_fetcher
    @formatter = formatter
    @printer = printer
  end

  def generate(date, format)
    data = @data_fetcher.fetch(date)
    report = @formatter.format(data, format)
    @printer.print(report)
  end
end

class DataFetcher
  def fetch(date)
    # code to fetch data from a database
  end
end

class Formatter
  def format(data, format)
    # code to format the data as a string
  end
end

class Printer
  def print(report)
    # code to print the report
  end
end
```

This code follows the SRP, because each class has a single responsibility: the DataFetcher class is responsible for fetching data, the Formatter class is responsible for formatting the data, and the Printer class is responsible for printing the report. This makes the code easier to maintain and reuse, because we can change the way the data is fetched, formatted, or printed by modifying the corresponding class without affecting the others.

***

|   | [Index](../../) | [Next](02\_ocp.md) |
| - | --------------- | ------------------ |
