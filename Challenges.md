Here are some Java development challenges that will help you apply the SOLID principles and deepen your understanding:

## 1. Single Responsibility Principle (SRP) Challenge:

Refactor the following code to adhere to SRP:

```java
class ReportGenerator {
    public void generatePDFReport() {
        // Code to generate PDF report
    }

    public void generateCSVReport() {
        // Code to generate CSV report
    }

    public void sendReportViaEmail(String report) {
        // Code to send report via email
    }
}
```

**Task:**

- Break down the class so that each class has only one responsibility.
- Introduce separate classes for report generation and report delivery.

## 2. Open/Closed Principle (OCP) Challenge:

Currently, this code violates the OCP. Refactor it so that the code is open for extension but closed for modification:

```java
class InvoicePrinter {
    public void printInvoice(String invoice, String format) {
        if (format.equals("PDF")) {
            // Code to print as PDF
        } else if (format.equals("HTML")) {
            // Code to print as HTML
        }
    }
}
```

**Task:**

- Use polymorphism and create separate classes for each format.
- Ensure that the InvoicePrinter can be extended with new formats without modifying its existing code.

## 3. Liskov Substitution Principle (LSP) Challenge:

The following code violates LSP. Can you fix it?

```java
class Bird {
    public void fly() {
        System.out.println("Bird is flying");
    }
}

class Penguin extends Bird {
    @Override
    public void fly() {
        throw new UnsupportedOperationException("Penguins can't fly");
    }
}
```

**Task:**

- Refactor the code so that Penguin does not violate the Liskov Substitution Principle.
- Create a structure where flying and non-flying birds can be managed correctly.

## 4. Interface Segregation Principle (ISP) Challenge:

You have an interface that seems too broad. Refactor it according to the ISP:

```java
interface Worker {
    void work();
    void eat();
}
class Human implements Worker {
    @Override
    public void work() {
        System.out.println("Human is working");
    }

    @Override
    public void eat() {
        System.out.println("Human is eating");
    }
}
class Robot implements Worker {
    @Override
    public void work() {
        System.out.println("Robot is working");
    }

    @Override
    public void eat() {
        // Robots do not eat, this is a problem
        throw new UnsupportedOperationException("Robots don't eat");
    }
}
```

**Task:**

- Split the Worker interface into more focused interfaces, such as Workable and Eatable.
- Implement the interfaces so that Robot no longer has to deal with an unsupported eat() method.

## 5. Dependency Inversion Principle (DIP) Challenge:

The following code is tightly coupled. Refactor it to follow the Dependency Inversion Principle:

```java
class WindowsFileWriter {
    public void writeToFile(String content) {
        // Code to write to a file in Windows
    }
}

class DocumentProcessor {
    private WindowsFileWriter fileWriter = new WindowsFileWriter();

    public void process(String content) {
        // Process the document
        fileWriter.writeToFile(content);
    }
}
```

**Task:**

- Introduce an interface for writing to a file, and decouple the DocumentProcessor class from the WindowsFileWriter implementation.
- Create a flexible architecture where the file writing mechanism can be easily swapped out.

## 6. Bonus Challenge: SOLID Refactor

You have been given a class that violates multiple SOLID principles. Refactor it to apply all five SOLID principles:

```java
class ShoppingCart {
    private List<String> items = new ArrayList<>();
    private double total;

    public void addItem(String item) {
        items.add(item);
    }

    public void calculateTotal() {
        for (String item : items) {
            // Logic to calculate total
        }
    }

    public void checkout() {
        // Logic to process payment and checkout
    }

    public void generateReceipt() {
        // Logic to generate receipt
    }
}
```

**Task:**

- Refactor this ShoppingCart class so that each responsibility is handled by a different class or method, following SOLID principles.
- Ensure that your design is open for extension, easily testable, and respects LSP, ISP, and DIP.

## Additional Considerations:

- **Testing**: For each of the above challenges, write unit tests to ensure your refactoring works as expected.
- **Extensions**: In some challenges, extend the functionality by adding new features (e.g., adding a new file format for the OCP challenge) without changing existing code.
- **Dependency Injection**: Where applicable, practice using dependency injection in your refactored code (using constructor or setter injection).

These challenges will help you grasp the intricacies of SOLID principles in a hands-on way! Let me know if you need further guidance on any of these.
