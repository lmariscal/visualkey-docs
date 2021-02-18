# Math

Data structures that are useful when working with lineal algebra.

## Vec2

Two dimensional vector data structure.

### Fields

- `x` First component of the vector. (Float)
- `y` Second component of the vector. (Float)

### Constructors

- `#!csharp Vec2(float n)` Take a scalar and make all components this value.
- `#!csharp Vec2(float x, float y)` Take one scalar for each component.
- `#!csharp Vec2(Vec3 v)` Convert a `Vec3` to `Vec2`, losing the third component.
- `#!csharp Vec2(Vec4 v)` Convert a `Vec4` to `Vec2`, losing the third and fourth component.

### Methods

- `#!csharp []` Operator overload to access each respective component.
- `#!csharp +(Vec2 i, Vec2 j)` Operator overload.
- `#!csharp -(Vec2 i, Vec2 j)` Operator overload.
- `#!csharp *(Vec2 i, float k)` Operator overload, scalar affects each component.
- `#!csharp /(Vec2 i, float k)` Operator overload, scalar affects each component.
- `#!csharp +(Vec2 i, float k)` Operator overload, scalar affects each component.
- `#!csharp -(Vec2 i, float k)` Operator overload, scalar affects each component.
- `#!csharp Set(float x, float y)` Set the components of the `Vec2`.
- `#!csharp MagnitudeSqrt()` Calculates the magnitude of the `Vec2`, squared.
- `#!csharp Magnitude()` Calculates the magnitude of the `Vec2`.
- `#!csharp Normalize()` Normalize the `Vec2` to a length of 1.
- `#!csharp Dot(Vec2 other)` Calculates the dot product of two `Vec2`.
- `#!csharp Angle(Vec2 other)` Calculates the angle respective to other `Vec2`.
- `#!csharp DistanceSqrt(Vec2 other)` Calculate the distance between two `Vec2`, squared.
- `#!csharp Distance(Vec2 other)` Calculate the distance between two `Vec2`.

- `#!csharp static down()` Returns `Vec2(0, -1)`.
- `#!csharp static left()` Returns `Vec2(-1, 0)`.
- `#!csharp static up()` Returns `Vec2(0, 1)`.
- `#!csharp static right()` Returns `Vec2(1, 0)`.
- `#!csharp static zero()` Returns `Vec2(0)`.
- `#!csharp static one()` Returns `Vec2(1)`.

### Example

```csharp
using System;
using VisualKey;

class App {

  Window window;
  Vec2 pos = new Vec2(0);

  void Start() {
    var x = new Vec2(10, 20);
    x += 3;
    Console.WriteLine(x); // (x: 13, y: 23)

    var d = x.Dot(new Vec2(20, 10));
    Console.WriteLine(d); // 490

    var n = x.Normalize();
    Console.WriteLine(n); // (x: 0.4920573, y: 0.8705629)

    window = new Window((uint)size.x, (uint)size.y);
  }

  void Update() {
    if (Key.A.IsPressed())
      pos.x += Time.deltaTime * 1;
    Console.WriteLine("x: " + pos.x); // Same as pos[0]
  }

}
```

## Vec3

Three dimensional vector data structure.

### Fields

- `x` First component of the vector. (Float)
- `y` Second component of the vector. (Float)
- `z` Third component of the vector. (Float)

### Constructors

- `#!csharp Vec3(float n)` Take a scalar and make all components this value.
- `#!csharp Vec3(float x, float y, float z)` Take one scalar for each component.
- `#!csharp Vec3(Vec2 v, float z)` Convert a `Vec2` to `Vec3`, adding the third component.
- `#!csharp Vec3(Vec4 v)` Convert a `Vec4` to `Vec3`, losing the fourth component.

### Methods

