⏺️ ➡️ 🟦 🔵 🟢🔴⭕🟠🟣🟥🟧✔️ ☑️ • ‣ → ⁕

# ⏺️ Comparator vs Comparable

## ➡️ Comparable

- `java.lang.Comparable<T>` interface has exactly 1 method `int compareTo(T o)`.
- No default or static methods
- Unchanged since **Java 1.2**(No additions in Java 5+ (generics) or **Java 8+** (lambdas don't add methods here).)

```java
   class Employee implements Comparable<Employee> {
    int age;
    public int compareTo(Employee other) {
        return this.age - other.age; // natural order by age
    }
}

```

## ➡️ Comparator

- `java.util.Comparator<T>` is a functional interface introduced in **Java 8.**

### 🟦 Abstract Method (only one)

```java
  Abstract Method (only one)
```

### 🟦 Default Methods (from Java 8 onwards)

| Method                                                          | Description                                                         |
| --------------------------------------------------------------- | ------------------------------------------------------------------- |
| `reversed()`                                                    | Returns a comparator that reverses the order.                       |
| `thenComparing(Comparator<? super T> other)`                    | Used for **chained comparisons** (e.g. first by age, then by name). |
| `thenComparing(Function<? super T, ? extends U> keyExtractor)`  | Same as above but using a key extractor function.                   |
| `thenComparingInt(ToIntFunction<? super T> keyExtractor)`       | For comparing primitive int keys efficiently.                       |
| `thenComparingLong(ToLongFunction<? super T> keyExtractor)`     | For comparing primitive long keys efficiently.                      |
| `thenComparingDouble(ToDoubleFunction<? super T> keyExtractor)` | For comparing primitive double keys efficiently.                    |

### 🟦 Static Methods

| Method                                                                                          | Description                                             |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------------------- |
| `comparing(Function<? super T, ? extends U> keyExtractor)`                                      | Builds a comparator based on a key extractor function.  |
| `comparing(Function<? super T, ? extends U> keyExtractor, Comparator<? super U> keyComparator)` | Same as above but allows custom comparator for the key. |
| `comparingInt(ToIntFunction<? super T> keyExtractor)`                                           | Builds comparator for int keys.                         |
| `comparingLong(ToLongFunction<? super T> keyExtractor)`                                         | Builds comparator for long keys.                        |
| `comparingDouble(ToDoubleFunction<? super T> keyExtractor)`                                     | Builds comparator for double keys.                      |
| `naturalOrder()`                                                                                | Returns a comparator using natural ordering.            |
| `reverseOrder()`                                                                                | Returns a comparator in reverse natural order.          |
| `nullsFirst(Comparator<? super T> comparator)`                                                  | Handles nulls before non-nulls.                         |
| `nullsLast(Comparator<? super T> comparator)`                                                   | Handles nulls after non-nulls.                          |

- **Employe Model**

```java
   package com.example.demo.model;

import java.time.LocalDate;

public class Employee {
    private int empId;
    private String name;
    private int age;
    private LocalDate dateOfJoining;
    private double salary;

    public Employee(int empId, String name, int age, LocalDate dateOfJoining, double salary) {
        this.empId = empId;
        this.name = name;
        this.age = age;
        this.dateOfJoining = dateOfJoining;
        this.salary = salary;
    }

    public int getEmpId() { return empId; }
    public String getName() { return name; }
    public int getAge() { return age; }
    public LocalDate getDateOfJoining() { return dateOfJoining; }
    public double getSalary() { return salary; }

    @Override
    public String toString() {
        return empId + " - " + name + " - " + age + " - " + dateOfJoining + " - " + salary;
    }
}

```

- **Controlller**

```java
  package com.example.demo.controller;

import com.example.demo.model.Employee;
import com.example.demo.service.EmployeeService;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.List;

@RestController
public class EmployeeController {

    private final EmployeeService employeeService;

    public EmployeeController(EmployeeService employeeService) {
        this.employeeService = employeeService;
    }

    @GetMapping("/employees/sort/age")
    public List<Employee> getEmployeesSortedByAge() {
        return employeeService.sortByAge();
    }

    @GetMapping("/employees/sort/date")
    public List<Employee> getEmployeesSortedByDateOfJoining() {
        return employeeService.sortByDateOfJoining();
    }

    @GetMapping("/employees/sort/date-salary")
    public List<Employee> getEmployeesSortedByDateAndSalary() {
        return employeeService.sortByDateOfJoiningAndSalary();
    }
}

```

- **Service**

```java
package com.example.demo.service;
import com.example.demo.model.Employee;
import com.example.demo.repository.EmployeeRepository;
import org.springframework.stereotype.Service;

import java.util.Comparator;
import java.util.List;
import java.util.stream.Collectors;

@Service
public class EmployeeService {

    private final EmployeeRepository employeeRepository;

    public EmployeeService(EmployeeRepository employeeRepository) {
        this.employeeRepository = employeeRepository;
    }

    // Sort by Age
    public List<Employee> sortByAge() {
        return employeeRepository.getAllEmployees()
                .stream()
                .sorted(Comparator.comparing(Employee::getAge))
                .collect(Collectors.toList());
    }

    // Sort by Date of Joining (Ascending)
    public List<Employee> sortByDateOfJoining() {
        return employeeRepository.getAllEmployees()
                .stream()
                .sorted(Comparator.comparing(Employee::getDateOfJoining))
                .collect(Collectors.toList());
    }

    // Sort by Date of Joining, then Salary
    public List<Employee> sortByDateOfJoiningAndSalary() {
        return employeeRepository.getAllEmployees()
                .stream()
                .sorted(
                        Comparator.comparing(Employee::getDateOfJoining)
                                .thenComparing(Employee::getSalary)
                )
                .collect(Collectors.toList());
    }
}

```

- **Repository**

```java
  package com.example.demo.repository;

import com.example.demo.model.Employee;
import org.springframework.stereotype.Repository;

import java.time.LocalDate;
import java.util.Arrays;
import java.util.List;

@Repository
public class EmployeeRepository {

    public List<Employee> getAllEmployees() {
        return Arrays.asList(
                new Employee(1, "John", 28, LocalDate.of(2022, 1, 10), 50000),
                new Employee(2, "Alice", 24, LocalDate.of(2023, 5, 1), 60000),
                new Employee(3, "Bob", 30, LocalDate.of(2021, 3, 15), 55000),
                new Employee(4, "David", 24, LocalDate.of(2023, 5, 1), 45000)
        );
    }
}

```
