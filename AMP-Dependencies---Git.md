What is Git?
---

Git is a version control system. It's a way for developers to store different versions of source code as they work on a project, and share it with other developers.

Why does AMP need it?
---

### Minecraft Module

AMP needs Git in order to install both Spigot and CraftBukkit. The reason for this is that due to DMCA requests against the developers of Spigot and Craftbukkit - a complete, built version of either Spigot or CraftBukkit cannot be distributed. So anyone that wants to use either must build their own local copy. This requires that you are able to retrieve a copy of the source code for Spigot/CraftBukkit via Git so that it can be built locally. AMP automates this process.

### FiveM Module

FiveM uses Git to distribute certain server files, so AMP uses Git to obtain the necessary data during the update process.

How do I install it?
---

On most Linux distributions, Git is installed as standard by default. If it's not, you can usually install it using your distributions standard package manager. E.g. `apt-get install git` for Debian/Ubuntu-esque distros, or `yum install git` for Fedora/CentOS/Red-Hat based distros.

Under Windows, you should get the 'Git for Windows' binary from [https://git-for-windows.github.io/](https://git-for-windows.github.io/) - during installation it's important that you pick the option to use Git from the windows command prompt:

![Installation options](https://github.com/CubeCoders/AMP/blob/master/WikiContent/git.png)

You can check if Git has been installed properly by opening up a command prompt and typing 'git'. If you get a message that git is not a recognised command then it was not installed correctly.

**After installing Git you must restart AMP for it to be able to use it.**