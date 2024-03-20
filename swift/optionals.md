# optionals

## if let 
must unwrap in order to use it

```swift
var username: String? = nil

if let unwrappedName = username {
    print("We got a user: \(unwrappedName)")
} else {
    print("The optional was empty.")
}
```

## guard let
if it doesnt reach else statement = unwrapped
use if want to handle failure early

```swift
func printSquare(of number: Int?) {
    guard let number = number else {
        print("Missing input")

        // 1: We *must* exit the function here
        return
    }

    // 2: `number` is still available outside of `guard`
    print("\(number) x \(number) is \(number * number)")
}
```

typically used in a function
```swift
func plantTree(_ type: String?) {
	guard type else {
		return
	}
	print("Planting a \(type).")
}
plantTree("willow")
```

## nil coalescing - ??

if random element fails , returns none
after ?? must be the same type as the unwrapped value
```swift
let tvShows = ["Archer", "Babylon 5", "Ted Lasso"]
let favorite = tvShows.randomElement() ?? "None"
```

```swift
struct Book {
    let title: String
    let author: String?
}

let book = Book(title: "Beowulf", author: nil)
let author = book.author ?? "Anonymous"
print(author)
```

```swift
let input = ""
let number = Int(input) ?? 0
print(number)
```

0 is valid as 0 is a `integer literal`. swift auto converts literals to other appropriate numeric types.
```swift
let distanceRan: Double? = 0.5
let distance: Double = distanceRan ?? 0
```

## optional chaining

can only use book? when inside there is an optional property

```swift
struct Book {
    let title: String
    let author: String?
}

var book: Book? = nil
let author = book?.author?.first?.uppercased() ?? "A"
print(author)
```

first (used in collections) returns an optional, even though shoppingList is not an optional, first can return optional
```swift
let shoppingList = ["eggs", "tomatoes", "grapes"]
let firstItem = shoppingList.first?.appending(" are on my shopping list")
```

dictionaries return optional without needing to declare
```swift
let favoriteColors = ["Paul": "Red", "Charlotte": "Pink"]
let charlotteColor = favoriteColors["Charlotte"]?.lowercased()
```

## using try ?
using try ? returns function value as an optional
unwrap optional from try?, if fail, it will throw network failed error
```swift
enum UserError: Error {
    case badID, networkFailed
}

func getUser(id: Int) throws -> String {
    throw UserError.networkFailed
}

if let user = try? getUser(id: 23) {
    print("User: \(user)")
}
```