# Window

The window system is special, since it uses a hidden window to coordinate a shared OpenGL Context
and coordinate system events, this window will be called default_window. Each window can be said to
be tied to the default_window, this being the case since if all the windows have been closed the
default_window will enter exit mode.

The window to be made current context at the start of each Update is the first one to be created
that is still active. You can force the current context by calling `MakeCurrent`. A window can still
exist in the C# Script, but it may have become inactive in the C++ backend, this can occur due
to System events, or simply because the user has called the `Close` function.

Since the OpenGL Context is shared between all the windows, any resource created can be used in any
window. The only warning to be given is that if you make use of more than one window, you **must**
keep track of active windows and check if a window is active before drawing.

!!! info
    When changing Projection type (Perspective <-> Ortho) call `MakeCurrent`, since this is the step in
    which the Projection Matrix is calculated and loaded into the Shader.

## Functions

- `#!csharp static void SetPerspective(float fov)` Sets window projection mode to Perspective with
  the given FOV in Radians.
- `#!csharp static void SetOrtho()` Sets window projection mode to Orthogonal.
- `#!csharp Window(uint width, uint height, string title = "VisualKey")` Creates a window with the given width, height and title.
- `#!csharp bool IsOrtho()`
- `#!csharp bool IsPerspective()`
- `#!csharp void Background(uint r, uint g, uint b)` Sets Background color to the given values divided by 255.
- `#!csharp void Background(Vec3 color)` Sets Background color to the given Vec3 divided by 255.
- `#!csharp void Background(Color color)` Sets Background color to the given Color.
- `#!csharp void HideCursor()` Hides window cursor and locks it.
- `#!csharp void ShowCursor()` Shows window cursor and unlocks it.
- `#!csharp bool Fullscreen()` Makes the window fullscreen and returns its fullscreen state.
- `#!csharp void MakeCurrent()` Recalculates Projection Matrix and Makes the window the current context.
- `#!csharp void Close()` Closes the window and makes it inactive.
- `#!csharp bool IsValid()` Returns if the window is still active in the C++ backend.

## Fields

- `#!csharp size` Returns the current Window size, it uses custom Get and Set to resize when
  changed.

## Example

```csharp
using System;
using VisualKey;

class App {

  Window window = new Window(1280, 720);
  Rectangle rectangle = new Rectangle(100, 100);

  void Start() {
    Console.WriteLine("Starting...");
  }

  void Update() {
    window.Background(33, 33, 33);
    rectangle.Draw();
  }

  void Stop() {
    Console.WriteLine("Stopping...");
  }
}
```
