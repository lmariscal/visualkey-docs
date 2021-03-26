# Graphics

As a backend the project is using an OpenGL 3.2 renderer. It abstracts this renderer into a Mesh
system, then it further simplifies it into 3D shapes. The user is able to access both the Mesh
system and the Shapes system.

To change the position of certain Meshes (Shapes) it uses a single state, which can be modified by
using the `Mesh.Translate` function. This single state is shared between all the Meshes, so the
responsibility of managing it lies on the user.

A way to save the current position and rotation state is to create a `Stash`, you can create a new
Stash by creating its object `#!csharp Stash stash = new Stash();`. This takes a snapshot of the
current state which you can modify in any way you want. To recover this snapshot of a state, it is
as simple as `#!csharp stash.Pop();`. This doesn't invalidate the state saved in the Stash, so you
can further reuse it.

## Mesh

The base object, which holds the information about the mesh, this being: vertices, indices and
primitive type.

### Constructors

- `#!csharp Mesh(float[] vertices, bool isLine = false)`
- `#!csharp Mesh(float[] vertices, uint[] indices, bool isLine = false)`

The `isLine` parameter changes the primitive type of the Mesh into `GL_LINES`
from `GL_TRIANGLES`.

### Methods

- `static void Translate(Vec3 position)` Set state's position value.

- `static void Rotate(Vec3 rotation)` Set state's rotation value.

- `static void RotateX(float rotation)` Set state's rotation value.

- `static void RotateY(float rotation)` Set state's rotation value.

- `static void RotateZ(float rotation)` Set state's rotation value.

- `static void PolygonMode(bool mode)` Set `true` to fill polygons, and `false` not.

### Example

As it is using an Uber shader at the moment, all the meshes, indistinctly of them being 2D or 3D,
use 8 f32 to represent Vertex. The first 3 values are the position of the Vertex, followed by 2
values of Texture Coordinates, finished by 3 values of the Vertex's Normals.

```csharp
public class Line {
  public Mesh mesh { get; private set; }

  private void CreateLine(float p0x, float p0y, float p1x, float p1y) {
    float[] vertices = {
      p0x, p0y, 0.0f,  0.0f, 0.0f,  0.0f, 0.0f, 0.0f,
      p1x, p1y, 0.0f,  0.0f, 0.0f,  0.0f, 0.0f, 0.0f
    };
    mesh = new Mesh(vertices, true);
  }

  public Line(float p0x, float p0y, float p1x, float p1y) {
    CreateLine(p0x, p0y, p1x, p1y);
  }

  public Line(Vec2 p0, Vec2 p1) {
    CreateLine(p0.x, p0.y, p1.x, p1.y);
  }

  public void Draw() {
    mesh.Draw();
  }
}
```

You can also, make Meshes with Indices for the Vertices:

```csharp
public class Rectangle {
  public Mesh mesh { get; private set; }

  public Rectangle(float width, float height) {
    float[] vertices = {
        (width / 2.0f),  (height / 2.0f), 0.0f,  1.0f, 1.0f,  0.0f, 0.0f, 0.0f,
        (width / 2.0f), -(height / 2.0f), 0.0f,  1.0f, 0.0f,  0.0f, 0.0f, 0.0f,
       -(width / 2.0f), -(height / 2.0f), 0.0f,  0.0f, 0.0f,  0.0f, 0.0f, 0.0f,
       -(width / 2.0f),  (height / 2.0f), 0.0f,  0.0f, 1.0f,  0.0f, 0.0f, 0.0f
    };
    uint[] indices = {
      0, 2, 1,
      2, 0, 3
    };
    mesh = new Mesh(vertices, indices);
  }

  public void Draw() {
    mesh.Draw();
  }
}
```

Please take into consideration that the renderer enables Culling in a Counter Clock Wise mode.
