---?color=linear-gradient(180deg, white 66.66%, #1B1B1B 33.33%)

@snap[north span-100]
![](assets/images/mediator/main_image.png)
@snapend

@snap[south span-100 h2-white]
# Mediator 
@snapend

---

**Mediator** is a behavioral design pattern that lets you reduce chaotic dependencies between objects. The pattern restricts direct communications between the objects and forces them to collaborate only via a mediator object.

---

@snap[north]
## @fa[frown] Problem
@snapend

Say you have a dialog for creating and editing customer profiles. It consists of various form controls such as text fields, checkboxes, buttons, etc.

---

@snap[north]
## @fa[frown] Problem
@snapend

![filter=invert](assets/images/mediator/problem.png)

@snap[south span-100]
@ul[text-06]
- Relations between elements of the user interface can become chaotic as the application evolves.
- Elements can have lots of relations with other elements. Hence, changes to some elements may affect the others.
@ulend
@snapend

---

@snap[north]
## @fa[smile] Solution
@snapend

Use mediator

![filter=invert](assets/images/mediator/solution.png)

---

@snap[north]
## @fa[smile] Solution
@snapend

@css[text-07](The Mediator pattern suggests that you should cease all direct communication between the components which you want to make independent of each other. Instead, these components must collaborate indirectly, by calling a special mediator object that redirects the calls to appropriate components. As a result, the components depend only on a single mediator class instead of being coupled to dozens of their colleagues.)

---

@snap[north]
## Diagram
@snapend

@snap[west span-50]
![filter=invert](assets/images/mediator/diagram.png)
@snapend

@snap[east span-40 text-05]
@ul[list-square-bullets list-spaced-bullets list-fade-fragments] 
- **Mediator**. Defines the interface for communication between components
- **AuthenticationDialog**. Implements the mediator interface and coordinates communication between UI components
- **Component**. Base class of UI components that defines the interface for communication od components via mediator
- **Button, Textbox, Checkbox**. Inherit Component class
@ulend
@snapend

---

@snap[north text-07 z-1000]
## Code time
@snapend

@snap[midpoint span-100]
@code[cs zoom-04](src/code/mediator.cs?lines=5-37)
@snapend

@snap[south span-100 text-06]
@[1-4, zoom-16](The Mediator interface declares a method used by components to notify the mediator about various events. The Mediator may react to these events and pass the execution to other components.)
@[6-33, zoom-16](Concrete Mediators implement cooperative behavior by coordinating several components.)
@snapend

---

@code[cs zoom-04](src/code/mediator.cs?lines=39-86)

@snap[south span-100 text-06]
@[1-14, zoom-16](The Base Component provides the basic functionality of storing a mediator's instance inside component objects.)
@[16-48, zoom-16](Concrete Components implement various functionality. They don't depend on other components. They also don't depend on any concrete mediator classes.)
@snapend

---

@snap[north]
## Client code
@snapend

@snap[west span-48 code-wrap]
@code[cs zoom-06](src/code/mediator.cs?lines=88-104)
@snapend

@snap[east span-48]
``` plaintext zoom-06
Client triggers operation A.
Component 1 does A.
Mediator reacts on A and triggers following operations:
Component 2 does C.

Client triggers operation D.
Component 2 does D.
Mediator reacts on D and triggers following operations:
Component 1 does B.
Component 2 does C.
```
@snapend

---?color=linear-gradient(100deg, #1B1B1B 50%, #EC4D37 50.2%)

@snap[north-west span-40]
## Pros
@ol[pros-list list-spaced-bullets text-05]
- *Single Responsibility Principle*. You can extract the communications between various components into a single place, making it easier to comprehend and maintain.
- *Open/Closed Principle*. You can introduce new mediators without having to change the actual components.
- You can reduce coupling between various components of a program.
- You can reuse individual components more easily.
@olend
@snapend

@snap[north-east span-40]
## @color[#1B1B1B](Cons)
@ol[cons-list list-spaced-bullets text-05]
- Over time a mediator can evolve into a *@color[#2d2f34](God Object)*.
@olend
@snapend

---

@snap[north]
## Task
@snapend

Implement simple chatroom, where are many participant. Praticipants can be one of three types: **Admin**, **Moderator**, **Guest**

***Good luck!***