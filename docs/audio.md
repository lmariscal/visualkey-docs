# Audio

It uses [IRRKlang](https://www.ambiera.com/irrklang/index.html) as a sound engine and audio library. It is free for
non-commercial use but you must buy a license for commercial projects.
You can visit the [official license page](https://www.ambiera.com/irrklang/license.html) for more information.

A pull request with another sound engine would be highly appreciated. Please note that we would be looking for a
cross platform solution and an audio library which at least supports `WAV`, `OGG`.

Supports `WAV, MP3, OGG, FLAC, MOD, XM, IT, S3M`.

## Audio

Class that manages a given audio file.

### Fields

- `path` Path of the audio file. (string)
- `loop` Toggle if the audio should play on a loop. (bool)

### Constructors

- `#!csharp Audio(string path, bool loop = false)`

### Methods

- `#!csharp Play()` Play the given audio file, if on loop, will keep playing, on a loop...

### Example

```csharp
using VisualKey;

class App {

  Window window = new Window(1280, 720); // Needed to keep the program open
  Audio audio = new Audio("Kara Square - 8-Bit Side-Scrolling Action.wav", true);

  void Start() {
    audio.Play();
  }

}
```
