# data types

##  arrays

creating arrays: (type specific)
```swift
var albums = [String]()
```

```swift
var scores: [Int] = [10, 12, 9]
```

## **array functions**

### count

```swift
print(albums.count)
```

### remove

```swift
var characters = ["Lana", "Pam", "Ray", "Sterling"]
print(characters.count)

characters.remove(at: 2)
print(characters.count)

characters.removeAll()
print(characters.count)
```

### contains

```swift
let bondMovies = ["Casino Royale", "Spectre", "No Time To Die"]
print(bondMovies.contains("Frozen"))
```

### sorted

```swift
print(cities.sorted())
```

### reversed

```swift
print(reversedPresidents)
```


## dictionaries

use default, if not type will be Optional
```swift
let olympics = [
    2012: "London",
    2016: "Rio de Janeiro",
    2021: "Tokyo"
]

print(olympics[2012, default: "Unknown"])
```

set dictionary with customised types 
```swift
var heights = [String: Int]()
heights["Yao Ming"] = 229
heights["Shaquille O'Neal"] = 216
heights["LeBron James"] = 206
```

==setting same key with different value overwrites old value==


## sets

creating sets

```swift
let people = Set(["Denzel Washington", "Tom Cruise", "Nicolas Cage", "Samuel L Jackson"])
```

```swift
var people = Set<String>()
people.insert("Denzel Washington")
people.insert("Tom Cruise")
people.insert("Nicolas Cage")
people.insert("Samuel L Jackson")
```


##  set functions
`.sorted()` , `.contains()` , `count`


## enums

```swift
enum Weekday {
    case monday, tuesday, wednesday, thursday, friday
}
```

```swift
var day = Weekday.monday
day = .tuesday
day = .friday
```
