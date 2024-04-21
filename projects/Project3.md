## view composition

grouping common styles together

```swift
struct CapsuleText: View {
    var text: String

    var body: some View {
        Text(text)
            .font(.largeTitle)
            .padding()
            .foregroundStyle(.white)
            .background(.blue)
            .clipShape(.capsule)
    }
}
```

```swift
struct ContentView: View {
    var body: some View {
        VStack(spacing: 10) {
            CapsuleText(text: "First")
	            .foregroundStyle(.white)
            CapsuleText(text: "Second")
        }
    }
}
```

## view modifier

reusable component or a piece of code that can be used to modify the appearance or behavior of views. Essentially, it lets you encapsulate stylistic and behavioral changes in one place and then apply them to any view as needed. This helps keep your SwiftUI code clean, modular, and DRY (Don't Repeat Yourself).

### How ViewModifiers Work

A `ViewModifier` works by implementing its `body` method, which transforms an input view into an output view, usually by adding additional visual characteristics or behaviors. These modifications could include setting fonts, colors, frame sizes, padding, or even more complex behaviors like animations.

```swift
struct Title: ViewModifier {
    func body(content: Content) -> some View {
        content
            .font(.largeTitle)
            .foregroundStyle(.white)
            .padding()
            .background(.blue)
            .clipShape(.rect(cornerRadius: 10))
    }
}
```

can have multiple functions in extension View
```swift
struct Watermark: ViewModifier {
    var text: String

    func body(content: Content) -> some View {
        ZStack(alignment: .bottomTrailing) {
            content
            Text(text)
                .font(.caption)
                .foregroundStyle(.white)
                .padding(5)
                .background(.black)
        }
    }
}

extension View {
    func watermarked(with text: String) -> some View {
        modifier(Watermark(text: text))
    }
}
```
