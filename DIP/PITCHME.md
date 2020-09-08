##### SOLID principles
## Dependency Inversion Principle

---

@snap[north-west span-100]
## Definition
@snapend

@snap[south span-100]
**DIP** is one of the *SOLID* object-oriented principle invented by *Robert Martin*

@snap[span-100 mt-5]
Definition of principle:
@snapend

@ol[list-spaced-bullets]
1. High-level modules should not depend on low-level modules. Both should depend on the abstraction.
1. Abstractions should not depend on details. Details should depend on abstractions.
@olend
@snapend

---

@snap[north-west span-100]
### Example
@snapend

@snap[south span-100]
@code[cs zoom-05 code-power](src/code/DIP_bad.cs)
@snapend

@snap[east span-50 text-07 z-1000]
@snap[fragment span-100]
*CustomerBusinessLogic* and *DataAccess* are tightly coupled
@snapend

@snap[fragment span-100]
Let's use **DIP** and make them more loosely coupled.
@snapend
@snapend

---

@snap[north-west span-100]
## Modules
@snapend

@snap[south span-100]
@css[text-12](Which is the high-level module and the low-level module?)

@snap[fragment span-100]
@ul[mt-5](false)
- *CustomerBusinessLogic* is high-level module
- *DataAccess* is low-level module
@ulend

@css[text-03 mt-5](A high-level module is a module which depends on other modules)
@snapend

@snap[mt-5]
@snapend
@snapend

---

@snap[north-west span-100]
## What is abstraction?
@snapend

In English, abstraction means something which is non-concrete. In programming terms, the above *CustomerBusinessLogic* and *DataAccess* are concrete classes, meaning we can create objects of them. So, abstraction in programming means to create an interface or an abstract class which is non-concrete. This means we cannot create an object of an interface or an abstract class.

---

@snap[north-west span-100]
## Abstraction
@snapend

What should be in the interface (or in the abstract class)?

@snap[fragment span-100 mt-5]
*CustomerBusinessLogic* uses the **GetCustomerName()** method of the *DataAccess* class. So, we can declare the **GetCustomerName(int id)** method in the interface.

@snap[span-50]
@code[cs zoom-08](src/code/DIP_good.cs?lines=1-4)
@snapend
@snapend

---

@snap[north-west span-100]
### Good code
@snapend

@snap[span-100 mt-5]
@code[cs zoom-05 code-power](src/code/DIP_good.cs?lines=6-37)
@snapend

@snap[north-east span-60 mt-5]
@[1-8, zoom-12](*CustomerDataAccess* class, which implements *ICustomerDataAccess* interface)
@[10-16, zoom-12](Now, our factory class returns *ICustomerDataAccess* instead of the concrete *DataAccess* class)
@[18-34, zoom-12](And, *CustomerBusinessLogic* class which uses *ICustomerDataAccess* instead of the concrete *DataAccess*)
@snapend

---

@snap[north-west span-100]
## Advantage
@snapend

The advantages of implementing **DIP** in the above example is that the *CustomerBusinessLogic* and *CustomerDataAccess* classes are loosely coupled classes because *CustomerBusinessLogic* does not depend on the concrete *DataAccess* class, instead it includes a reference of the *ICustomerDataAccess* interface. So now, we can easily use another class which implements *ICustomerDataAccess* with a different implementation.

---

## Thank you for attention!