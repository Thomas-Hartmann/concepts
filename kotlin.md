# Kotlin
## Table of contents
- declarations
- named arguments
- vararg
- constructors
- default arguments
- control flow
- lambdas
- string template
- data classes
- object
- nullable types
- smart casts
- extension functions
- SAM (Single Abstract Method) objects
- kotlin collections extensions
- collection filter and map methods
- collection: all, any, count, first a.m.
- list.flatmap
- max, min, maxBy
- list.sortedBy, list.groupBy
- list partition
- list fold
- compound tasks
- generics

### declarations
- val
   - immutable, threadsafe, prefered choice
   - `val aSentence = "Hello from kotlin"` the type string is infered (compiler can figure it out from context)
   - 
- var
   - variable
   - `var aSentence: String` no context for compiler to know the type. therefore must be declared.
### named arguments
### vararg
- list of input arguments that together becomes an array.
  - `fun foo(vararg strings: String) { ... }` and run it: `foo(strings = *arrayOf("a", "b", "c"))`
### types
- Unit (instead of void).
### constructors
### default arguments
### control flow
- if else
  - if is not a statement (like in java) it is an expression (returns a value)
  - ` `
- ternary expression 
  - `val lowest = if(myInt < someInt) myInt else someInt` there must be an else clause when if is used as expression. 
- when
  - `when(value){ 0-> println("blablablab")}`
- loop
  - for
  - while
  - do-while
- return , break, continoue
### lambdas
### string template
### data classes
### object expression
in kotlin it is possible to create an object whithout a class: 
```kotlin
val adHoc = object {
        var x: Int = 0
        var y: Int = 0
    }
```
### nullable types
### smart casts
### extension functions
### SAM (Single Abstract Method) objects
### Collections
- list
- map
- range
  - `for (j in 1..4){` and `if (i in 1..10){`
  - `for(item in 10.rangeTo(20).step(2)){`

### kotlin collections extensions
### collection filter and map methods
### collection: all, any, count, first a.m.
### list.flatmap
### max, min, maxBy
### list.sortedBy, list.groupBy
### list partition
### list fold
### compound tasks
### generics