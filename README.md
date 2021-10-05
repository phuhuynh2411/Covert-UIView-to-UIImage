# Covert-UIView-to-UIImage

When you work on a live stream or video call app, you might need to convert a UIView to UImage to do some kinds of face recognition or nudity detection.

The process is quite simple. We only need a few lines of code.

```swift
let renderer = UIGraphicsImageRenderer(size: view.bounds.size)
let image = renderer.image { context in
    view.drawHierarchy(in: view.bounds, afterScreenUpdates: true)
}
```

The 'view' would be in the view hierarchy that is used to display the video call or live stream.


But one thing to keep in mind is that the above code must run on the main thread (UI thread); otherwise, you would get an empty image.
```swift
DispatchQueue.main.async {
    // get the uiimage here
}
```
