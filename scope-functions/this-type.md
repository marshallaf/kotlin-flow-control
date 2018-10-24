# `this`-type scope functions

`apply`:
```kotlin
inline fun <T> T.apply(block: T.() -> Unit): T

val sb = StringBuilder()
sb.apply {
  this.append("eg")
  append("g")
}
val breakfast = sb.toString()
```

`run`:
```kotlin
inline fun <T, R> T.run(block: T.() -> R): R

val sb = StringBuilder()
val breakfast = sb.run {
  this.append("eg")
  append("g")
  toString() // last statement is the return
}
```

`with`:
```kotlin
inline fun <T, R> with(receiver: T, block: T.() -> R): R

val sb = StringBuilder()
val breakfast = with(sb) {
  this.append("eg")
  append("g")
  toString()
}
```

See all the `T.()` in the `block` definitions? The `block` is the lambda, and the `T` is the receiver.

The point of all these is to change the scope to `T`. Instead of `this` referring to whatever class you're running it in, it refers to `T`.
```kotlin
class Chef {
  fun makeBreakfast() {
    println(this) // this == the Chef object

    val sb = StringBuilder()
    sb.apply {
      println(this) // this == sb
    }
  }
}
```

[Back to scope functions intro](/scope-functions/intro.md) | [Forward to it-type scope functions](/scope-functions/it-type.md)
