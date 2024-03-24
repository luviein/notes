# WeSplit App

## grouping texts

 ``` Swift
var body: some View {
        Form {
            Text("Hello!!")
            Section{
                Text("Section1")
                Text("Section2")
            }
        }
    }
```

## @State

```swift
struct ContentView: View {
    @State private var tapCount = 0

    var body: some View {
        Button("Tap Count: \(tapCount)") {
            self.tapCount += 1
        }
    }
}
```

- Use `@State` for state that:
    - Is specific to a `single view`.
    - Is mutable and needs to be modified within the view.
    - Does not need to be shared with other views or components.

## binding variables 

2 way binds name with $ to variable so swift and read and write to update

```swift
struct ContentView: View {
    @State private var name = ""

    var body: some View {
        Form {
            TextField("Enter your name", text: $name)
            Text("Hello, world!")
        }
    }
}
```

## for each loop
```swift
struct ContentView: View {
    let students = ["Harry", "Hermione", "Ron"]
    @State private var selectedStudent = "Harry"

    var body: some View {
        NavigationStack {
            Form {
                Picker("Select your student", selection: $selectedStudent) {
                    ForEach(students, id: \.self) {
                        Text($0)
                    }
                }
            }
        }
    }
}
```

- `ForEach(fruits, id: \ .self)`: This iterates over each element in the `fruits` array, and `\.self` is used to specify that each element should be used as its own identifier.

- `Text($0)`: This creates a `Text` view for each element in the `fruits` array, with `$0` representing each individual element. So, for example, if `fruits` contains ["Apple", "Banana", "Orange"], the `ForEach` loop will create three `Text` views: one with "Apple", one with "Banana", and one with "Orange".

## picker style

opens up select menu in a separate view
```swift
Picker("Number of people", selection: $numberOfPeople) {
    ForEach(2 ..< 100) {
        Text("\($0) people")
    }
}
.pickerStyle(.navigationLink)
```

## section title

creates a title for the section
```Swift
Section("How much do you want to tip"){}
```

![[Pasted image 20240324225118.png]]

## hiding keyboard
checks for format currency, giving a done button to hide keyboard
```Swift
    @FocusState private var focusAmount : Bool

    TextField("Amount", value: $checkAmount, format: .currency(code: Locale.current.currency?.identifier ?? "USD"))
		.keyboardType(.decimalPad)
		.focused($focusAmount)
// put it after whole form
 .toolbar{
	if focusAmount {
		Button ("Done"){
			focusAmount = false
			}
		}
	}
```
### notes
`cmd + option + p` : refreshes screen
`cmd + r` : runs virtual iphone simulator