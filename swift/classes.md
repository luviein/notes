# classes

mutating keyword is not allowed in class
```swift
class SewingMachine {
	var itemsMade = 0
	// wrong
	mutating func makeBag(count: Int) {
		itemsMade += count
	}
}
var machine = SewingMachine()
machine.makeBag(count: 1)
```

able to change `light` even though `light` is a constant as onState is a variable 

```swift
class Light {
	var onState = false
	func toggle() {
		if onState {
			onState = false
		} else {
			onState = true
		}
		print("Click")
	}
}
let light = Light()
light.toggle()
```

## inheritance

```swift
class Employee {
    let hours: Int

    init(hours: Int) {
        self.hours = hours
    }
}
```

use override to replace the parent class function
```swift
class Developer: Employee {
    func work() {
        print("I'm writing code for \(hours) hours.")
    }
   
	override func printSummary() {
	    print("I'm a developer who will sometimes work \(hours) hours a day, but other times spend hours arguing about whether code should be indented using tabs or spaces.")
	}

}

 final class Manager: Employee {
    func work() {
        print("I'm going to meetings for \(hours) hours.")
    }
}
```
 if marked final means cannot use inheritance

## initialiser for class
```swift
class Vehicle {
    let isElectric: Bool

    init(isElectric: Bool) {
        self.isElectric = isElectric
    }
}
```
```swift
class Vehicle {
    let isElectric: Bool

    init(isElectric: Bool) {
        self.isElectric = isElectric
    }
}
```

must add variables from parent class in initialiser
```swift
class Car: Vehicle {
    let isConvertible: Bool

    init(isElectric: Bool, isConvertible: Bool) {
        self.isConvertible = isConvertible
        super.init(isElectric: isElectric)
    }
}
```

## copy class
```swift
class User {
    var username = "Anonymous"

    func copy() -> User {
        let user = User()
        user.username = username
        return user
    }
}
```

## deinit

```swift
class User {
    let id: Int

    init(id: Int) {
        self.id = id
        print("User \(id): I'm alive!")
    }

    deinit {
        print("User \(id): I'm dead!")
    }
}
```
```swift
var users = [User]()

for i in 1...3 {
    let user = User(id: i)
    print("User \(user.id): I'm in control!")
    users.append(user)
}

print("Loop is finished!")
users.removeAll()
print("Array is clear!")
```

when appending user into array, it hasnt deinit, only when removed from array then deinit