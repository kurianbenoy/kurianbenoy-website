---
layout: post
title: Exploring Swift programming lanugae
---

## Classes and objects

Use class followed by the classÅfs name to create a class. A property declaration in a class is written the same way as a constant or variable declaration, except that it is in the context of a class. Likewise, method and function declarations are written the same way.

```
7> class Shape{ 
8.     var ns = 0 
9.     func simple(n:String) -> String { 
10.         return "A shape with \(ns) sides named \(n)."
11.    
14> shape.ns = 7
15> var shapedesc = shape.simple(n:"Heptagon")
shapedesc: String = "A shape with 7 sides named Heptagon."
 16> print(shapedesc)
A shape with 7 sides named Heptagon.
```




Notice how self is used to distinguish the name property from the name argument to the initializer. The arguments to the initializer are passed like a function call when you create an instance of the class. Every property needs a value assignedÅ\either in its declaration (as with numberOfSides) or in the initializer (as with name).

Use deinit to create a deinitializer if you need to perform some cleanup before the object is deallocated.

Subclasses include their superclass name after their class name, separated by a colon. There is no requirement for classes to subclass any standard root class, so you can include or omit a superclass as needed.

Methods on a subclass that override the superclassÅfs implementation are marked with overrideÅ\overriding a method by accident, without override, is detected by the compiler as an error. The compiler also detects methods with override that donÅft actually override any method in the superclass.

```
29> class Square: NamedShape{ 
 30.     var sL: Double 
 31.     init(sL: Double, name: String) { 
 32.         self.sL = sL 
 33.         super.init(name:name) 
 34.         ns=4 
 35.     } 
 36.     func area() -> Double { 
 37.         return sL*sL 
 38.     } 
 39.      
 40.     override func simpledesc() -> String{ 
 41.         return "A square with side of length \(sL)." 
 42.     } 
 43. } 
 44>  


 45> let test = Square(sL:5.3, name:"my square")  
test: Square = {
  __lldb_expr_14.NamedShape = {                                                                         
    ns = 4                                                                                              
    name = "my square"                                                                                  
  }                                                                                                     
  sL = 5.2999999999999998                                                                               
}                                                                                                       
 46> test.area()
$R0: Double = 28.09
 47> test.simpledesc()
$R1: String = "A square with side of length 5.3."
```

In addition to simple properties that are stored, properties can have a getter and a setter.In the setter for perimeter, the new value has the implicit name newValue. You can provide an explicit name in parentheses after set.

```
48> class EquilateralTriangle: NamedShape { 
 49.     var sL: Double = 0.0 
 50.     init(sL: Double, name: String) { 
 51.         self.sL = sL 
 52.         super.init(name: name) 
 53.         ns = 3 
 54.     } 
 55.      
 56.     var perimeter: Double{ 
 57.         get{ 
 58.             return 3.0 * sL 
 59.         } 
 60.         set{ 
 61.             sL = newValue/3.0 
 62.         } 
 63.     } 
 64.      
 65.     override func simpledesc() -> String { 
 66.         return "An equilateral triangle with sides of length \(sL)." 
 67.     } 
 68. } 
 69>  
 70>  
 71> var tri = EquilateralTriangle(sL: 3.2, name:"tri")
tri: EquilateralTriangle = {
  __lldb_expr_14.NamedShape = {
    ns = 3
    name = "tri"
  }
  sL = 3.2000000000000002
}
 72> print(tri.perimeter)
9.600000000000001
 73> tri.perimeter=99.9
 74> print(tri.sL)
33.300000000000004
```

## Enumerations and Structures

160> enum Rank: Int{ 
 161.     case ace=1 
 162.     case two, three, four, five, six, seven, eight, nine, ten 
 163.     case jack, queen, king 
 164.      
 165.     func simple() -> String{ 
 166.         switch self{ 
 167.         case .ace: 
 168.             return "ace" 
 169.         case .jack: 
 170.             return "jack" 
 171.         case .queen: 
 172.             return "queen" 
 173.         case .king: 
 174.             return "king" 
 175.         default: 
 176.             return String(self.rawValue) 
 177.         } 
 178.     } 
 179. } 
 180> 
 181> let ace = Rank.ace
ace: Rank = ace
 182> let aceR = ace.rawValue
aceR: Int = 1


Use the init?(rawValue:) initializer to make an instance of an enumeration from a raw value. It returns either the enumeration case matching the raw value or nil if there is no matching Rank.

    if let convertedRank = Rank(rawValue: 3) {
        let threeDescription = convertedRank.simpleDescription()
    }

Use struct to create a structure. Structures support many of the same behaviors as classes, including methods and initializers. One of the most important differences between structures and classes is that structures are always copied when they are passed around in your code, but classes are passed by reference.

```
struct Card {
    var rank: Rank
    var suit: Suit
    func simpleDescription() -> String {
        return "The \(rank.simpleDescription()) of \(suit.simpleDescription())"
    }
}
```

## Protocols

Use protocol to declare a protocol.

```
    protocol ExampleProtocol {
        var simpleDescription: String { get }
        mutating func adjust()
    }
```

Classes, enums adopt protocols:

```
    class SimpleClass: ExampleProtocol {
        var simpleDescription: String = "A very simple class."
        var anotherProperty: Int = 69105
        func adjust() {
            simpleDescription += "  Now 100% adjusted."
        }
    }
    var a = SimpleClass()
    a.adjust()
    let aDescription = a.simpleDescription

    struct SimpleStructure: ExampleProtocol {
        var simpleDescription: String = "A simple structure"
        mutating func adjust() {
            simpleDescription += " (adjusted)"
        }
    }
    var b = SimpleStructure()
    b.adjust()
    let bDescription = b.simpleDescription

```

Notice the use of the mutating keyword in the declaration of SimpleStructure to mark a method that modifies the structure. The declaration of SimpleClass doesnÅft need any of its methods marked as mutating because methods on a class can always modify the class.

## Generics

Write a name inside angle brackets to make a generic function or type.

    func makeArray<Item>(repeating item: Item, numberOfTimes: Int) -> [Item] {
        var result = [Item]()
        for _ in 0..<numberOfTimes {
            result.append(item)
        }
        return result
    }
    makeArray(repeating: "knock", numberOfTimes: 4)

You can make generic forms of functions and methods, as well as classes, enumerations, and structures.

    // Reimplement the Swift standard library's optional type
    enum OptionalValue<Wrapped> {
        case none
        case some(Wrapped)
    }
    var possibleInteger: OptionalValue<Int> = .none
    possibleInteger = .some(100)

Use where right before the body to specify a list of requirementsÅ\for example, to require the type to implement a protocol, to require two types to be the same, or to require a class to have a particular superclass.

    func anyCommonElements<T: Sequence, U: Sequence>(_ lhs: T, _ rhs: U) -> Bool
        where T.Element: Equatable, T.Element == U.Element
    {
        for lhsItem in lhs {
            for rhsItem in rhs {
                if lhsItem == rhsItem {
                    return true
                }
            }
        }
        return false
    }
    anyCommonElements([1, 2, 3], [3])
