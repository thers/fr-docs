# How to setup development environment for C# scripts

## Prerequisites

1. FiveReborn installed client. Get it [here](https://forum.fivem.net/t/fivereborn-release/89).
3. FiveReborn installed server. Get it [here](https://forum.fivem.net/t/fivereborn-release/89) (same as above).
2. Visual Studio 2015 Community. Its free. Get it [here](https://www.visualstudio.com/ru/downloads/).

We will assume that your client installed here `C:\FiveReborn\client` and server installed here `C:\FiveReborn\server`.

## Creating a solution

1. Create it from template: "Visual C#" -> "Class library".
2. You want it to be created inside `resources` folder of the server installation. Thats to simplify development.
3. *Make sure to pick lowercase name for your solution.*

## Configure the solution

Open the project properties.

![](https://i.imgur.com/ik3qMz9.png)

Change the name of assembly. From, lets say, `MyAwesomeResource` you should get `myawesomeresource.net`.

![](https://i.imgur.com/cENp543.png)

Go to "Build" section. Select "Release" configuration. Change the build path to lowercase one.

![](https://i.imgur.com/ya6zw52.png)

Don't forget to select the same "Release" configuration on toolbar.

![](https://i.imgur.com/1sklXLI.png)

## Link `CitizenFX.Core`

Select "Add Reference" in references context menu.

![](https://i.imgur.com/NM4fxsF.png)

On the bottom of the opened window click "Browse...".

Now you need to navigate to your client installation directory. In it follow the path `citizen\clr2\lib\mono\4.5`.

Select `CitizenFX.Core.dll` and hit "Add".

## Make `__resource.lua`

In order for FiveReborn to pick up your script you should make `__resource.lua` in the root of your solution.


