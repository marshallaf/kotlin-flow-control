# `if`
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
} else { // required when used as an expression
  "It's fine."
}
```

### in place of ternary
```kotlin
val message = if (weight > minimum) "It's too heavy." else "It's fine."
```

[Back to start](/README.md) | [Forward to `when`](/control-operators/when.md)
