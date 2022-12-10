# OCP

## EXAMPLE 1

> **BAD**

Here is an example of bad Ruby code that violates the Open/Closed Principle (OCP), which is one of the principles of the SOLID design principles:

```ruby
class ReportGenerator
  def generate(date, format)
    data = fetch_data(date)

    if format == :pdf
      generate_pdf(data)
    elsif format == :csv
      generate_csv(data)
    elsif format == :xlsx
      generate_xlsx(data)
    end
  end

  def fetch_data(date)
    # code to fetch data from a database
  end

  def generate_pdf(data)
    # code to generate a PDF report
  end

  def generate_csv(data)
    # code to generate a CSV report
  end

  def generate_xlsx(data)
    # code to generate an XLSX report
  end
end

```

This code violates the OCP because it is not open for extension and closed for modification. In particular, the generate method has a long if statement that checks the format argument and calls a different method depending on its value. This means that if we want to support a new format, such as JSON, we have to modify the generate method to add another if statement and another method, generate\_json, to handle the new format.

To fix this, we can use polymorphism to make the code more flexible and extensible. For example:

> **Good**

```ruby
class ReportGenerator
  def generate(date, formatter)
    data = fetch_data(date)
    formatter.format(data)
  end

  def fetch_data(date)
    # code to fetch data from a database
  end
end

class PDFFormatter
  def format(data)
    # code to generate a PDF report
  end
end

class CSVFormatter
  def format(data)
    # code to generate a CSV report
  end
end

class XLSXFormatter
  def format(data)
    # code to generate an XLSX report
  end
end

```

This code follows the OCP because it is open for extension and closed for modification. In particular, the generate method accepts a formatter object as an argument and calls the format method on it, without knowing or caring what class the object belongs to. This means that if we want to support a new format, such as JSON, we can create a new class, JSONFormatter, that implements the format method and pass an instance of this class to the generate method. The generate method will be able to use the format method without needing to be modified.

***

| [Previous](01\_srp.md) | [Index](../../) | [Next](03\_lsp.md) |
| ---------------------- | --------------- | ------------------ |