- `#!csharp []` Operator overload to access each respective component.
- `#!csharp *(Vec3 v, Mat3 m)` Operator overload, multiply `Vec3` to `Mat3`.
- `#!csharp +(Vec3 i, Vec3 j)` Operator overload.
- `#!csharp -(Vec3 i, Vec3 j)` Operator overload.
- `#!csharp *(Vec3 i, float k)` Operator overload, scalar affects each component.
- `#!csharp /(Vec3 i, float k)` Operator overload, scalar affects each component.
- `#!csharp +(Vec3 i, float k)` Operator overload, scalar affects each component.
- `#!csharp -(Vec3 i, float k)` Operator overload, scalar affects each component.
- `#!csharp Set(float x, float y, float z)` Set the components of the `Vec3`.
- `#!csharp MagnitudeSqrt()` Calculates the magnitude of the `Vec3`, squared.
- `#!csharp Magnitude()` Calculates the magnitude of the `Vec3`.
- `#!csharp Normalize()` Normalize the `Vec3` to a length of 1.
- `#!csharp Dot(Vec3 other)` Calculates the dot product of two `Vec3`.
- `#!csharp Angle(Vec3 other)` Calculates the angle respective to other `Vec3`.
- `#!csharp Cross(Vec3 other)` Calculates the cross product respective to other `Vec3`.
- `#!csharp DistanceSqrt(Vec3 other)` Calculate the distance between two `Vec3`, squared.
- `#!csharp Distance(Vec3 other)` Calculate the distance between two `Vec3`.
- `#!csharp RGB()` Return a new `Vec3` with same components divided by `255.0f`.

- `#!csharp static back()` Returns `Vec3(0, 0, -1)`.
- `#!csharp static down()` Returns `Vec3(0, -1, 0)`.
- `#!csharp static left()` Returns `Vec3(-1, 0, 0)`.
- `#!csharp static forward()` Returns `Vec3(0, 0, 1)`.
- `#!csharp static up()` Returns `Vec3(0, 1, 0)`.
- `#!csharp static right()` Returns `Vec3(1, 0, 0)`.
- `#!csharp static zero()` Returns `Vec3(0)`.
- `#!csharp static one()` Returns `Vec3(1)`.

### Example

```csharp
using System;
using VisualKey;

class App {

  Window window;
  Vec3 pos = new Vec3(0);

  void Start() {
    var x = new Vec3(10, 20, 30);
    x += 3;
    Console.WriteLine(x); // (x: 13, y: 23, z: 33)

    var d = x.Dot(new Vec3(30, 20, 10));
    Console.WriteLine(d); // 1180

    var n = x.Normalize();
    Console.WriteLine(n); // (x: 0.3075255, y: 0.5440835, z: 0.7806416)

    window = new Window(1280, 720);
  }

  void Update() {
    if (Key.A.IsPressed())
      pos.x += Time.deltaTime * 1;
    Console.WriteLine("x: " + pos.x); // Same as pos[0]
  }

}
```

## Vec4

Four dimensional vector data structure.

### Fields

- `x` First component of the vector. (Float)
- `y` Second component of the vector. (Float)
- `z` Third component of the vector. (Float)
- `z` Fourth component of the vector. (Float)

### Constructors

- `#!csharp Vec4(float n)` Take a scalar and make all components this value.
- `#!csharp Vec4(float x, float y, float z, float w)` Take one scalar for each component.
- `#!csharp Vec4(Vec2 v, float z, float w)` Convert a `Vec2` to `Vec4`, adding the third and fourth component.
- `#!csharp Vec4(Vec3 v, float w)` Convert a `Vec3` to `Vec4`, adding the fourth component.
- `#!csharp Vec4(Quat q)` Convert a `Quat` to `Vec4`.

### Methods

