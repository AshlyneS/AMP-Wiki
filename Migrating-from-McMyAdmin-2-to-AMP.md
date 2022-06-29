While AMP is an entirely different product to McMyAdmin, it does provide an upgrade path for users currently on McMyAdmin 2 who wish to keep up to date. There are a few important differences that users will need to be aware of before migrating. If you are considering moving you should carefully examine this guide before continuing.

For new users, it is *strongly* recommended that you install AMP rather than McMyAdmin.

# Licencing

## McMyAdmin Personal Users

As of time of writing there is no free licence tier for users previously on McMyAdmin Personal. The upgrade path for Personal Edition users is to upgrade to AMP Professional.

## McMyAdmin Professional Users

Users with an McMyAdmin 2 Professional licence may use it in AMP. However these licences are restricted such that they can only be used for running Minecraft servers.

Within AMP there is a 'McMyAdmin' module. This is actually simply an alias of the standard 'Minecraft' module but allows the use of McMyAdmin 2 licence keys. There's no difference in behaviour or functionality other than this.

## McMyAdmin Enterprise Users

AMP will accept McMyAdmin 2 Enterprise keys as if they were AMP Enterprise keys and allows all commercial usage functionality.

# System Requirements

By and large AMP has fairly modest system requirements similar to McMyAdmin 2, however there are some caveats:

 * AMP only runs on 64 bit x86 (AMD/Intel) and aarch64 systems. It has zero support for 32 bit systems.
 * AMP does not support Mac OS or BSD based operating systems. It runs on Windows 8.1/Windows 2012 R2 or newer (Windows 7 is not supported!), or any reasonably modern Linux distribution (Ubuntu 18.04+, CentOS 7, Debian 8+, etc). The recommended migration path for Mac OS/BSD users is to run AMP inside a virtual machine or docker container.

# Security

AMP very strictly enforces certain security rules to try and ensure that it does not become a vector for attacks. These rules cannot be disabled and there will never be any way to do so.

 * AMP will not run as root/Administrator or any user that has direct root/admin rights. On Linux it may run as a user with `sudo` access so long as the password is prompted for, on Windows it may run as user that is a member of the Administrators group so long as UAC is enabled. AMP checks this on startup and will refuse to start if these test fail.
 * With regards to the above, this still applies if running inside a Docker/LXC/Similar container. You must create a non-root user within that container.
 * AMP Enterprise requires that `hidepid` is enabled to prevent information leakage across processes belonging to different users. See [Configuring 'hidepid' for Linux systems](Configuring-'hidepid'-for-Linux-systems)

Be careful when handling AMPs datastore directly. One of the most common errors made during the migration process is accidentally touching a file that AMP uses while logged in as a user with root/admin permissions. If you do this, AMP or the game server its managing will not be able to read from/write to that file any more and may not work correctly.

# Creating Instances

Unlike McMyAdmin, AMP is designed to control multiple game servers at once. So once AMP itself is installed (either via the package manager or the installer) you'll need to create a game instances. See the [Installation Guide](https://cubecoders.com/AMPInstall) for more details on getting started.

If you are migrating from McMyAdmin 2 to AMP for an existing server, it's strongly recommended you stop the old server first so that any ports it was previously using are not occupied.

# Moving your data over

See [How to import an existing Minecraft server into AMP](How-to-import-an-existing-Minecraft-server-into-AMP) - this procedure applies for MCMA2 migrations as well as new installations.

# Server Types

AMP has built in support for a wider array of Minecraft server mods than McMyAdmin 2 does. You should check first if either of these are compatible with your existing server before trying to use Custom (aka Snowflake) mode.