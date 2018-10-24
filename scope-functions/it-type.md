# `it`-type scope functions
Redefining `this` is great sometimes, but sometimes it's annoying because then you don't have succinct access to the old `this`.

To avoid this, `it`-type scope functions use the receiver of the scope function as the argument to the lambda block.

`let`:
```kotlin
inline fun <T, R> T.let(block: (T) -> R): R

class Chef {
  fun getName() = "Jeff"

  fun makeBreakFast(): String {
    val breakfast = StringBuilder().let {
      it.append("egg made by Chef ") // it is the StringBuilder
      it.append(this.getName()) // this is the Chef
      toString()
    }
    return breakfast
  }
}
```

`also`:
```kotlin
inline fun <T> T.also(block: (T) -> Unit): T

class Chef {
  fun getName() = "Jeff"

  fun makeBreakFast(): String {
    val breakfastBuilder = StringBuilder().also {
      it.append("egg made by Chef ") // it is the StringBuilder
      it.append(this.getName()) // this is the Chef
    }
    return breakfastBuilder.toString()
  }
}
```

[Back to this-type scope functions](/scope-functions/this-type.md) | [Forward to scope functions and nullability](/scope-functions/null-checking.md)
