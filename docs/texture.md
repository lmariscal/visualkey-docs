# Texture

## Texture

This class allows you to load images and set them for access in the given Shader. It uses stb_image
to load the Images and transform them into the correct format, using 4 channels (RGBA).

While creating the Texture_2D in OpenGL it uses these parameters:

```cpp
glTexParameterf(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR_MIPMAP_LINEAR);
glTexParameterf(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);

glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_CLAMP_TO_EDGE);
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_CLAMP_TO_EDGE);
```

### Functions

- `#!csharp static void SetNone()` Sets the Texture used to ID 0, which disables any Texture.
- `#!csharp Texture(string path)` Creates a Texture with the given path.
- `#!csharp void Draw()` Sets the Texture used to the ID of this Texture.

## Color

Colour*. It is a practical wrapper of a Vec4 which gives functionality to quickly load the value to
the Color uniform in the current Shader.

### Functions

- `#!csharp Color(Vec4 color)` Gets a Vec4 and divides the XYZ/RGB values by 255.0f, and the Alpha value by 100.0f if the value is bigger than 1.0f.
- `#!csharp Color(Vec3 color)` Gets a Vec4 and divides the XYZ/RGB values by 255.0f, the Alpha value is 1.0f.
- `#!csharp Color(uint r, uint g, uint b, uint a = 100)` Constructor that receives each value, RGB is divided by 255.0f and Alpha always by 100.0f.
- `#!csharp void Draw()` Quickly loads the Value into the current Shader into the Uniform `Color`
