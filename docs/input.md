# Input

The Input is managed by the Window system, using GLFW to retrieve the system events. These events
are then passed onto the Input system, which in turn manages the state of `Pressed`, `Released`, and
their variants in `JustPressed` and `JustReleased`.

## Functions

Using the Enums below, you can access their state by calling one of these functions:

For `Key`, `MouseButton`, `Pad`:

- `IsPressed()` Checks if the state of the Key/Button is Pressed.
- `IsJustPressed()` Checks if the state of the Key/Button has changed to Pressed. Please note that
  this function must be called every frame for the State to properly flush.
- `IsJustReleased()` Checks if the state of the Key/Button has changed to Released. Please note that
  this function must be called every frame for the State to properly flush.

For `JoyStick`:

- `GetAxis()` Returns a float with the Axis of the given JoyStick.

## Example

```csharp
void UpdateInput() {
  float speed = 2.5f * Time.deltaTime;
  if (Key.W.IsPressed())
    this.position -= front * speed;
  if (Key.S.IsPressed())
    this.position += front * speed;
  if (Key.A.IsPressed())
    this.position += front.Cross(up).Normalize() * speed;
  if (Key.D.IsPressed())
    this.position -= front.Cross(up).Normalize() * speed;
  if (Key.E.IsPressed())
    this.position += up * speed;
  if (Key.Q.IsPressed())
    this.position -= up * speed;
}
```

!!! warning
    A possible mistake while using the `Just` variants is that they are not called in every frame.
    This is wrong:

    ```csharp
    void Update() {
      if (Key.LeftControl.IsPressed() && Key.Q.IsJustPressed()) {
        // Something
      }
    }
    ```

    Since the second statement is not called on every frame, the state is not flushed properly,
    causing it to be always true whenever the Key Q has been pressed in the past, but not
    necessarily in that moment.

## Enums 

=== "Key"

    - Unknown
    - Space
    - Apostrophe
    - Comma
    - Minus
    - Period
    - Slash
    - N0
    - N1
    - N2
    - N3
    - N4
    - N5
    - N6
    - N7
    - N8
    - N9
    - Semicolon
    - Equal
    - A
    - B
    - C
    - D
    - E
    - F
    - G
    - H
    - I
    - J
    - K
    - L
    - M
    - N
    - O
    - P
    - Q
    - R
    - S
    - T
    - U
    - V
    - W
    - X
    - Y
    - Z
    - LeftBracket
    - Backslash
    - RightBracket
    - GraveAccent
    - World1
    - World2
    - Escape
    - Enter
    - Tab
    - Backspace
    - Insert
    - Delete
    - Right
    - Left
    - Down
    - Up
    - PageUp
    - PageDown
    - Home
    - End
    - CapsLock
    - ScrollLock
    - NumLock
    - PrintScreen
    - Pause
    - F1
    - F2
    - F3
    - F4
    - F5
    - F6
    - F7
    - F8
    - F9
    - F10
    - F11
    - F12
    - F13
    - F14
    - F15
    - F16
    - F17
    - F18
    - F19
    - F20
    - F21
    - F22
    - F23
    - F24
    - F25
    - KP0
    - KP1
    - KP2
    - KP3
    - KP4
    - KP5
    - KP6
    - KP7
    - KP8
    - KP9
    - KPDecimal
    - KPDivide
    - KPMultiply
    - KPSubtract
    - KPAdd
    - KPEnter
    - KPEqual
    - LeftShift
    - LeftControl
    - LeftAlt
    - LeftSuper
    - RightShift
    - RightControl
    - RightAlt
    - RightSuper
    - Menu

=== "MouseButton"

    - Left
    - Right
    - Middle
    - Button3
    - Button4
    - Button5
    - Button6
    - Button7
    - Button8

=== "Pad"

    - Pad0
    - Pad1
    - Pad2
    - Pad3
    - Pad4
    - Pad5
    - Pad6
    - Pad7
    - Pad8
    - Pad9
    - Pad10
    - Pad11
    - Pad12
    - Pad13
    - Pad14
    - Pad15

=== "PadButton"

    - A
    - B
    - X
    - Y
    - LeftBumper
    - RightBumper
    - Back
    - Start
    - Guide
    - LeftThumb
    - RightThumb
    - DPadUp
    - DPadRight
    - DPadDown
    - DPadLeft

=== "JoyStick"

    - LeftX
    - LeftY
    - RightX
    - RightY
    - LeftBumper
    - RightBumper
