# Updating your AMP instances

## Windows and Linux

Shared-mode instances on Linux do not need upgrading separately, they update automatically with updates to the instance manager.

ADS can manage instances that are of a similar version, where all parts of the version number are the same except the last. For example ADS version 1.9.6.2 could manage an instance of version 1.9.6.0 or 1.9.6.4, but not of 1.9.7.0.

When you do upgrade instances, do so as the user running AMP (such as `amp` on Linux or `AMP` on Windows). On Linux, switch to the `amp` user by running `sudo su -l amp`.

You can run the following command line (on both platforms) to bulk-upgrade all of your AMP instances:

    ampinstmgr upgradeall

Sometimes you may wish to only update ADS, and then use the web interface to upgrade instances via the right-click context menu:

    ampinstmgr upgrade ADS

**On Windows, it may be necessary to reboot the system after updating AMP.**

# Updating the instance manager

It's not always necessary to upgrade the instance manager with each AMP version (unless using shared instances on Linux). Generally speaking it's only necessary to do this if the release notes for a given version specifically mention changes to the instance manager tools or the local instance manager (LIM)

## Linux

On Linux, The AMP instance manager (ampinstmgr) is updated via your distributions package manager:

### Ubuntu/Debian/deb-based

> [20201031] Reminder for Debian/Ubuntu/Other DEB based distro users, the certificate for the CubeCoders repo was renewed a couple of months ago. If you haven't already, Please run `sudo apt-key adv --fetch-keys https://repo.cubecoders.com/archive.key` (root access required) to fetch the latest key to continue getting updates. If you have already done this, please disregard this and proceed as normal.

    sudo apt update
    sudo apt upgrade

This will update all packages on your system. If you want to only update AMP then replace the second command with:

    sudo apt upgrade ampinstmgr

### CentOS/Fedora/Red Hat/rpm-based

    sudo yum update

This will update all packages on your system. If you want to only update AMP then run:

    sudo yum update ampinstmgr

## Windows

It is not usually necessary to update the Windows instance manager. We advise against doing this unless there is a particular change that affects you.

 * Make sure all instances are fully stopped. You can do this by running `ampinstmgr stopall` in the command prompt
 * Download a [fresh copy of the installer](https://cubecoders.com/Downloads/AMPSetup.msi) and running the setup as an upgrade.
 * **Reboot the system**
