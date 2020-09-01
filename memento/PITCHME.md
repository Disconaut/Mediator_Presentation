---?color=linear-gradient(180deg, white 66.66%, #1B1B1B 33.33%)

@snap[north span-100]
![](assets/images/memento/main_image.png)
@snapend

@snap[south span-100 h2-white]
# Memento 
@snapend

---

**Memento** is a behavioral design pattern that lets you save and restore the previous state of an object without revealing the details of its implementation.

---

@snap[north]
## @fa[frown] Problem
@snapend

Imagine that you’re creating a text editor app. In addition to simple text editing, your editor can format text, insert inline images, etc. At some point, you decided to let users undo any operations carried out on the text. This feature has become so common over the years that nowadays people expect every app to have it.

---

@snap[north]
## @fa[frown] Problem
@snapend

@snap[west span-45 text-06 text-center]
![filter=invert](assets/images/memento/problem1.png)
Before executing an operation, the app saves a snapshot of the objects’ state, which can later be used to restore objects to their previous state.
@snapend

@snap[midpoint fragment]
**BUT**
@snapend

@snap[east span-45 text-06 text-center fragment]
![filter=invert](assets/images/memento/problem2.png)
How to make a copy of the object’s private state?
@snapend

@snap[south span-100 text-06 fragment]
@css[text-16 text-uppercase](**AND ONE MORE PROBLEM**)
To allow other objects to write and read data to and from a snapshot, you’d probably need to make its fields public.
@snapend

---

@snap[north]
## @fa[smile] Solution
@snapend

@snap[west span-45 text-center]
Use memento

![filter=invert](assets/images/memento/solution.png)
@snapend

@snap[east span-45]
The originator must have full access to the memento, whereas the caretaker can only access the metadata.
@snapend

---

@snap[north]
## @fa[smile] Solution
@snapend

The Memento pattern delegates creating the state snapshots to the actual owner of that state, the originator object. Hence, instead of other objects trying to copy the editor’s state from the “outside,” the editor class itself can make the snapshot since it has full access to its own state.

---

@snap[north]
## Diagram
@snapend

@snap[west span-50]
![filter=invert](assets/images/memento/diagram_example.png)
@snapend

@snap[east span-40 text-05]
@ul[list-square-bullets list-spaced-bullets list-fade-fragments] 
- **Editor**. The object for which the state is to be saved. It creates the memento and uses it in future to undo
- **Snapshot**. The object that is going to save the state of originator
- **Command**. The object that keeps last snapshot. Is used to call undo operation
@ulend
@snapend

---

@snap[north span-100]
## More diagrams
@snapend

@snap[south-west span-43 text-center]
![filter=invert](assets/images/memento/diagram1.png)
@snapend

@snap[south-east span-43]
![filter=invert](assets/images/memento/diagram2.png)
@snapend

@snap[midpoint span-43]
![filter=invert](assets/images/memento/diagram3.png)
@snapend

---

@snap[north text-07 z-1000]
## Code time
@snapend

@snap[midpoint span-100]
@code[cs zoom-04](src/code/memento.cs?lines=8-45)
@snapend

@snap[south span-100 text-06]
@[1, zoom-16](The Originator holds some important state that may change over time. It also defines a method for saving the state inside a memento and another method for restoring the state from it.)
@[10-14, zoom-16](Saves the current state inside a memento.)
@[16-25, zoom-16](Restores the Originator's state from a memento object.)
@snapend

---

@snap[north span-100]
@code[cs zoom-04](src/code/memento.cs?lines=47-82)
@snapend

@snap[south span-100 text-06]
@[1-8, zoom-16](The Memento interface provides a way to retrieve the memento's metadata, such as creation date or name. However, it doesn't expose the Originator's state.)
@[10-36, zoom-16](The Concrete Memento contains the infrastructure for storing the Originator's state.)
@snapend

---

@snap[north span-100]
@code[cs zoom-04 code-max](src/code/memento.cs?lines=84-121)
@snapend

@snap[south span-100 text-05]
The Caretaker doesn't depend on the Concrete Memento class. Therefore, it doesn't have access to the originator's state, stored inside the memento. It works with all mementos via the base Memento interface.
@snapend

---?color=linear-gradient(100deg, #1B1B1B 50%, #EC4D37 50.2%)

@snap[north-west span-40]
## Pros
@ol[pros-list list-spaced-bullets text-05]
- You can produce snapshots of the object’s state without violating its encapsulation.
- You can simplify the originator’s code by letting the caretaker maintain the history of the originator’s state.
@olend
@snapend

@snap[north-east span-40]
## @color[#1B1B1B](Cons)
@ol[cons-list list-spaced-bullets text-05]
- The app might consume lots of *@color[#2d2f34](RAM)* if clients create mementos too often.
- Caretakers should track the originator’s lifecycle to be able to destroy obsolete mementos.
- Most dynamic programming languages, such as PHP, Python and JavaScript, can’t guarantee that the state within the memento stays untouched.
@olend
@snapend

---

@snap[north]
## Task
@snapend

Implement game saving. Game state consists of: *Player*, *Enemies positions*, *Seed*(random string).

**Player** has his *position* and *level*.

***Good luck!***