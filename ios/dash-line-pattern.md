# Draw a dashed border for UIView

There is a way to apply a dashed border onto UIView using `lineDashPattern` of `CAShapeLayer` 

```swift
let customView = UIView()
let  = CAShapeLayer()
shapeLayer.strokeColor = UIColor.red.cgColor
shapeLayer.lineDashPattern = [5, 5]
shapeLayer.frame = customView.bounds
shapeLayer.fillColor = UIColor.clear.cgColor
shapeLayer.path = UIBezierPath(roundedRect: customView.bounds).cgPath
customView.layer.addSublayer(shapeLayer)
```

Basically, `lineDashPattern` is an array of NSNumber. It defines the lengths of the painted segments and unpainted segments of the dash pattern.

Passing [5, 5] as above sets a pattern with a 5-user-space-unit-long painted segment and a 5-user-space-unit-long unpainted segment. 

Passing `nil` makes it return a solid line.

The image below is from Apple Docs, it shows effects of these different line dash pattern: nil, [2, 3], [10, 5, 5]. The last one is 10-long painted segments, 5-long unpainted segments, 5-long painted segments and 5-long unpainted segments then repeat.

![different-dash-line-styles]()

We could easily achieve rounded border using init function of UIBezierPath

```swift
convenience init(roundedRect rect: CGRect, 
    cornerRadius: CGFloat)
```
