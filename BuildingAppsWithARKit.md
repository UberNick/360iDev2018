# Building Augmented Reality Apps with ARKit

#### Speaker: [Mohammad Azam](https://360idev.com/speakers/mohammad-azam/)

Apple's _SceneKit_ can be used to create AR experiences.

The environment you view is called a "scene".
A scene is comprised of a number of "nodes".
* For example, if you were looking at a gas station, all that you can see would be the "scene", and then each car, person, building, etc. would be a separate node.

To add a new item to the view, you add a new "node" to a "scene".

_All measurement units in SceneKit are in meters._

"Material" is the decorations you can add to items (color, decorations, etc.)

"Plane detection" is how ARKit detects stuff like walls and the floor.
* For example, if you want to place an item on the ground, you use plane detection.
* Plane detection works better on surfaces that are well-lit and have some sort of texture.

Items are placed on a plane via an "anchor".

A "hit test" on a view is detection of whether or not a certain point intersects with a view.

#### Classes
_AR prefix: ARKit_
_SCN prefix: SceneKit_
* Anchor = ARAnchor (or ARPlaneAnchor)
* Node = SCNNode
* Plane = SCNPlane
* Material = SCNMaterial
* Scene = ARSCNView
