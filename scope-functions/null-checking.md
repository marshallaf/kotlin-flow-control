# Nullability and scope functions
Scope functions can be used alongside the null safe functionality of Kotlin.

Instead of this in Java:
```java
if (textView != null) {
  textView.setText("You have 1 alert.");
  textView.setVisibility(View.VISIBLE);
  textView.performLongClick();
}
```

You can do this in Kotlin:
```kotlin
textView?.apply {
  text = "You have 1 alert.";
  visibility = View.VISIBLE;
  performLongClick();
}
```
Since we've used a safe call to access `textView` here, if `textView` is null, the lambda passed to `.run()` just doesn't happen.

Another way this is useful is for null-safe transformations:
```kotlin
val distance = distanceString?.run { toDouble() } ?: 0.0
```
Here, if `distanceString` is null, `.run()` is not invoked. Execution is passed to the right side of the elvis operator, assigning the default value of `0.0` to `distance`. 

[Back to it-type scope functions](/scope-functions/it-type.md)
