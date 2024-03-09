# closures

allows us to modify example sorted function to specify conditions we want in the function

### trailing closure with shorthand syntax

```swift
let captainFirstTeam = team.sorted {
    if $0 == "Suzanne" {
        return true
    } else if $1 == "Suzanne" {
        return false
    }

    return $0 < $1
}
```

use shorthands when:
`when there are less parameters`
`if functions are commonly used to people easily understand them`
`dont really refer to them alot, if not just give it a name`


### accepting functions in parameters

```swift
func doImportantWork(first: () -> Void, second: () -> Void, third: () -> Void) {
    print("About to start first work")
    first()
    print("About to start second work")
    second()
    print("About to start third work")
    third()
    print("Done!")
}
```

```swift
doImportantWork {
    print("This is the first work")
} second: {
    print("This is the second work")
} third: {
    print("This is the third work")
}
```

return value of the functions must be the same in the second window. EG: if first() returns String, then in second window should do a return string.
