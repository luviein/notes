# Protocol

Protocols define a common set of methods and properties. Check if a type conforms to a protocol. Protocols can provide default method implementations.

All must conform to protocol structure
```swift
protocol Purchaseable {
    var name: String { get set }
}
```
```swift
struct Book: Purchaseable {
    var name: String
    var author: String
}

struct Movie: Purchaseable {
    var name: String
    var actors: [String]
}

struct Car: Purchaseable {
    var name: String
    var manufacturer: String
}

struct Coffee: Purchaseable {
    var name: String
    var strength: Int
}
```
```swift
func buy(_ item: Purchaseable) {
    print("I'm buying \(item.name)")
}
```

can do item.name as Swift ensures that item follows protocol 

## opaque return types
used with `some` keyword
```swift
func getRandomNumber() -> some Equatable {
    Int.random(in: 1...6)
}

func getRandomBool() -> some Equatable {
    Bool.random()
}
```
Returning an opaque return type means we still get to focus on the functionality we want to return rather than the specific type, which in turn allows us to change our mind in the future without breaking the rest of our code.


## extensions

to have both custom and default initialiser, put custom one in extension
```swift
struct Book {
    let title: String
    let pageCount: Int
    let readingHours: Int
}
```
```swift
extension Book {
    init(title: String, pageCount: Int) {
        self.title = title
        self.pageCount = pageCount
        self.readingHours = pageCount / 50
    }
}
```

The `.whitespacesAndNewlines` value comes from Apple’s Foundation API, and actually so does `trimmingCharacters(in:)`

```swift
extension String {
    func trimmed() -> String {
        self.trimmingCharacters(in: .whitespacesAndNewlines)
    }
}
```

needs to me mutating as it is altering existing string
```swift
extension String { 
	mutating func append(_ other: String) { 
	self += other 
	} 
	}
```

## protocol extension

```swift
protocol Person {
    var name: String { get }
    func sayHello()
}
```
```swift
extension Person {
    func sayHello() {
        print("Hi, I'm \(name)")
    }
}
```

to change a property with get set

```swift
**protocol** Building {

    **var** roomNum : Int {**get**}

    **var** cost : Int {**get** **set**}

    **var** agent : String {**get**}

}


```

example of house struct: house.cost = 2000