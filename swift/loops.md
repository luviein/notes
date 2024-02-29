# loops

## for loop in range
```swift
for i in 1...5 {
    print("Counting from 1 through 5: \(i)")
}

print()

for i in 1..<5 {
    print("Counting 1 up to 5: \(i)")
}
```

## enhanced for loop
```swift
for name in platforms {
    print("Swift works great on \(name).")
}
```

## ignoring loop variable
```swift
var lyric = "Haters gonna"

for _ in 1...5 {
    lyric += " hate"
}

print(lyric)
```

Using the underscore in this context is a convention to signal that the loop variable is intentionally ignored and not needed within the loop block. It can improve code readability and let other developers know that the loop variable is not used, preventing unnecessary compiler warnings about unused variables.