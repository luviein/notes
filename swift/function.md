# function

```swift
func printTimesTables(number: Int, end: Int) {
    for i in 1...end {
        print("\(i) x \(number) is \(i * number)")
    }
}

printTimesTables(number: 5, end: 20)
```

```swift
func driveRace(laps: String) {
	for i in 1...laps {
		print("Another lap!")
	}
}
driveRace(laps: 100)
```

## remove external parameter

using underscore
The main reason for skipping a parameter name is when your function name is a verb and the first parameter is a noun the verb is acting on.
```swift
func isUppercase(_ string: String) -> Bool {
    string == string.uppercased()
}

let string = "HELLO, WORLD"
let result = isUppercase(string)
```

using another name to make parameter more readable
``` swift
func printTimesTables(multiplier number: Int) { for i in 1...12 print("\(i) x \(number) is \(i * number)") } } printTimesTables(multiplier: 5)
}
```

# return function
```swift
func sameLetter(first: String , second: String) -> Bool {

    return first.sorted() == second.sorted()

}

print(sameLetter(first: "abc", second: "cab"))
```

can dont write return if its a single operation (eg: ternary / single line). if using if statements etc need write return

need return
```swift
func greet(name: String) -> String {
    if name == "Taylor Swift" {
        return "Oh wow!"
    } else {
        return "Hello, \(name)"
    }
}
```

no need return 
```swift
func greet(name: String) -> String {
    name == "Taylor Swift" ? "Oh wow!" : "Hello, \(name)"
}
```


# tuples

```swift
func getUser() -> (firstName: String, lastName: String) {
    (firstName: "Taylor", lastName: "Swift")
}

let user = getUser()
print("Name: \(user.firstName) \(user.lastName)")
```

Tuples are convenient for situations where you want a quick and simple way to bundle related pieces of data, especially when the structure is temporary or doesn't need additional behaviour.

### shorthand setting tuple results into variables
```swift
func getUser() -> (firstName: String, lastName: String) {
    (firstName: "Taylor", lastName: "Swift")
}
```
```swift

let (firstName, lastName) = getUser()
print("Name: \(firstName) \(lastName)")
```
