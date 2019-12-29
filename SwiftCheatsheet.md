# Marlon's Swift Cheatsheet

## Table Of Contents
- [Aesthetics](#aesthetics)
- Swift Basics
- TableViews
- Animations
- Custom Classes


## Aesthetics
### Curved Corners
There are two properties you can use here which are very nice.
One of the properties is `.cornerRadius` and it is a property of `CALayer`. You need to give it a `CGFloat` value.

#### Implementation:

Here's a regular ol' `UIView()` with rounded corners:

<script src="https://pastebin.com/embed_js/nxWzaR5i"></script>

```swift
// Assuming you're creating the view programmatically. If you're using an IBOutlet, just use the nameof your view or outlet property.

let containerView = UIView(frame: CGRect(x: 0, y:0, height: 100, width: 100))
containerView.backgroundColor = .systemGreen
containerView.layer.cornerRadius = 10.0 // You can also just use 10.
```


```swift
let button = UIButton()
button.backgroundColor = .systemIndigo
button.tintColor = .Label
button.layer.cornerRadius = 10
```

What I like to do if I need to give rounded corners to multiple views with the same `cornerRadius`, I will do this:
```swift
[containerView, button].forEach { $0.layer.cornerRadius = 10 }
```
That's much better than tediously writing the same code for every button.

If you want a capsule look for your button, the best way to do this is as follows:
_Quick note: You don't want to hard code these numbers for a capsule shape because if you ever needed to change the size of your button for example, then it can get messy. Typically, if you're making a capsule the corner radius value would have to be the view's height / 2. If you're changing your height in storyboards, then you'd have to sift through your code as well and change the corner radius there to. I'll show you what I mean._

Try to stay away from this:
```swift
// Say in the storyboard you made your button have a height of 40. To get the capsule look, you can set 20 (CGFloat) to the cornerRadius of the view.

let button = UIButton()
button.backgroundColor = .systemIndigo
button.tintColor = .Label
button.layer.cornerRadius = 20
```

Instead, do this:
```swift
let button = UIButton()
button.backgroundColor = .systemIndigo
button.tintColor = .Label
// Say, in the storyboard you set your button's height to 40
button.layer.cornerRadius = button.frame.height / 2
```
This way, you can change the height to whatever you want and you'll always have that capsule look.


Now, my favorite (just learned how to implement this) is `continuousCorners`!
Capsules and just plain ol' rounded corners have a much nicer and smoother look.
**Add link here for more info**
You use this along with `cornerRadius`. Here's how to implement it:
```swift
let button = UIButton()
button.backgroundColor = .systemIndigo
button.tintColor = .Label
button.layer.cornerRadius = 12
button.layer.cornerCurve = .continuous
```
The difference is subtle, but pretty amazing!!























