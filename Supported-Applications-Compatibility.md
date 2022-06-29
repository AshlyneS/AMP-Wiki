# Using the Generic Module

Using the [Generic Module](Configuring-the-'Generic'-AMP-module), AMP can be configured to run any application. It's able to handle connecting via RCON or using other admin methods to give you access to the console, track when players join/leave and handle updates and crash recovery.

# Applications with dedicated modules

Dedicated modules allow applications to have additional functionality, for example the Minecraft module has extra features for managing installed plugins.

## List of applications/games supported by AMP and their support on each platform.

ARM64 and AArch64 compatibility are [listed separately](AArch64-%5C-ARM64-Compatibility).

<!--= |Cube World|✅|❌|Only the original Alpha. The Beta does not include a standalone headless server at this time.| !--->

|Application|Windows|Linux|Notes|
|:------|:-----|:-----|:-----|
|7 Days to Die|✅|✅||
|ARK: Survival Evolved|✅|✅||
|ARMA III|✅|✅|No 64 bit version on Linux. RCON/Console unreliable on Linux due to bug in the game server itself.|
|Factorio|✅|✅*|Not supported on CentOS 7, requires a newer version of GlibC. Windows version requires Steam account.|
|FiveM/RedM|✅|✅|Cannot be used with AMP Enterprise licences due to licencing restrictions imposed by the developer.|
|Minecraft Java Edition|✅|✅|Requires Java 8/11/16 (depending on mods used) - Ideally the AdoptOpenJDK packages.|
|Minecraft Bedrock Edition|✅|✅*|Not properly supported on CentOS 7 or Debian 8/9 - Requires a newer version of GlibC<br/>Not supported on Windows Server 2012 R2/Windows 8.1 - Requires Server 2016/newer or Windows 10|
|Rust|✅|✅||
|Space Engineers|✅|❌|Limited configuration at this time|
|Starbound|✅|✅||
|Terraria|✅|✅||
|The Forest|✅|❌||

# Applications running under the 'Generic' module

|Application|Windows|Linux|Notes|
|:------|:-----|:-----|:-----|
|Astroneer|✅|❌|Community contributed configuration|
|Avorion|❌|✅|Community contributed configuration|
|Broke Protokol|❌|✅|Community contributed configuration|
|CoreKeeper|✅|✅|Community contributed configuration|
|Craftopia|✅|✅|Community contributed configuration|
|Conan Exiles|✅|✅|Community contributed configuration. Linux support via Proton.|
|Don't Starve Together|✅|✅|Community contributed configuration|
|Eco|✅|✅|Community contributed configuration|
|HurtWorld|✅|✅|Community contributed configuration|
|Insurgency Sandstorm|✅|✅|Community contributed configuration|
|Kaboom!|❌|✅|AMP Exclusive|
|Killing Floor 2|✅|✅|Community contributed configuration|
|Last Oasis|✅|✅|Additional account required via https://myrealm.lastoasis.gg/|
|Mordhau|✅|✅|Community contributed configuration|
|Pavlov VR|❌|✅|Community contributed configuration|
|Project Zomboid|✅|✅|Community contributed configuration|
|Risk of Rain 2|✅|✅|Community contributed configuration. Linux support via Proton.|
|Satisfactory|✅|✅||
|Squad|✅|✅|Community contributed configuration|
|Starmade|✅|✅|Community contributed configuration|
|Stationeers|✅|✅|Community contributed configuration|
|Sven Co-op|✅|✅|Community contributed configuration|
|The Isle (Legacy)|✅|❌|Community contributed configuration|
|The Isle (EVRIMA)|✅|✅|Community contributed configuration|
|Unturned|✅|✅|Community contributed configuration|
|V Rising|✅|✅|Community contributed configuration|
|Valheim|✅|✅||
|Valheim Plus|✅|✅||
|Wurm Unlimited|✅|✅|Community contributed configuration|
|Xonotic|✅|✅|Community contributed configuration|

# Applications running under the srcds module

|Application|Windows|Linux|Notes|
|:------|:-----|:-----|:-----|
|Alien Swarm|✅|✅||
|Alien Swarm: Reactive Drop|✅|✅||
|Black Mesa|✅|✅||
|Counter-Strike 1.6|✅|✅||
|Counter-Strike Global Offensive|✅|✅||
|Counter-Strike: Condition Zero|✅|✅||
|Counter-Strike: Source|✅|✅||
|Day of Defeat|✅|✅||
|Day of Defeat: Source|✅|✅||
|Deathmatch Classic|✅|✅||
|Dota 2|✅|✅||
|Dystopia|✅|✅||
|E.Y.E|✅|✅||
|Fistful of Frags|✅|✅||
|Garry's Mod|✅|✅||
|Half-Life Deathmatch: Source|✅|✅||
|Half-Life: Opposing Force|✅|✅||
|Insurgency|✅|✅||
|Insurgency 2014|✅|✅||
|Just Cause 2 Multiplayer|✅|✅||
|Left 4 Dead|✅|✅||
|Left 4 Dead 2|✅|✅||
|No more room in hell|✅|✅||
|Nuclear Dawn|✅|✅||
|Ricochet|✅|✅||
|Team Fortress 2|✅|✅||
|Team Fortress Classic|✅|✅||
|The Ship|✅|✅||
|Zombie Panic Source|✅|✅||
