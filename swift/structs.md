# structs

similar to model in Java

```swift
struct Employee {
    let name: String = "Anonymous" // becomes default
    var vacationRemaining: Int

    mutating func takeVacation(days: Int) {
        if vacationRemaining > days {
            vacationRemaining -= days
            print("I'm going on vacation!")
            print("Days remaining: \(vacationRemaining)")
        } else {
            print("Oops! There aren't enough days remaining.")
        }
    }
}
```

cannot change value of constants (let), only can change var with `mutating` keyword to edit the properties in function


## getters and setters

```swift
struct Employee {
    let name: String
    var vacationAllocated = 14
    var vacationTaken = 0

    var vacationRemaining: Int {
        vacationAllocated - vacationTaken
    }
}
```

```swift
var vacationRemaining: Int {
    get {
        vacationAllocated - vacationTaken
    }

    set {
        vacationAllocated = vacationTaken + newValue
    }
}
```

```swift
var archer = Employee(name: "Sterling Archer", vacationAllocated: 14)
archer.vacationTaken += 4
archer.vacationRemaining = 5
print(archer.vacationAllocated)
```

swift automatically sets new value as the one we are setting 

if you regularly read the property when its value hasn’t changed, then using a stored property will be much faster than using a computed property. On the other hand, if your property is read very rarely and perhaps not at all, then using a computed property saves you from having to calculate its value and store it somewhere.

``` swift
struct Dog {
    var breed: String
    var cuteness: Int

    var rating: String {
        switch cuteness {
        case ..<3:
            return "That's a cute dog!"
        case ..<7:
            return "That's a really cute dog!"
        default:
            return "That's a super cute dog!"
        }
    }
}

let luna = Dog(breed: "Samoyed", cuteness: 11)
let message = luna.rating
print(message)

```

## didset & willset

- `willSet` is called just before the value of the property is set.
- It provides a chance to take action before the new value is assigned to the property.
- The new value is available as the constant parameter name `newValue`.

- `didSet` is called immediately after the value of the property is set.
- It allows you to react to the change after it has occurred.
- The old value is available as the constant parameter name `oldValue`.

The most important reason is _convenience_: using a property observer means your functionality will be executed whenever the property changes.

```swift
struct App {
    var contacts = [String]() {
        willSet {
            print("Current value is: \(contacts)")
            print("New value will be: \(newValue)")
        }

        didSet {
            print("There are now \(contacts.count) contacts.")
            print("Old value was \(oldValue)")
        }
    }
}

var app = App()
app.contacts.append("Adrian E")
app.contacts.append("Allen W")
app.contacts.append("Ish S")
```


## custom initialiser

```swift
struct Player {
    let name: String
    let number: Int

    init(name: String) {
        self.name = name
        number = Int.random(in: 1...99)
    }
}

let player = Player(name: "Megan R")
print(player.number)
```

self = this in java