- `#!csharp []` Operator overload to access each respective component.
- `#!csharp +(Vec4 i, Vec4 j)` Operator overload.
- `#!csharp -(Vec4 i, Vec4 j)` Operator overload.
- `#!csharp *(Vec4 i, float k)` Operator overload, scalar affects each component.
- `#!csharp /(Vec4 i, float k)` Operator overload, scalar affects each component.
- `#!csharp +(Vec4 i, float k)` Operator overload, scalar affects each component.
- `#!csharp -(Vec4 i, float k)` Operator overload, scalar affects each component.
- `#!csharp Set(float x, float y, float z, float w)` Set the components of the `Vec4`.
- `#!csharp MagnitudeSqrt()` Calculates the magnitude of the `Vec4`, squared.
- `#!csharp Magnitude()` Calculates the magnitude of the `Vec4`.
- `#!csharp Normalize()` Normalize the `Vec4` to a length of 1.
- `#!csharp Dot(Vec4 other)` Calculates the dot product of two `Vec4`.
- `#!csharp Angle(Vec4 other)` Calculates the angle respective to other `Vec4`.
- `#!csharp DistanceSqrt(Vec4 other)` Calculate the distance between two `Vec4`, squared.
- `#!csharp Distance(Vec4 other)` Calculate the distance between two `Vec4`.
- `#!csharp RGBA()` Return a new `Vec4` with same components divided by `255.0f`, except the fourth which is divided by `100.0f`.

- `#!csharp static zero()` Returns `Vec4(0)`.
- `#!csharp static one()` Returns `Vec4(1)`.

### Example

```csharp
using System;
using VisualKey;

class App {

  Window window;
  Vec4 pos = new Vec4(0);

  void Start() {
    var x = new Vec4(10, 20, 30, 40);
    x += 3;
    Console.WriteLine(x); // (x: 13, y: 23, z: 33)

    var d = x.Dot(new Vec4(40, 30, 20, 10));
    Console.WriteLine(d); // 2300

    var n = x.Normalize();
    Console.WriteLine(n); // (x: 0.2155914, y: 0.3814309, z: 0.5472704, w: 0.71311)

    window = new Window(1280, 720);
  }

  void Update() {
    if (Key.A.IsPressed())
      pos.x += Time.deltaTime * 1;
    Console.WriteLine("x: " + pos.x); // Same as pos[0]
  }

}
```
## Mat3

Three dimensional matrix data structure.

### Fields

- `row0` First component of the matrix. (Vec3)
- `row1` Second component of the matrix. (Vec3)
- `row2` Third component of the matrix. (Vec3)

### Constructors

- `#!csharp Mat3(float n)` Take a scalar and make all components this value.
- `#!csharp Mat3(Vec3 row0, Vec3 row1, Vec3 row2)` Take three `Vec3` and make each row this value.
- Take one scalar per each component of the `Mat3`:
```csharp
Mat3(float v00, float v01, float v02,
     float v03, float v04, float v05,
     float v06, float v07, float v08)
```

### Methods

- `#!csharp []` Operator overload to access each respective component.
- `#!csharp *(Mat3 m, float k)` Operator overload, scalar affects each component.
- `#!csharp /(Mat3 m, float k)` Operator overload, scalar affects each component.
- `#!csharp +(Mat3 m, float k)` Operator overload, scalar affects each component.
- `#!csharp -(Mat3 m, float k)` Operator overload, scalar affects each component.
- `#!csharp *(Mat3 m, Mat3 other)` Multiply two `Mat3`.
- `#!csharp ToArray()` Convert `Mat3` to `float[9]`.

- `#!csharp static identity()` Returns an identity `Mat3`.
- `#!csharp static zero()` Returns `Mat3(0)`.
- `#!csharp static one()` Returns `Mat3(1)`.

### Example

```csharp
using System;
using VisualKey;

class App {

  void Start() {
    var m = new Mat3(1, 2, 3,
                     4, 5, 6,
                     7, 8, 9);
    var o = m * Mat3.identity();
    Console.WriteLine(o);
  }

}
```

## Mat4

Four dimensional matrix data structure.

### Fields

- `row0` First component of the matrix. (Vec4)
- `row1` Second component of the matrix. (Vec4)
- `row2` Third component of the matrix. (Vec4)
- `row3` Fourth component of the matrix. (Vec4)

### Constructors

- `#!csharp Mat4(float n)` Take a scalar and make all components this value.
- `#!csharp Mat4(Vec4 row0, Vec4 row1, Vec4 row2, Vec4 row3)` Take four `Vec4` and make each row this value.
- Take one scalar per each component of the `Mat4`:
```csharp
Mat4(float v00, float v01, float v02, float v03,
     float v04, float v05, float v06, float v07,
     float v08, float v09, float v10, float v11,
     float v12, float v13, float v14, float v15)
```

