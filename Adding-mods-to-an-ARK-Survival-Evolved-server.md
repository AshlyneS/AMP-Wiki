<!---
{
    "Tags": ["CommunityContributed", "ARK"],
    "ModuleSpecific": "ARK",
    "Author": "Greenlan",
}
-->

### _This page was contributed by a member of the AMP community_

**Note: Before doing any of the below instructions, your ARK:SE server must be started at least once. So, after creating the ARK:SE instance in AMP, manage the instance and click Update to install the ARK:SE server. Then click Start, wait until the server is running, and then stop it.**

# Linux

Currently some manual intervention is required to install mods on ARK:SE servers on Linux. There are two options: manually upload mods to the server, or manually adjust the server files so that mods are able to be automatically downloaded by the server.

## Option 1 - Manual upload approach

While it is possible to download Steam workshop items, including mods, on Linux servers via AMP (via Configuration->Steam Workshop), steamcmd does not install them in the correct directory, and therefore they need to be manually moved. In addition, in the case of ARK:SE servers, the required `.mod` file is not created at all when this method is used.

As a result, to manually upload mods to an ARK:SE server on Linux:

1. Install the mod on your client and run the client. 
2. Upload the resulting mod directory and associated `.mod` file to the server. Place them in the `arkSE/376030/ShooterGame/Content/Mods` directory. Use AMP’s File Manager or in-built SFTP to do this, to ensure correct permissions on the directory and file.
3. To activate the mod for the server, either:
* add `GameModIds` as a Custom Setting key for the ARK instance under Configuration->Server, with comma-separated numbers for the mods as the value (no spaces - for example, `731604991,680481868`); OR
* add `ActiveMods=` with comma-separated numbers for the mods in `arkSE/376030/ShooterGame/Saved/Config/LinuxServer/GameUserSettings.ini`, in the `[ServerSettings]` section. For example, `ActiveMods=731604991,680481868`

## Option 2 - Automatic download approach

ARK:SE comes with a launch parameter option that is meant to automate the process of downloading, installing and updating mods. Unfortunately it does not work on Linux systems without manual intervention.

**Warning: This option does not appear to work correctly if the ARK:SE instance is run in a Docker container.**

To use this option:
1. **Run the following commands on the command line as the `amp` user.** If you are not already the `amp` user, first run `sudo su -l amp` to switch. Also, substitute `ARK01` in the first line with your ARK instance name as shown in `~/.ampdata/instances/` (NOT the “friendly name”):
```
INSTANCE=ARK01
LINUXDIR=~/.ampdata/instances/${INSTANCE}/arkSE/376030/Engine/Binaries/ThirdParty/SteamCMD/Linux/
mkdir -m 700 ${LINUXDIR}
ln -s ~/.ampdata/instances/${INSTANCE}/arkSE/steamcmd.sh ~/.ampdata/instances/${INSTANCE}/arkSE/linux32 ~/Steam/steamapps ${LINUXDIR}
```
2. Add `-automanagedmods` as a Custom Flag for the ARK instance under Configuration->Server.
3. In `arkSE/376030/ShooterGame/Saved/Config/LinuxServer/Game.ini`, add a `[ModInstaller]` section with each mod listed on a separate line, for example:
```
[ModInstaller]
ModIDS=731604991
ModIDS=680481868
```
4. Follow Step 3 in the "Manual upload approach" above to activate the mods for the server.

Note: You only need to do Steps 1 and 2 above once for your server.


# Windows

Like for Linux, there are two options for ARK:SE servers on Windows: configure the server to automatically download mods, or manually upload mods to the server.

## Option 1 - Recommended approach (automatic download)

On Windows servers, the ARK:SE launch parameter option that is meant to automate the process of downloading, installing and updating mods works, without the need for manual intervention. 

To use this option:
1. Add `-automanagedmods` as a Custom Flag for the ARK instance under Configuration->Server.
2. In `arkSE\376030\ShooterGame\Saved\Config\WindowsServer\Game.ini`, add a `[ModInstaller]` section with each mod listed on a separate line, for example:
```
[ModInstaller]
ModIDS=731604991
ModIDS=680481868
```
3. To activate the mod for the server, either:
* add `GameModIds` as a Custom Setting key for the ARK instance under Configuration->Server, with comma-separated numbers for the mods as the value (no spaces - for example, `731604991,680481868`); OR
* add `ActiveMods=` with comma-separated numbers for the mods in `arkSE\376030\ShooterGame\Saved\Config\WindowsServer\GameUserSettings.ini`, in the `[ServerSettings]` section. For example, `ActiveMods=731604991,680481868`

## Option 2 - Alternative approach (manual upload)

If the recommended approach above does not work, a more manual process can be used:

1. Install the mod on your client and run the client. 
2. Upload the resulting mod directory and associated `.mod` file to the server. Place them in the `arkSE\376030\ShooterGame\Content\Mods` directory. Use AMP’s File Manager or in-built SFTP to do this, to ensure correct permissions on the directory and file.
3. Follow Step 3 in the "Recommended approach" above to activate the mods for the server.