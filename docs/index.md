# Getting Started

VisualKey is a Graphics Sketchbook, in the sense that it enables you to work directly with Shaders,
Meshes, Window, Input, Texture, Audio, Text and Light systems, each at the level you need. For
example, you can use a pre-created Rectangle Mesh, or you can create your own Mesh with the
necessary Vertices and optional Indices.

## Installation

To get started you must first install VisualKey, at the moment it works with Windows 64 bits and
Linux 64 bits. To download the installer go to the [releases tab in the GitHub repo.](https://github.com/lmariscal/visualkey/releases/latest)

In the Windows installer be sure to enable `Add to Path` either for all Users or just for yourself.
The installed version is self-contained, since it contains the Mono utilities and libraries
necessary to run any VisualKey project.

## Basics

To begin using VisualKey you can make use of the command line interface to either run an existing
project or to create one:

```sh
visualkey init .
```

```sh
visualkey run .
```

The created project contains a `csproject` which can be used to open almost any editor that supports
C#. It also contains a .vscode folder with tasks to easily run your project using Visual Studio
Code, and a .run folder to easily run your project in the JetBrains Rider IDE.

## Visual Studio Code

In VSCode open a folder, in which your project will be created and stored. Presse ctrl + \` to open
the integrated terminal, or run the command `Terminal: Create New Integrated Terminal` in the show
commands panel (ctrl + shift + p).

Type: `visualkey init .`

!!! hint
    If there's an error message which states that `visualkey` is not an existing command, please
    restart VSCode. If the problem persists please reinstall VisualKey and be sure to enable
    `Add to Path`.

With the default project created, you will have an `App.cs` which is the entry point for VisualKey.
You can create any other C# source files and they will be linked together at run time.

### Autocompletion

To enable autocompletion you need the C# extension. A pop-up should show up when you load the
project recommending you to install the C# extension, but if not, open the extensions menu and seach
for `ms-dotnettools.csharp`.

The con of using this method of autocompletion is that it relies on an external installation of
dotnet. Follow [https://dotnet.microsoft.com/download](https://dotnet.microsoft.com/download)
download and install the SKD **not** the Runtime.

### Running

To run your project you don't need any external installation of neither dotnet nor mono. You can
call visualkey and run the project from the pre-generated tasks or via the command line.

#### Task

You can run the pre-generated build task by pressing: `ctrl+shift+b` in the default keybindings.

#### CLI

Run the project by calling the visualkey CLI:

```sh
cd project-dir
visualkey run .
```
or:

```sh
visualkey run project-dir/
```
