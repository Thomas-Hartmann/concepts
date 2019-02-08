# Principles of Object Oriented Programming
## Drawing with plant-uml
- [How to](http://plantuml.com/sequence-diagram)  
- [Online editor](http://www.plantuml.com/plantuml/uml/SoWkIImgAStDuNBCoKnELT2rKt3AJx9IA4a5IYGMfnHpEQJcfG3b0G00)
### relationships
[link to article](https://javarevisited.blogspot.com/2014/02/ifference-between-association-vs-composition-vs-aggregation.html)
- **Association**
    - when one object has a reference to another
    - **Aggregation** is a form of association where the referenced object can meaningfully exist when the "using" object is destroyed. Example: A school class that has reference to a student
    - **Composition** is a form of association where the referenced object cannot meaningfully exist outside the "owning" object: Example a human and its brain or hand. In java code this field can be **final**
- **Dependency**
    - A references B and depends on B. If B is changed it will change A. A owns or uses B. Example a CarportCalculator depends on a StykList to produce its results. Without the StykList object the Calculator cannot function.

UML:
![](https://1.bp.blogspot.com/-VL_9cjhwEE4/UvJN__IvaBI/AAAAAAAABCc/IkDmShgM-Yc/s1600/Association,+Composition+UML.JPG)

### Dependencies
[Link to jenkov tutorial](http://tutorials.jenkov.com/ood/understanding-dependencies.html)