# `for`
`for` loops can be used on anything that has an iterator. To do a basic numeric `for` loop, use a range:
```kotlin
for (i in 152..252) {
  println("Pokemon $i is in Generation II.")
}
```

You can also use it with other collections like a Java for/each loop:
```kotlin
for (element in collection) {
  println("This is a $element")
}
```
...or if you need the index:
```kotlin
for (i in collection.indices) {
  println("Element $i is ${collection[i]}")
}
```

`break` and `continue` are still around, and they behave the same as in Java.

[Back to `when`](/control-operators/when.md) | [Forward to ranges](/compiler-magic/ranges.md)