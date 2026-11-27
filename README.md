A stronger wooden torch for Necesse.

Check out the [Steam workshop page for the mod.](https://steamcommunity.com/sharedfiles/filedetails/?id=3311404008)

### [Jar File for servers](https://github.com/bolo422/necesse-mod-better-torch/blob/main/ABetterTorch-0.26.1-1.1.jar)

### I'm not an artist, so if you want to submit a better texture for my mod I may accept it :)
Here's the current textures and how to submit a new one:
- [Torch object textures, ON and OFF versions](https://github.com/bolo422/necesse-mod-better-torch/tree/main/src/main/resources/objects)
- [Torch item texture (current the same as object)](https://github.com/bolo422/necesse-mod-better-torch/blob/main/src/main/resources/items/bettertorch.png)
- [Mod cover (Steam workshop icon)](https://github.com/bolo422/necesse-mod-better-torch/blob/main/src/main/resources/preview.png)
- My discord for your submission: `bolo422` (you can also make a pull request on github if you know how to do it)

---------
# Better Torch Reloaded

**Better Torch Reloaded** is a Necesse mod that adds a stronger, configurable wooden torch. It extends the vanilla torch and gives it a light level twice the vanilla default.

- **Current version:** `1.2.2`
- **Target Necesse game version:** `1.3.3`
- **Author:** Rkdevs

The mod is available on the [Steam Workshop](https://steamcommunity.com/sharedfiles/filedetails/?id=3311404008).

## Features

- Adds a placeable **Better Torch** object and inventory item.
- Emits light at a light level of `300`, compared with the vanilla torch's standard level.
- Supports custom light hue and saturation.
- Includes separate ON and OFF object textures.
- Provides three configurable crafting and uncrafting difficulties.
- Is server-side content, so it must be installed on the server and by multiplayer clients.

## Installation

### Steam Workshop

Subscribe to the mod through the [Steam Workshop page](https://steamcommunity.com/sharedfiles/filedetails/?id=3311404008), then enable the mod from the Necesse mod menu.

### Multiplayer servers

Because this mod is not marked as client-side-only, install the mod JAR on both the server and every multiplayer client. The server and clients should use matching mod and game versions.

## Crafting

The crafting recipe is selected through `recipeDifficulty` in `settings.cfg`.

| Difficulty | Required to craft | Better Torches produced | Required crafting station |
| --- | --- | ---: | --- |
| `EASY` | 2 vanilla torches | 1 | None |
| `MEDIUM` (default) | 4 vanilla torches | 1 | Workstation |
| `HARD` | 4 vanilla torches and 4 any-stone items | 1 | Workstation |

The mod also installs a reverse recipe:

- `EASY`: returns 2 vanilla torches from 1 Better Torch.
- `MEDIUM` and `HARD`: return 4 vanilla torches from 1 Better Torch.

Note: stone items are not returned when an item is crafted with the `HARD` recipe and subsequently uncrafted.

## Configuration

The mod creates the following settings file on first startup:

```text
<Necesse data directory>/settings/bettertorch/settings.cfg
```

Restart the game after changing the file so that the mod reloads the values.

```properties
# Default lightLevel is 300, which is twice the vanilla torch light level
lightLevel=300

# Hue and saturation values control the light color
lightHue=1.0
lightSat=0.0

# EASY, MEDIUM, or HARD
recipeDifficulty=MEDIUM
```

### Setting reference

| Setting | Default | Description |
| --- | --- | --- |
| `lightLevel` | `300` | Brightness/radius value used by the Better Torch. |
| `lightHue` | `1.0` | Hue of the emitted light. |
| `lightSat` | `0.0` | Saturation of the emitted light. The default produces white light. |
| `recipeDifficulty` | `MEDIUM` | Crafting recipe tier: `EASY`, `MEDIUM`, or `HARD`. |

Lines beginning with `#` are comments and are ignored when the file is read.

## Building from Source

### Prerequisites

- A Java 8-compatible JDK
- Necesse installed through Steam
- The Necesse JAR and library files in their expected Steam installation directories

### Configure the game path

The game installation path is declared near the top of `build.gradle`:

```groovy
/* Default configured game installation path */
def gameDirectory = "D:/Steam/steamapps/common/Necesse"
```

Update this path if Necesse is installed elsewhere.

### Build the JAR

On Windows:

```bat
gradlew.bat buildModJar
```

On Linux or macOS:

```bash
./gradlew buildModJar
```

The generated mod JAR will be written to:

```text
build/jar/
```

The output name follows this format:

```text
BetterTorchReloaded-<game-version>-<mod-version>.jar
```

### Run a development client or server

The Gradle project also includes these tasks:

```bat
gradlew.bat runClient
gradlew.bat runDevClient
gradlew.bat runServer
```

`runClient` and `runServer` build the mod JAR before launching their respective processes.

## Project Structure

```text
src/main/java/bolo/bettertorch/
  BetterTorchMod.java       Mod entry point and registry setup
  Config.java               Configuration and recipe definitions
  model/BetterTorchObject.java

src/main/resources/
  items/                    Inventory item texture
  objects/                  ON and OFF object textures
  locale/en.lang            English display names and tooltip text
  preview.png               Workshop preview image
```

## Texture and Localization Contributions

If you would like to improve the mod's visual assets:

- [Better Torch inventory texture](src/main/resources/items/bettertorch.png)
- [Better Torch ON and OFF object textures](src/main/resources/objects)
- [Steam Workshop preview image](src/main/resources/preview.png)
- [English localization](src/main/resources/locale/en.lang)

Pull requests that add or improve textures or localization are welcome. Please keep new assets consistent with the existing art style and Necesse's texture dimensions.

For texture submission help, open a pull request.
