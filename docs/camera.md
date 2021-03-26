# Camera

This class is an implementation of a very simple Camera, it is fully written in C#, so it is a good
example of what you can do with the tools given ([src](https://github.com/lmariscal/visualkey/blob/main/csharp/Camera.cs)).
By default, this class saves a reference to the Uber shader in order to set the `View` Uniform
Matrix. To implement it into your project you must first call the `Update` function, which makes use
of the `WASD` keys to move in XZ and `QE` to move in the `Y` axis.

To properly render in a Perspective view enable those features in the Window object:

```csharp
camera.Update(); // Updates position and rotation, via the Input
camera.Draw() // Sets the View uniform the given Shader
window.Background(38, 50, 56); // Clear color buffer
Window.SetPerspective(MathV.Radians(90)); // Sets Perspective view with a FOV of 90
window.HideCursor(); // Hides the cursor to lock it inside the window
window.MakeCurrent(); // Recalculates and applies the Projection Matrix
```

## Functions

- `#!csharp Camera` Creates a new Camera with the Uber Shader, position Vec3(0, 0, -3) and rotation
  Euler Vec2(-90, 0).
- `#!csharp void Update()` Updates position and rotation via Input
- `#!csharp void Draw()` Sets the View uniform in the given Shader
- `#!csharp void SetNone()` Sets the View uniform to Mat4 Identity
- `#!csharp Mat4 GetView()` Returns a Mat4 with the Calculated View Matrix