### Methods

- `#!csharp []` Operator overload to access each respective component.
- `#!csharp *(Mat4 m, float k)` Operator overload, scalar affects each component.
- `#!csharp /(Mat4 m, float k)` Operator overload, scalar affects each component.
- `#!csharp +(Mat4 m, float k)` Operator overload, scalar affects each component.
- `#!csharp -(Mat4 m, float k)` Operator overload, scalar affects each component.
- `#!csharp *(Mat4 m, Mat4 other)` Multiply two `Mat4`.
- `#!csharp ToArray()` Convert `Mat4` to `float[16]`.
- `#!csharp Scale(Vec3 elements)`
- `#!csharp LookAt(Vec3 eye, Vec3 at, Vec3 up)`
- `#!csharp Ortho(float left, float right, float bottom, float top, float zNear, float zFar)`
- `#!csharp Perspective(float fov, float aspect, float zNear, float zFar)`
- `#!csharp RotateX(float angle)`
- `#!csharp RotateY(float angle)`
- `#!csharp RotateZ(float angle)`
- `#!csharp Translate(Vec3 offset)`

- `#!csharp static identity()` Returns an identity `Mat3`.
- `#!csharp static zero()` Returns `Mat3(0)`.
- `#!csharp static one()` Returns `Mat3(1)`.

### Example

```csharp
using System;
using VisualKey;

class App {

  void Start() {
    var m = new Mat4(1, 2, 3, 4,
                     5, 6, 7, 8,
                     9, 0, 1, 2,
                     3, 4, 5, 6);
    var o = m * Mat4.identity();
    Console.WriteLine(o);
  }

}
```
## Quat

Quaternion data structure.

### Fields

- `x` First component of the quaternion. (Float)
- `y` Second component of the quaternion. (Float)
- `z` Third component of the quaternion. (Float)
- `w` Fourth component of the quaternion. (Float)

### Constructors

- `#!csharp Quat(float n)` Take a scalar and make all components this value.
- `#!csharp Quat(float x, float y, float z, float w)` Take a scalar per each component.
- `#!csharp Quat(Vec4 v)` Take a `Vec4` and convert it to `Quat`.
- `#!csharp Quat(Vec3 axis, float angle)` Take a `Vec3` and convert it to `Quat` by providing an angle.
- `#!csharp Quat(Mat3 m)` Convert a `Mat3` to `Quat`.

### Methods

- `#!csharp []` Operator overload to access each respective component.
- `#!csharp *(Quat q, float k)` Operator overload, scalar affects each component.
- `#!csharp /(Quat q, float k)` Operator overload, scalar affects each component.
- `#!csharp +(Quat q, float k)` Operator overload, scalar affects each component.
- `#!csharp -(Quat q, float k)` Operator overload, scalar affects each component.
- `#!csharp *(Quat q, Quat other)` Operator overload, multiply two `Quat`.
- `#!csharp *(Quat q, Vec3 v)` Operator overload, multiply `Quat` with a `Vec3`.
- `#!csharp Set(float x, float y, float z, float w)` Set each component value.
- `#!csharp Conjugate()`
- `#!csharp Inverse()`
- `#!csharp Rotate(float angle, Vec3 v)`
- `#!csharp Roll()`
- `#!csharp Pitch()`
- `#!csharp Yaw()`
- `#!csharp EulerAngles()`
- `#!csharp Dot()`
- `#!csharp Mat3()` Convert `Quat` to `Mat3`.
- `#!csharp Mat4()`
- `#!csharp Mat4(Vec4 v)`
- `#!csharp Mat4(Vec3 v)`

- `#!csharp static identity()` Returns an identity `Mat3`.
- `#!csharp static zero()` Returns `Mat3(0)`.
- `#!csharp static one()` Returns `Mat3(1)`.

## MathV

Math utilities to work with `#!csharp float` values.

- `#!csharp Radians(float angle)` Convert an angle to radians.
- `#!csharp Clamp(float v, float l, float r)`
