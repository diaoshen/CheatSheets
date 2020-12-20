# Swift

## Table of Contents

#

-   Basic

    -   [Variables & Constants](#Constants-and-Variables)
        -   [Computed Vars](#Computed-vars)
    -   [Useful Types](#Useful-Types)
    -   [Value Typed vs Reference Typed](#Value-Typed-vs-Reference-Typed)
    -   [Numeric Literal](#Numeric-Literal)
    -   [Limits](#Limits)
    -   [Conversion](#Conversion)
    -   [Type Aliases](#Type-Aliases)
    -   [Semicolons](#Semicolons)

-   Operators

    -   [Closed Range Operator](<#Closed-Range-Operator-[a,b]-(...)>)
    -   [Half-Open Range Operator](#Half-Open-Range-Operator-[a,b)
    -   [One-Sided Ranges](#One-Sided-Ranges)
    -   [Nil-Coalescing Operator](#Nil-Coalescing-Operator)

-   [Enum](#Enum)
-   Optional

    -   [What is Optional](#Optional)
    -   [Nil](#nil)
    -   [Unwrap Optional](#Unwrap-Optional)
    -   [Unwrap Optional Implicitly](#Implicitly-Unwrapped-Optionals)
    -   [Option Binding - Alternative to Unwrap Optional](#Optional-binding)

-   Collections

    -   [String](#String)
    -   [Tuples](#Tuples)
    -   [Array](#Arrays)
    -   [Set](#Set)
    -   [Dictionary](#Dictionary)

-   Iterating

    -   [Iterate](#Iterate)
    -   [ForEach](#ForEach)
    -   [TODO: use of \_ in loops](#)
    -   [TODO: Identifiable , Iterable? ](#)

-   Control Flow

    -   [For Loop](#For-Loops)
    -   [While Loop & Do-While](#While-Loops-&-Do-While)
    -   [Switch](#Switch)
        -   [Case Interval](#case:Interval)
        -   [Case Tuples](#case:Tuples)
        -   [Case Value Binding & Where](#Value-Binding)

-   Exceptions

    -   [Assertions & Precondition & Guard Statement](#Assertions-&-Precondition-&-Guard-Statement)

-   Function

    -   [Basic Function Declaration](#Functions)
    -   [Function as Types](#Function-Types)
    -   [Closure](<#Closure(inline-function)-(similar-to-lamda-in-C++-)>)

-   Struct & Class

    -   [Struct](#Structure-&-Classes)
    -   [Class](#Structure-&-Classes)

-   [Inheritance](#Inheritance)

-   [Protocol](#Protocol)
-   [Extension](#Extension)

#### Constants and Variables

```
Constant
let myConstant = 10
let c1 = 2 , c2 = 4 , c3 = 7
let π = 3.14159
let 你好 = "你好世界"
let 🐶🐮 = "dogcow"

Variable
var foo = 5
var x = 1 , y = 2 , z = 3
```

#### Computed vars

```
value of a computed var are computed when the var is being asked
var body: some View {
    return Text("Hello World")
}
```

#### Useful Types

```
UInt8 , 16 , 32 , 64
Int8  , 16 , 32 , 64
Int will be Int32 on a 32-bit platform , 64 on a 64-bit platform , same with UInt
Double (64bit floating-point number)
Float  (32bit floating-point number)
Bool
Character
String
Function
Optional
```

#### Value Typed vs Reference Typed

```
Value typed is when stuff gets copied when passed around
Reference typed is when stuff lives in a heap, only pointers get passed around

Stuff that's Value Typed :
    Struct
    Primitive Types like Int,Double
    Collections like Array,Set,Dictionary

Stuff that's Reference Typed :
    Class
```

#### Numeric Literals

```
Binary, with a 0b prefix
Octal , with a 0o prefix
Hex   , with a 0x prefix

Example : integer literals have a decimal value of 17 will be
let binaryInteger = 0b10001
let octalInteger = 0o21
let hexInteger = 0x11
```

#### Limits

```
let minValue = UInt8.min
let maxValue = UInt8.max
```

#### Conversion

```
// UInt16 can't add with Uint8 so use the syntax :   SomeType(initialValue) to convert UInt8 -> UInt16
let twoThousand: UInt16 = 2_000
let one: UInt8 = 1
let twoThousandAndOne = twoThousand + UInt16(one)
```

#### Type Aliases

```
typealias AudioSample = UInt16
var maxAmplitudeFound = AudioSample.min
// maxAmplitudeFound is now 0
```

#### Semicolons

```
used to write multiple statement on a single line
let cat = "🐱"; print(cat)
// Prints "🐱"
```

# Operators

#### Closed Range Operator [a,b] (...)

```
for index in 1...5 {
    print("\(index) times 5 is \(index * 5)")
}
// 1 times 5 is 5
// 2 times 5 is 10
// 3 times 5 is 15
// 4 times 5 is 20
// 5 times 5 is 25
```

#### Half-Open Range Operator [a,b) (..<)

```
let names = ["Anna", "Alex", "Brian", "Jack"]
let count = names.count
for i in 0..<count {
    print("Person \(i + 1) is called \(names[i])")
}
// Person 1 is called Anna
// Person 2 is called Alex
// Person 3 is called Brian
// Person 4 is called Jack
```

#### One-Sided Ranges

```
let names = ["Anna", "Alex", "Brian", "Jack"]
for name in names[2...] {
    print(name)
}
// Brian
// Jack

for name in names[...2] {
    print(name)
}
// Anna
// Alex
// Brian

for name in names[..<2] {
    print(name)
}
// Anna
// Alex


let range = ...5
range.contains(7)   // false
range.contains(4)   // true
range.contains(-1)  // true
```

#### Nil-Coalescing Operator

```
Basically shorthand for
a != nil ? a! : b
```

```
let defaultColorName = "red"
var userDefinedColorName: String?   // defaults to nil

var colorNameToUse = userDefinedColorName ?? defaultColorName
// userDefinedColorName is nil, so colorNameToUse is set to the default of "red"
```

# Enum

```
TODO
```

# Optional

```
Optional is used to cope with absence of a value
An optional represents two possibilities: Either there is a value, and you can unwrap the optional to access that value, or there isn’t a value at all.
```

```
let possibleNumber = "123"
let convertedNumber = Int(possibleNumber)
// convertedNumber is inferred to be of type "Int?", or "optional Int"
```

-   ### nil

```
You set an optional variable to a valueless state by assigning it the special value nil:

var serverResponseCode: Int? = 404
// serverResponseCode contains an actual Int value of 404
serverResponseCode = nil
// serverResponseCode now contains no value

var surveyAnswer: String?
// surveyAnswer is automatically set to nil
```

-   ### Unwrap Optional

```
// Unwrapping using "!"
if convertedNumber != nil {
    print("convertedNumber has an integer value of \(convertedNumber!).")
}
// Prints "convertedNumber has an integer value of 123."
```

-   ### Implicitly Unwrapped Optionals

```
let possibleString: String? = "An optional string."
let forcedString: String = possibleString! // requires an exclamation point

let assumedString: String! = "An implicitly unwrapped optional string."
let implicitString: String = assumedString // no need for an exclamation point
```

-   ### Optional binding

```
an alternaive to unwrapping

if let actualNumber = Int(possibleNumber) {
    print("The string \"\(possibleNumber)\" has an integer value of \(actualNumber)")
} else {
    print("The string \"\(possibleNumber)\" could not be converted to an integer")
}
// Prints "The string "123" has an integer value of 123"

Multiple optional binding
if let firstNumber = Int("4"), let secondNumber = Int("42"), firstNumber < secondNumber && secondNumber < 100 {
    print("\(firstNumber) < \(secondNumber) < 100")
}
```

# String

```
var emptyString = ""
var anotherEmptyString = String()
var catString = String(["C", "a", "t", "!", "🐱"])
.isEmpty()
.append()
.count
.startIndex
.endIndex
.index( params )
.insert( params )
.remove( params )
.hasPrefix("foo")
.hasSuffix("foo")
```

```
// SubString
let greeting = "Hello, world!"
let index = greeting.firstIndex(of: ",") ?? greeting.endIndex
let beginning = greeting[..<index]
// beginning is "Hello"

// Convert the result to a String for long-term storage.
let newString = String(beginning)
```

```
let greeting = "Guten Tag!"
greeting[greeting.startIndex]
// G
greeting[greeting.index(before: greeting.endIndex)]
// !
greeting[greeting.index(after: greeting.startIndex)]
// u
let index = greeting.index(greeting.startIndex, offsetBy: 7)
greeting[index]
// a
```

```
for index in greeting.indices {
    print("\(greeting[index]) ", terminator: "")
}
// Prints "G u t e n   T a g ! "
```

# Tuples

```
Syntax :   let foo = (Item1,Item2,Item3...)
```

```
Declare Option 1 :
let http404Error = (404, "Not Found")
// http404Error is of type (Int, String), and equals (404, "Not Found")

To Retrieve  :
let (statusCode, statusMessage) = http404Error
let (justTheStatusCode, _) = http404Error
let statusCode = http404Error.0
let statusMessage = http404Error.1
```

```
Declare Option 2 :
let http200Status = (statusCode: 200, description: "OK")

To Retrieve :
print("The status code is \(http200Status.statusCode)")
print("The status message is \(http200Status.description)")

```

# Arrays

```
var intArray = Array<Int>()
var intArray = [Int]()
var intArray : [Int] = []
var threeDoubles = Array(repeating: 0.0, count 3)
var threeInts = [Int](repeating: 5, count 3)

myArray[4..6] = ["foo","bar"]
newArray = [1,2,3] + [4,5,6]
newArray += [7,8,9]
.count
isEmpty()
.append()
.insert("foo", at: index)
.remove(at: index)
.removeLast()

```

# Set

```
var letters = Set<Character>()
var movies: Set<String> = ["Foo","Bar"]
var movies: Set = ["Foo","Bar"]

.count
.isEmpty
.insert("a")
.remove(item)
.contains(item)

```

-   Set Operation

```
Use the intersection(_:) method to create a new set with only the values common to both sets.
Use the symmetricDifference(_:) method to create a new set with values in either set, but not both.
Use the union(_:) method to create a new set with all of the values in both sets.
Use the subtracting(_:) method to create a new set with values not in the specified set.

let oddDigits: Set = [1, 3, 5, 7, 9]
let evenDigits: Set = [0, 2, 4, 6, 8]
let singleDigitPrimeNumbers: Set = [2, 3, 5, 7]

oddDigits.union(evenDigits).sorted()
// [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
oddDigits.intersection(evenDigits).sorted()
// []
oddDigits.subtracting(singleDigitPrimeNumbers).sorted()
// [1, 9]
oddDigits.symmetricDifference(singleDigitPrimeNumbers).sorted()
// [1, 2, 9]
```

-   Set Membership and Equality

```
Use the “is equal” operator (==) to determine whether two sets contain all of the same values.
Use the isSubset(of:) method to determine whether all of the values of a set are contained in the specified set.
Use the isSuperset(of:) method to determine whether a set contains all of the values in a specified set.
Use the isStrictSubset(of:) or isStrictSuperset(of:) methods to determine whether a set is a subset or superset, but not equal to, a specified set.
Use the isDisjoint(with:) method to determine whether two sets have no values in common.
let houseAnimals: Set = ["🐶", "🐱"]
let farmAnimals: Set = ["🐮", "🐔", "🐑", "🐶", "🐱"]
let cityAnimals: Set = ["🐦", "🐭"]

houseAnimals.isSubset(of: farmAnimals)
// true
farmAnimals.isSuperset(of: houseAnimals)
// true
farmAnimals.isDisjoint(with: cityAnimals)
// true
```

# Dictionary

```
var myDict = [Int: String]()
var airports: [String: String] = ["YYZ": "Toronto Pearson", "DUB": "Dublin"]
var airports = ["YYZ": "Toronto Pearson", "DUB": "Dublin"]

airports["LHR"] = "London Heathrow" // Creates new item if doesn't exist
.count
.isEmpty
.updateValue(newValue", forKey: key) // returns nil if value dont exist for key
.removeValue(forKey: key)
myDict["keyToRemove"] = nil
```

```
if let oldValue = airports.updateValue("Dublin Airport", forKey: "DUB") {
    print("The old value for DUB was \(oldValue).")
}
// Prints "The old value for DUB was Dublin."

OR

if let airportName = airports["DUB"] {
    print("The name of the airport is \(airportName).")
} else {
    print("That airport is not in the airports dictionary.")
}

// Remove value by KEY
if let removedValue = airports.removeValue(forKey: "DUB") {
    print("The removed airport's name is \(removedValue).")
} else {
    print("The airports dictionary does not contain a value for DUB.")
}
// Prints "The removed airport's name is Dublin Airport."
```

# Iterate

```
// String
for character in "Dog!🐶" {
    print(character)
}
for index in myString.indices {
    print("\(myString[index]) ", terminator: "")
}

// Array
for item in shoppingList {
    print(item)
}
for(index, value) in shoppingList.enumerated() {
    print("Item \(index+1): \(value)")
}

// Set
for ch in letters {
    print("\(genre)")
}
for ch in letters.sorted() {
    print("\(genre)")
}

// Dictionary
for (airportCode, airportName) in airports {
    print(airportCode + " -> " + airportName)
}
for key in myDict.keys {
    print(key)
}
for val in myDict.values {
    print(val)
}
for key in myDict.keys.sorted() {
    print(key)
}
```

### ForEach

```
ForEach takes some iterable range and content to iterate over

let numberWords = ["one", "two", "three"]
numberWords.
numberWords.forEach { word in
    print(word)
}

// Prints "one"
// Prints "two"
// Prints "three"
```

# Control Flow

## For Loops

```
// Ignore index
let base = 3
let power = 10
var answer = 1
for _ in 1...power {
    answer *= base
}
print("\(base) to the power of \(power) is \(answer)")
// Prints "3 to the power of 10 is 59049"
```

```
let minutes = 60
for tickMark in 0..<minutes {
    // render the tick mark each minute (60 times) 0 to 59
}
```

-   stride(from:to:by) same as ..<

```
let minuteInterval = 5
for tickMark in stride(from: 0, to: minutes, by: minuteInterval) {
    // render the tick mark every 5 minutes (0, 5, 10, 15 ... 45, 50, 55)
}
```

-   stride(from:through:by) same as ...

```
let hours = 12
let hourInterval = 3
for tickMark in stride(from: 3, through: hours, by: hourInterval) {
    // render the tick mark every 3 hours (3, 6, 9, 12)
}
```

## While Loops & Do-While

```
while condition {
    statements
}
```

```
repeat {
    statement
} while condition
```

## Switch

```
let anotherCharacter: Character = "a"
switch anotherCharacter {
case "a", "A":
    print("The letter A")
default:
    print("Not the letter A")
}
// Prints "The letter A"
```

-   ### case:Interval

```
let approximateCount = 62
let countedThings = "moons orbiting Saturn"
let naturalCount: String
switch approximateCount {
case 0:
    naturalCount = "no"
case 1..<5:
    naturalCount = "a few"
case 5..<12:
    naturalCount = "several"
case 12..<100:
    naturalCount = "dozens of"
case 100..<1000:
    naturalCount = "hundreds of"
default:
    naturalCount = "many"
}
print("There are \(naturalCount) \(countedThings).")
// Prints "There are dozens of moons orbiting Saturn."
```

-   ### case:Tuples

```
let somePoint = (1, 1)
switch somePoint {
case (0, 0):
    print("\(somePoint) is at the origin")
case (_, 0):
    print("\(somePoint) is on the x-axis")
case (0, _):
    print("\(somePoint) is on the y-axis")
case (-2...2, -2...2):
    print("\(somePoint) is inside the box")
default:
    print("\(somePoint) is outside of the box")
}
// Prints "(1, 1) is inside the box"
```

-   ### Value Binding

```
let anotherPoint = (2, 0)
switch anotherPoint {
case (let x, 0):
    print("on the x-axis with an x value of \(x)")
case (0, let y):
    print("on the y-axis with a y value of \(y)")
case let (x, y):
    print("somewhere else at (\(x), \(y))")
}
// Prints "on the x-axis with an x value of 2"
```

-   Where

```
let yetAnotherPoint = (1, -1)
switch yetAnotherPoint {
case let (x, y) where x == y:
    print("(\(x), \(y)) is on the line x == y")
case let (x, y) where x == -y:
    print("(\(x), \(y)) is on the line x == -y")
case let (x, y):
    print("(\(x), \(y)) is just some arbitrary point")
}
// Prints "(1, -1) is on the line x == -y"
```

# Assertions & Precondition & Guard Statement

```
The difference between assertions and preconditions is in when they’re checked: Assertions are checked only in debug builds, but preconditions are checked in both debug and production builds. In production builds, the condition inside an assertion isn’t evaluated. This means you can use as many assertions as you want during your development process, without impacting performance in production.
```

-   assert()

```
let age = -3
assert(age >= 0, "A person's age can't be less than zero.")
// This assertion fails because -3 is not >= 0.

// Can omit the message
assert(age >= 0)
```

-   assertionFailure

```
if age > 10 {
    print("You can ride the roller-coaster or the ferris wheel.")
} else if age >= 0 {
    print("You can ride the ferris wheel.")
} else {
    assertionFailure("A person's age can't be less than zero.")
}
```

-   precondition

```
// In the implementation of a subscript...
precondition(index > 0, "Index must be greater than zero.")
```

-   Guard Statement

```
func greet(person: [String: String]) {
    guard let name = person["name] else {
        return
    }
}
```

# Functions

```
Syntax of a function is like so :

func nameOfTheFunction(externalName InternalName : Type , [externalName2 InternalName2]...) -> ReturnType {
    //Body
}

externalName can be "_" which means you don't want any external name
```

```
func greet(person: String , dead: Bool = True) -> String {
    let greeting = "Hello, " + person + "!"
    return greeting
}
greet(person:"Bob")

// If label is omitted then calling function don't need to use "Person:"
func greet(_ person: String , dead: Bool = True) -> String {
    let greeting = "Hello, " + person + "!"
    return greeting
}
greet("Bob")

```

```
func minMax(array: [Int]) -> (min: Int, max: Int)? {
    if array.isEmpty { return nil }
    var currentMin = array[0]
    var currentMax = array[0]
    for value in array[1..<array.count] {
        if value < currentMin {
            currentMin = value
        } else if value > currentMax {
            currentMax = value
        }
    }
    return (currentMin, currentMax)
}
if let bounds = minMax(array: [8, -6, 2, 109, 3, 71]) {
    print("min is \(bounds.min) and max is \(bounds.max)")
}
// Prints "min is -6 and max is 109"
```

-   Function Argument Labels and Parameter Names

```
Each function parameter has both an argument label and a parameter name. The argument label is used when calling the function; each argument is written in the function call with its argument label before it. The parameter name is used in the implementation of the function. By default, parameters use their parameter name as their argument label.

Ex:

func foo(outerName innerName: String) {
    print(innerName)
}
foo(outerName: "Hello")
```

-   Nested Function

```
func chooseStepFunction(backward: Bool) -> (Int) -> Int {
    func stepForward(input: Int) -> Int { return input + 1 }
    func stepBackward(input: Int) -> Int { return input - 1 }
    return backward ? stepBackward : stepForward
}
var currentValue = -4
let moveNearerToZero = chooseStepFunction(backward: currentValue > 0)
// moveNearerToZero now refers to the nested stepForward() function
while currentValue != 0 {
    print("\(currentValue)... ")
    currentValue = moveNearerToZero(currentValue)
}
print("zero!")
// -4...
// -3...
// -2...
// -1...
// zero!
```

-   ### Function Types

```
similar to Function Pointers in C++)
var operation: (Double) -> Double
This is a var called operation
It is of type "function that takes a double and returns a double"
```

-   ### Closure(inline function) (similar to lamda in C++ )

```
alot of times , the function you want to pass , does not already exists
so forces you to write the definition..

Ex.
var operation: (Double) -> Double
operation = { (operand: Double) -> Double in return -operand}
basically the structure is like so..
operation = { (param1: Type) -> returnType in return funcDefinitions}

But Swift have inference so it can be shortcut even more to...

operation = { -$0 }
```

# Structure & Classes

```
    All vars in struct must be initialized.
    You can initialize inline :
    struct foo {
        var bar: Bool = false
    }
    OR during creation :
    foo(bar: false)

    Structs get free init() that initializes all vars that's why foo(bar: false) works without writing init()

    Mutability must be explicitly stated for structs that is if there is anything that does write then it needs to be marked with the keyword "mutating"
```

```
struct Resolution {
    var width = 0
    var height = 0
}
class VideoMode {
    var resolution = Resolution()
    var interlaced = false
    var frameRate = 0.0
    var name: String?
}

let someResolution = Resolution()
let someVideoMode = VideoMode()

OR

let vga = Resolution(width: 640, height: 480)
```

```
Structures Are Value Types meaning value is copied when its assigned to a var or passed to a function

Ex:
let hd = Resolution(width: 1920, height: 1080)
var cinema = hd // cinema is a different instance than hd

```

```
Classes Are Reference Types
```

```
struct Fahrenheit {
    var temperature: Double
    init() {
        temperature = 32.0
    }
}
var f = Fahrenheit()
print("The default temperature is \(f.temperature)° Fahrenheit")
// Prints "The default temperature is 32.0° Fahrenheit"
```

-   Property Observer , willSet , didSet

```
class StepCounter {
    var totalSteps: Int = 0 {
        willSet(newTotalSteps) {
            print("About to set totalSteps to \(newTotalSteps)")
        }
        didSet {
            if totalSteps > oldValue  {
                print("Added \(totalSteps - oldValue) steps")
            }
        }
    }
}
let stepCounter = StepCounter()
stepCounter.totalSteps = 200
// About to set totalSteps to 200
// Added 200 steps
stepCounter.totalSteps = 360
// About to set totalSteps to 360
// Added 160 steps
stepCounter.totalSteps = 896
// About to set totalSteps to 896
// Added 536 steps
```

# Inheritance

```
class SomeSubclass: SomeSuperclass {
    // subclass definition goes here
}

class SomeSubclass: SomeSuperclass {
    override func someFuncInSuperClass() {
        print("Choo Choo")
    }
}
```

# Protocol

-   View is Protocol
-   Adding protocol implementations

```
// Add a default implementation for protocol using extension
protocol Moveable {
    func move(by: Int)
    var hasMoved: Bool { get }
    var distanceFromStart: Int { get set }
}
extension Moveable {
    var hasMoved: Bool { return distanceFromStart > 0 }
}
```

# Extension

-   Adding code to a struct or class via an extension

```
struct Boat {
    // some code
}
extension Boat {
    func someNewFunction() { // Implementations... }
}
You can even make Boat become Moveable by doing this...
extension Boat : Moveable {
    // implement Moveable stuff here...
}
Now Boat is a Moveable thing
```

# Common Functions

#### Print(\_:separator:terminator:)

```
// print defaults to put line break
print(someValue)

// print without line break
print(someValue, terminator: "")

// print with string interpolation
// Prints "The current value of friendlyWelcome is Bonjour!"
print("The current value of friendlyWelcome is \(friendlyWelcome)")

```

# Exception

# Casting

-   Down casting

```
racecarVar becomes nil if fails
if let racecarVar = someCarVar as? Car {
    racecar.go()
}
```

# SwiftUI

## Common Views

### HStack

```

```

### ZStack

```
    ZStack {
        RoundedRectangle(cornerRadius: 10.0).fill(Color.White)
        RoundedRectangle(cornerRadius: 10.0).stroke(lineWidth: 3)
        Text("Blah")
    }
```

### VStack

```
    VStack {

    }
```

### ForEach to generate views

```
ForEach loops to return multiple view , can use a Hstack to stack the views returned by ForEach

Example: Make 5 Zstack and then HStack it

HStack {
    ForEach(0...4) { index in
        ZStack {
            RoundedRectangle(cornerRadius: 10.0).fill(Color.White)
            RoundedRectangle(cornerRadius: 10.0).stroke(lineWidth: 3)
            Text("Blah")
        }
    }
}
```

### View Functions

```
    Views have these functions available to apply
    Example :
    HStack(spacing: 0) {
        // Views..
    }
        .padding()
        .foregroundColor(Color.orange)
        .font(Font.largeTitle)
```
