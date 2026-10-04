# ImApp

**ImApp** is a lightweight C# application framework for building native desktop applications with **Dear ImGui**, **GLFW**, and **OpenGL**.

It provides a small application/window layer while keeping Dear ImGui as the main UI API.

![ImApp Application Preview](https://raw.githubusercontent.com/codefluxo/ImApp/main/docs/Screenshot%20From%202026-10-04%2007-38-51.png)

> **Status:** Early development

## Features

* Native desktop windows via GLFW
* Dear ImGui integration
* OpenGL rendering
* Configurable window options
* Borderless and resizable windows
* Maximized windows
* Transparent windows
* Topmost windows
* Mouse passthrough
* Dear ImGui docking
* Optional full-window host
* Target FPS limiter
* Embedded Noto Sans font
* .NET 10

## Requirements

* .NET 10 SDK/runtime
* OpenGL 3.2+
* GLFW-compatible desktop environment

## Installation

Install ImApp using the .NET CLI:

```bash
dotnet add package ImApp
```

Or add it directly to your `.csproj`:

```xml
<PackageReference Include="ImApp" Version="0.2.0" />
```

## Quick Start

```csharp
using Hexa.NET.ImGui;
using ImApp;

using var app = new App(new WindowOptions
{
    Title = "My Window",
    Width = 800,
    Height = 600
});

app.Run(() =>
{
    ImGui.Begin("Hello");

    ImGui.Text("Hello from ImApp!");

    if (ImGui.Button("Click Me"))
    {
        Console.WriteLine("Button clicked");
    }

    ImGui.End();
});
```

## Window Options

ImApp provides a `WindowOptions` class for configuring the application window.

| Property           | Default          |
| ------------------ | ---------------- |
| `Title`            | `"ImApp Window"` |
| `Width`            | `800`            |
| `Height`           | `600`            |
| `Decorated`        | `true`           |
| `Resizable`        | `true`           |
| `Transparent`      | `false`          |
| `Topmost`          | `false`          |
| `Maximized`        | `false`          |
| `Visible`          | `true`           |
| `Focused`          | `true`           |
| `MousePassthrough` | `false`          |
| `DockingEnabled`   | `false`          |
| `HostWindow`       | `true`           |
| `TargetFps`        | `100`            |
| `FontSize`         | `17`             |

Example:

```csharp
using var app = new App(new WindowOptions
{
    Title = "ImApp Window",
    Width = 1200,
    Height = 800,

    Decorated = true,
    Resizable = true,

    TargetFps = 144,
    FontSize = 18
});
```

## Host Window

By default, ImApp provides a host ImGui window.

```csharp
HostWindow = true
```

You can disable the host window and manage ImGui windows yourself:

```csharp
using var app = new App(new WindowOptions
{
    HostWindow = false
});
```

This is useful when you want complete control over the Dear ImGui layout.

## Docking

Dear ImGui docking can be enabled through `WindowOptions`.

```csharp
using Hexa.NET.ImGui;
using ImApp;

using var app = new App(new WindowOptions
{
    Title = "ImApp Docking",
    Width = 1200,
    Height = 800,
    DockingEnabled = true
});

app.Run(() =>
{
    ImGui.ShowDemoWindow();
});
```

## Transparent / Borderless Window

ImApp supports transparent and borderless windows.

```csharp
using var app = new App(new WindowOptions
{
    Decorated = false,
    Transparent = true,
    MousePassthrough = true
});
```

This can be useful for overlays and custom desktop UI.

## Font

ImApp includes **Noto Sans Regular** and loads it automatically.

You can configure the font size through `WindowOptions`:

```csharp
using var app = new App(new WindowOptions
{
    FontSize = 18
});
```

This avoids requiring Noto Sans to be installed on the user's system.

## Dependencies

ImApp is built using:

* [Dear ImGui](https://github.com/ocornut/imgui)
* [Hexa.NET.ImGui](https://github.com/HexaEngine/Hexa.NET.ImGui)
* [Hexa.NET.GLFW](https://github.com/HexaEngine/Hexa.NET.GLFW)
* [Hexa.NET.OpenGL](https://github.com/HexaEngine/Hexa.NET.OpenGL)
* [Hexa.NET.ImGui.Backends.GLFW](https://github.com/HexaEngine/Hexa.NET.ImGui.Backends)
* [Hexa.NET.ImGui.Backends.OpenGL3](https://github.com/HexaEngine/Hexa.NET.ImGui.Backends)
* [HexaGen.Runtime](https://github.com/HexaEngine/HexaGen)

## License

ImApp is released under the **MIT License**.
