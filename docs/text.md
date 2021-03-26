# Text

Text rendering class. Due to its nature this Class doesn't make use of the Uber shader, but of a
custom one. It uses FreeType to load Font textures and Glyph information.

It makes use of the Mesh transform state, so translation and rotation using the Mesh and Stash
system are okay. What it doesn't use is the Color and Texture system, that's why each Text contains
its own Color.

## Functions

- `#!csharp Text(string text, Color color)` Creates a Text with the given Text and Color.
- `#!csharp void Draw(float scale)` Renders the Text with the stored Color and given Scale.

## Fields

- `#!csharp string text` The text string to draw.
- `#!csharp Color color` Color to apply while rendering the Text.

## Examples

It is recommended that you draw the Text at the end of your update, since the Blend Alpha function
can complain if not.

```csharp
Text text = new Text("delta: ", new Color(255, 255, 255));

void Update() {
  text.text = "delta: " + Time.deltaTime;
  text.Draw();
}
```
