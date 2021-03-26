# Shader

This class allows you to load Shaders from a path and to access/modify uniforms inside the given
Shader. You can also access the Uber shader and modify its Uniform values.

The shaders loaded from here use a specific format to be able to load both Vertex and Fragment
shaders in one file. To access the different types of Shader stages supported (Vertex and Fragment
atm), you can use macros: `#vertex` to change into the Vertex shader and `#fragment` to change into
the Fragment shader. You can also use `#ignore` macro to write into no Shader stage in particular.
You are able to include other shaders by using the macro `#include` follow by a path relative to the
given shader. Example: `#include colour.glsl`.

## Functions

- `#!csharp static Shader GetUberShader()` Returns a Shader class with a reference to the Uber
  shader. Please note that this particular Shader has the destructor disabled.

- `#!csharp Shader(string path)` Constructor for the Shader class. It takes a string as an argument
  and returns built shader.
- `#!csharp void Draw()` Draws the given Shader, by selecting its program as the one to use when
  drawing meshes.
- `#!csharp int GetLocation(string name)` Returns a location to a Uniform with the same name as the
  one given. Returns a -1 and an Error Log when no Uniform is found with the given name. Please note
  that no Draw of the Shader is done before getting the location, and if a Variable is not used
  inside the GLSL shader it might be removed to optimize it.
- `#!csharp uint GetProgram()` Returns the OpenGL ID of the Shader Program.
- `#!csharp void SetInt(int location, int val)`
- `#!csharp void SetVec2(int location, Vec2 val)`
- `#!csharp void SetVec3(int location, Vec3 val)`
- `#!csharp void SetVec4(int location, Vec4 val)`
- `#!csharp void SetMat3(int location, Mat3 val)`
- `#!csharp void SetMat4(int location, Mat4 val)`
