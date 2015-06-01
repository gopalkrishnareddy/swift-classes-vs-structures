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
####Be extended to expand their functionality beyond a default implementation

```swift
struct Rectangle {
    var originX = 0.0, originY = 0.0
    var width = 0.0, height = 0.0
    
    init(originX: Double,originY: Double,width: Double, height:Double){
        self.originX = originX
        self.originY = originY
        self.width = width
        self.height = height
    }
}

//This extension add functionality to exsisting struct
extension Rectangle{
    func area() -> Double{
        return self.width * self.height
    }
}
```
```swift
class Dice {
    
    let sides:UInt32
    
    init(sides: UInt32){
        self.sides = sides
    }
    
    func roll() -> UInt32{
       return arc4random_uniform(self.sides) + 1
    }
}

var dice = Dice(sides: 6)
dice.roll()

extension Dice{

    //Note about module bias. For random number generation you should use arc4random_uniform over arc4random % upper_bound to avoid modulo bias
    //http://stackoverflow.com/questions/17640624/arc4random-modulu-biased
    func rollWithModuloBias() -> UInt32{
        return arc4random() % self.sides
    }
}
dice.rollWithModuloBias()

```
####Conform to protocols to provide standard functionality of a certain kind

```swift
protocol Descriptable{
    func describe() -> String
}

struct Rectangle : DebugPrintable {
    
    var originX = 0.0, originY = 0.0
    var width = 0.0, height = 0.0
    
    init(originX: Double,originY: Double,width: Double, height:Double){
        self.originX = originX
        self.originY = originY
        self.width = width
        self.height = height
    }
    
    func describe() -> String{
        return "Rectangle with origin (\(originX),\(originY)) and width = \(width) , height = \(height)"
    }
    
}
```

```swift
class Dice : Descriptable{
    
    let sides:UInt32
    
    init(sides: UInt32){
        self.sides = sides
    }
    
    func roll() -> UInt32{
       return arc4random_uniform(self.sides) + 1
    }
    
    func describe() -> String {
        return "A Dice with \(sides) sides"
    }
}
```
