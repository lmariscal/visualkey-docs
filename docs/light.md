# Light

Simple Light system that supports multiple Light Sources.

!!! important
    In the Uber shader there is a Maximum of 256 Light Sources.

## Functions

- `#!csharp static void Enable()` Enables the Light system by loading all given Light Sources into
  the current Shader.
- `#!csharp static void Disable()` Disables the Light system by setting the Number of Lights to 0
  and AmbientLight to 1.

- `#!csharp Light(Vec3 position)` Create a Light with the given Position.
- `#!csharp void Destroy()` Public pseudo destructor since you need to destroy the Light Source for
  it to cease having effect.

## Fields

- `#!csharp Vec3 Position` Position of the Light Source, with custom Get and Set
