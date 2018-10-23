# Smart cast

In Java, we're familiar with this construct:
```java
if (animal instanceof Dog) {
  Dog dog = (Dog) animal;
  dog.bark()
}
```

But that's silly. There's no reason that we need to manually cast `animal` to `Dog` there, since we know if execution has passed that `if` check, the `animal` _must_ be a `Dog`.

So Kotlin instead uses a __smart cast__. The compiler can tell that by entering that block, the `animal` variable is necessarily of type `Dog` and therefore allows you to call `Dog`-specific methods on it, no manual casting required!
```kotlin
if (animal is Dog) {
  animal.bark() // animal is now understood to be a Dog
}
```

It can also be used with early `return`:
```kotlin
if (animal !is Dog) {
  return
}

animal.bark() // animal is understood to be a Dog
```

And it can also be used with `when`:
```kotlin
when (animal) {
  is Dog -> animal.bark()
  is Frog -> animal.ribbit()
  is Cat -> animal.meow()
}
```

However, the compiler can't always save you. It only works when the compiler can be absolutely sure that nothing else could have changed the variable in between the time that it was type-checked and the time which the type-specific property would be accessed.

This case typically arises when the variable is a mutable property of a class:
```kotlin
class NoiseMachine {
  var animal: Animal = Cat()

  fun makeNoise() {
    if (animal is Cat) {
      animal.meow() // wrong! animal could be something else meow.
    }
  }
}
```

[Back to ranges](/compiler-magic/ranges.md) | [Forward to scope functions](/scope-functions/intro.md)
