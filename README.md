# Cyrene Launcher

Play Minecraft: Java Edition on your PS4. Cyrene Launcher lets you install Minecraft versions, create separate game instances, and browse mods and modpacks from Modrinth.

**[Download Cyrene Launcher](https://github.com/CyreneLauncher/CyreneLauncher/releases/latest)** · **[Report a problem](https://github.com/CyreneLauncher/CyreneLauncher/issues)**

This guide covers the current launcher. Older releases may have different menus or fewer features. Available versions and mods do not guarantee that every game or modpack will run correctly on PS4.

## What you need

- A PS4 already set up to install and run homebrew `.pkg` applications.
- Internet access for sign-in, game installation, mods, and runtime downloads.
- A controller for launcher navigation. A keyboard and mouse are useful for Minecraft; controller gameplay depends on the game's controller mod and setup.

The package includes the launcher's Java runtime and graphics libraries. You do not need to compile anything or install Java manually. Minecraft itself is downloaded after you sign in.

## Install and launch

1. Open the [Releases page](https://github.com/CyreneLauncher/CyreneLauncher/releases/latest).
2. Download the **Cyrene Launcher `.pkg`** from the release's **Assets** section. GitHub's **Source code** archives are for developers, not installation.
3. Transfer the package to your PS4 using your usual homebrew package-installation method, then install it with your console's package installer.
4. Open **Cyrene Launcher** from the PS4 home screen.
5. Sign in and create a Minecraft instance using the steps below.

The launcher creates its settings and data folders on first launch. A fresh installation does not include a preinstalled Minecraft game.

### Play without an internet connection

**Add offline account** appears in **Accounts**. Select it, enter a player name (1–16 letters, numbers, or underscores), and accept. The new profile is selected automatically. Choose an already installed instance and press **Play**.

Keep at least one verified Microsoft account saved in the launcher. Signing out your last premium account removes offline profiles; sign in again to create them. Offline profiles have separate player identities, so worlds can give them different inventories and progress from your Microsoft profile.

Offline play supports installed games and single-player worlds. Downloads and first-time setup still need internet access. Servers that verify Minecraft accounts require you to select your Microsoft account instead. To switch profiles, select one in **Accounts**; to remove an offline profile, highlight it, press **Triangle**, and confirm.

## Play and return to the launcher

Select an instance, move to its actions, and choose **Play**. Cyrene checks your account and prepares the game. The application restarts as part of launching Minecraft, so a restart at this point is expected.

After you exit Minecraft, reopen Cyrene Launcher from the PS4 home screen to select another instance or change settings.

Launcher controller navigation and Minecraft controller gameplay are separate. For controller gameplay, install a compatible controller mod for your Minecraft version and configure it in-game. A keyboard and mouse can also be used.

## Install mods

1. Select the instance you want to change.
2. Open **Mods**, then the mod browser.
3. Search Modrinth and open a project to read its description and available versions.
4. Choose **Install** and review the required dependencies and any warnings.
5. Confirm installation, then launch the instance with **Play**.

The browser filters mods for the selected instance's game version and loader. Quilt instances are offered Fabric mods. Vanilla instances do not have a mod browser. Matching the version and loader does not guarantee PS4 compatibility, especially for mods that require additional native libraries. Java agents and mods that require Java instrumentation are not supported by the bundled runtime.

In the installed-mod list, **Cross** enables or disables a mod. **Triangle** removes it after confirmation. Disable a recently added mod first when troubleshooting; you can re-enable it later. Changes apply the next time you press Play.

## Install a modpack

1. Go to **Instances → New instance** and choose the Modrinth modpack option.
2. Search for a pack and open its page.
3. Choose **Create instance** and review its installation summary and warnings.
4. Confirm and wait for installation. The pack is created as a separate instance.
5. Select that instance and choose **Play**.

The installer supports compatible Fabric, Quilt, Forge, and NeoForge packs in the launcher's Minecraft version range. If a pack cannot be installed, check its loader, game version, and the reason shown in the dialog. Large PC modpacks can exceed console memory or depend on unsupported features.

## Memory

Start with the default memory settings. Minecraft memory is used by the game; graphics memory is reserved for textures, shaders, and chunk meshes. The launcher limits their combined allocation to **3072 MiB**. Increasing one can leave less room for the other; maximum values are not a universal performance fix.

## Update Cyrene Launcher

1. Close Minecraft and Cyrene Launcher completely.
2. Back up any worlds and instance folders you want to keep.
3. Download the newer `.pkg` from [Releases](https://github.com/CyreneLauncher/CyreneLauncher/releases/latest).
4. Install it over the existing Cyrene Launcher application using your normal package installer.
5. Reopen the launcher and check your accounts and instances.

Updates use the same application identity and preserve existing settings and game data. Keep `/data/orbis-jdk` intact. Install the full launcher package to update its bundled components; you do not need to replace individual graphics libraries.

Java 21 and 25 runtimes are checked for updates when needed. An installed runtime is retained if its update check fails; first-time installation still needs internet access. Microsoft sign-in and online play have their own connection requirements. Interrupted Minecraft, mod/modpack, and Java runtime downloads keep partial data. Retry the same operation to resume where the server supports it; servers without resume support start that file again. Already verified files are reused, and a checksum mismatch discards the incomplete file before another attempt.

## Back up your worlds

Close the application before copying files with your console's file manager or FTP setup. Managed instances live under:

```text
/data/orbis-jdk/launcher/instances/<instance-id>/game/
```

The instance ID is an internal folder name, not necessarily the displayed name. Inside its game folder:

| Folder | Contents |
| --- | --- |
| `saves/` | Single-player worlds |
| `mods/` | Installed mods |
| `config/` | Mod configuration |
| `logs/` | Minecraft logs |
| `crash-reports/` | Minecraft crash reports, when generated |

Copy the whole instance folder to preserve its setup, or at least `saves/` to preserve worlds. Imported installations keep their existing game location. Account credentials are stored separately; do not include them in bug reports or shared backups.

### Report a problem

Open an [issue](https://github.com/Rerence1016/CyreneLauncher/issues) and include:

- Cyrene Launcher package version.
- PS4 model (base, Slim, or Pro), firmware, and homebrew environment.
- Minecraft version, loader, and modpack or relevant mods.
- What you did, what you expected, and what happened instead.
- The exact error message and relevant logs.

Useful logs are:

```text
/data/orbis-jdk/launcher/launcher.log
/data/orbis-jdk/logs/orbis-runner.log
/data/orbis-jdk/launcher/instances/<instance-id>/game/logs/latest.log
/data/orbis-jdk/launcher/instances/<instance-id>/game/crash-reports/
```

Share logs as text where possible. Remove personal information or tokens before posting, and never upload the launcher's account-credentials folder.