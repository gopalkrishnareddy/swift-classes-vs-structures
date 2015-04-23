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

####Define subscripts to provide access to their values using subscript syntax

```swift
class WeekClass {
    
    let week = ["Sunday","Monday","Tuesday","Wednesday","Thursday","Friday","Saturday"]
    
    subscript(day: Int) -> String {
        return week[day]
    }
    
    subscript(day: String) -> Int {
        return find(week, day)!
    }
}

struct WeekStruct {
    
    //US consider Sunday as first day of the week
    let week = ["Sunday","Monday","Tuesday","Wednesday","Thursday","Friday","Saturday"]
    
    subscript(day: Int) -> String {
        return week[day]
    }
    
    subscript(day: String) -> Int {
        return find(week, day)!
    }
}

var weekClassInstance = WeekClass()
weekClassInstance["Monday"] //1 (Index of Monday on the week)
weekClassInstance[1] //"Monday"

var weekStructInstance = WeekStruct()
weekStructInstance["Sunday"] //0
weekStructInstance[0] //"Sunday"
```

####Define initializers to set up their initial state

```swift
struct Matrix {
    let rows: Int, columns: Int
    init(rows: Int,columns:Int){
        //Initialize
        self.rows = rows
        self.columns = columns
    }
}

var mat = Matrix(rows: Int, columns: Int)
//Structures have an automatically-generated memberwise initializer. So the initializer is optional here

class User {
  init(firstName: String, lastName: String){
    //Initialize
  }
}

```

