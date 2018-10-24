# Ranges
Ranges are an easy way to quickly create a sequence of numbers, and are very useful for `for` loops.

We've seen the most simple use of range already, inclusive:
```kotlin
for (i in 152..252) {
  // iterates over [152, 252]
}
```

They can be exclusive:
```kotlin
for (i in 152 until 251) {
  // iterates over [152, 251)
}
```

You can skip numbers:
```kotlin
for (i in 152..252 step 2) {
  // iterates over 152, 154, 156...
}
```

And they can be backwards:
```kotlin
for (i in 251..150) {
  // iterates over [251, 150]
}

for (i in 251 downTo 150) {
  // iterates over [251, 150)
}
```

[Back to `for`](/control-operators/for.md) | [Forward to smart cast](/compiler-magic/smartcast.md)
