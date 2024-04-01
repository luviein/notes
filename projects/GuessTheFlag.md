```swift
ZStack {
	// divides screen 50-50
    VStack(spacing: 0) {
        Color.red
        Color.blue
    }   
	// frosted glass look
    Text("Your content")
        .foregroundStyle(.secondary)
        .padding(50)
        .background(.ultraThinMaterial)
}
// ignores the safe areas on different iphone models
.ignoresSafeArea()
```

## gradients

Blends the top and bottom color
```swift
LinearGradient(stops: [
    .init(color: .white, location: 0.45),
    .init(color: .black, location: 0.55),
], startPoint: .top, endPoint: .bottom)
```

A ball like gradient
```swift
RadialGradient(colors: [.blue, .black], center: .center, startRadius: 20, endRadius: 200)
```

Elliptical gradient
```swift
AngularGradient(colors: [.red, .yellow, .green, .blue, .purple, .red], center: .center)
```

Adds a soft white gradient at the top
```swift
Text("Your content")
    .frame(maxWidth: .infinity, maxHeight: .infinity)
    .foregroundStyle(.white)
    .background(.red.gradient)
```

If want to reverse gradient can use LinearGradient
```swift
Text("Your content")

            .frame(maxWidth: .infinity, maxHeight: .infinity)

            .foregroundStyle(.white)

            .background(

                LinearGradient(gradient: Gradient(colors: [.red, .blue]), startPoint: .bottom, endPoint: .top)

            )
```

## buttons
```swift
Button {
    print("Edit button was tapped")
} label: {
    Label("Edit", systemImage: "pencil")
        .padding()
        .foregroundStyle(.white)
        .background(.red)
}
```
Label puts the icon and text side by side and is also customisable

can also put in button but wont be customisable
```swift
Button("Edit", systemImage: "pencil") {
    print("Edit button was tapped")
}
```

## alerts

Shows alert with title message and smaller message with delete and cancel buttons side by side
```swift
@State private var showingAlert = false
Button("Show Alert") {
    showingAlert = true
}
.alert("Important message", isPresented: $showingAlert) {
    Button("OK", role: .cancel) { }
} message: {
    Text("Please read this.")
}
```
