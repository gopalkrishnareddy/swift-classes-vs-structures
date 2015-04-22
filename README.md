##Both classes and structures in Swift

####Define properties to store values

```swift
class ProfilePicture {
  var fileName: String
}
```
```swift
struct Resolution{
  var width = 0
  var height = 0
}
```

####Define methods to provide functionality

```swift
struct Frame{
  var originX = 0
  var originY = 0
  var width = 0
  var height = 0
  
  func centerX() -> Double {
    return Double(originX) + (Double(width))/2
  }
}
```

```swift
class Counter {
  var counter = 0
  
  func incrment() {
    counter++
  }
}
```
