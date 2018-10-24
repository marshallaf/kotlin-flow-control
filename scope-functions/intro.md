# Scope functions
Extension functions in Kotlin all have a __reciever__, which is the object that the function is called on:
```kotlin
inline fun <T> Iterable<T>.printAll() {
  for (element in this) {
    println(element)
  }
}
```
Note that the `Iterable` above becomes `this` in the function definition: the scope is now the `Iterable` itself.

The method above would be called like:
```kotlin
myList.printAll()
```

Kotlin also allows lambda function, typically of a form like:
```kotlin
() -> R
(T) -> Unit
(T) -> R
```

__Scope functions__ combine the scoping of extension functions with the customizability of lambdas. The purpose of scope functions is to redefine the local scope of execution.

Kotlin has a number of scope functions, each of which has a different combination of scoping and lambda structure.

[Back to smart cast](/compiler-magic/smartcast.md) | [Forward to this-type scope functions](/scope-functions/this-type.md)
