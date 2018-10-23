# `when`
`when` is generally a replacement for `switch`, but the cases can be more varied, and the compiler helps when it can.

```kotlin
val specialNumbers = listOf(4, 8, 9)
when (number) {
  1,3 -> println("This is prime.") // separated values with comma
  2 -> println("This is prime, but it's the only even one.")
  in 4..6 -> println("It's either 4 or 5.") // using a range
  in specialNumbers -> println("This is special") // contained in a collection
  else -> println("This number is too big to figure out.")
}
```
Note that if `number` was `4`, it would satisfy two conditions. Because the case `in 4..6` comes before the case `in specialNumbers`, it will execute the path that prints `"It's either 4 or 5."`.

`when` can also be used as an expression.
```kotlin
val omeletteMessage = when (egg) {
  is OstrichEgg -> "The egg is too big for an omelette."
  is QuailEgg -> "The egg is too small for an omelette."
  else -> {
    makeOmelette()
    "The egg is perfect for an omelette!"
  }
}
```

Normally, `when` requires an `else` condition when used as an expression. However, if the compiler can prove that a `when`'s conditions are exhaustive, then the `else` condition can be omitted.
```kotlin
enum class Rsvp {
  YES, 
  YES_PLUS_ONE, 
  NO
}

val response = when (rsvp) {
  Rsvp.YES -> "See you there."
  Rsvp.YES_PLUS_ONE -> "See you both there."
  Rsvp.NO -> "Sorry you can't make it."
}
```

`when` doesn't necessarily need an argument.
```kotlin
val omeletteMessage = when {
  egg.weight > 5 -> "too big"
  egg.weight < 1 -> "too small"
  else -> "just right"
}
```


[Back to `if`](/control-operators/if.md) | [Forward to `for`](/control-operators/for.md)
