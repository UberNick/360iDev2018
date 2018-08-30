# Stealing Views & Animations

* Session Link:
https://360idev.com/sessions/custom-view-and-animations-workshop/

* Repo:
https://github.com/sammyd/360iDev2018_ViewAndAnimations

* Similar:
https://www.raywenderlich.com/6278-new-course-reproducing-popular-ios-controls


## Author

**Sam Davies**

*@iwantmyrealname*

### Sample project

Start with "start_here" branch of cloned project

Open Views and Layers.playground

To follow along, view each commit of the git repo from that point

## Three projects
### Express VPN shield animation

We'll build it up with CALayers
  Those are the building blocks what we see in iOS (and increasingly MacOS)

Layers are essentially model objects that tell the system how to display a bitmap

Goes to the CoreAnimation engine

If you ever override drawRect, you're just overriding a CALayerDelegate

CAShapeLayer
  Special because the path isn't just the bounds like other layers

UIBezierPath

Type "color" into XCode and choose Color Literal
  Smart enough to be CGColor and UIColor

To show LiveView, click the connected-circles icon in XCode

Notice that many layer changes (hidden on/off) are implicitly animated

  Sometimes it's an issue with layers "fighting" eachother

  Path needs to be explicitly animated

When adding sublayers relative to something, do it to bounds

When adding co-layers relative to something, do it to frame

### Maps

Presenting View Controller (map view)

  Creates a container view in the same size as the presenting view controller

Presented view controller is the one stuck on top

UIWindow.maxFrame is the biggest visible frame

### App Store

Don't have time to get to it, but it's part of the git repo.  It's also an online lesson that Razeware offers
