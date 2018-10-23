# Flow control in Kotlin

---

## if
`if` works in mostly the same way as in Java, but it can now be used as an expression.

### standard usage
```kotlin
if (weight > minimum) {
  showMessage("It's too heavy.")
} else { // not required in standard usage
  showMessage("It's fine.")
}
```

### as expression
```kotlin
val message = if (weight > minimum) {
  "It's too heavy."
} else { // required when used as expression
  "It's fine."
}
```

### in place of ternary
```kotlin
val message = if (weight > minimum) "It's too heavy." else "It's fine."
```

---

## when
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