# How to setup development environment for C# scripts

## Prerequisites

1. FiveReborn installed client. Get it [here](https://forum.fivem.net/t/fivereborn-release/89).
3. FiveReborn installed server. Get it [here](https://forum.fivem.net/t/fivereborn-release/89) (same as above).
2. Visual Studio 2015 Community. Its free. Get it [here](https://www.visualstudio.com/ru/downloads/).

We will assume that your client installed here `C:\FiveReborn\client` and server installed here `C:\FiveReborn\server`.

## Preparation

### Create a resource

We will create a resource named `example`.

Make a resource folder inside `C:\FiveReborn\server` with a name`example`.

Then create a `__resource.lua` file in it with content:
```lua
client_script "example.net.dll"
```

### Create project in Visual Studio

`File -> New -> Project`

Create it with whatever name you like whereever you like, it doesn't matter.

Pick a template: "Visual C#" -> "Class library".

![](https://i.imgur.com/C5dpWHu.png)

## Configuration

### Configure project properties

Open project properties.
![](https://i.imgur.com/SSbokJB.png)

Change the "Assembly name" to `example.net.dll`. This is needed for FiveReborn client to pick up that correctly.

Now you wanna add the "Post-build" event so when you build your project it will automatically copy `example.net.dll` to your resource folder.

Go to "Build Events" tab in the project properties and add "Post-build event command line":
```
copy /y $(TargetPath) C:\FiveReborn\server\resources\example
```
![](https://i.imgur.com/6ggUKpg.png)


### Add the reference to `CitizenFX.Core`

In order to work with API you need to add reference to the base library called `CitizenFX.Core`.

Click "Add Reference" in "References" context menu.
![](https://i.imgur.com/yL8Rhhj.png)

On the bottom of the opened window click "Browse...".
![](https://i.imgur.com/n4NAQ4O.png)

Now you need to navigate to your client installation directory. In it follow the path `citizen\clr2\lib\mono\4.5`.

Select `CitizenFX.Core.dll` and hit "Add".

## Finishing

That's it, your environment is ready.

Don't forget to add your resource to the `AutoStartResources` section of `C:\FiveReborn\server\citmp-server.yml` so it will, you know, automatically start :)

## Example of the code

This will show notification above the minimap when you press `Z` on keyboard.

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using CitizenFX.Core;
using CitizenFX.Core.UI;

namespace Example
{
  public class Class1: BaseScript
  {
    public Class1()
    {
      Tick += OnTick;
    }

    public async Task OnTick()
    {
      // Show notification when Z was pressed
      if (Game.IsControlJustReleased(0, Control.MultiplayerInfo))
      {
        Screen.ShowNotification("Hello, mister!");
      }
    }
  }
}
```
