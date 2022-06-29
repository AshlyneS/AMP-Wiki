# Environment Variables

On Linux, GetAMP supports unattended installations to allow AMP to be automatically provisioned and started without requiring any input.

This is achieved by specifying a number of environment variables that the GetAMP script will pick up when executed.

|Flag|Description|
|-|-|
|USE_ANSWERS|Set to `y` to specify that you'd like to perform an unattended installation|
|ANSWER_AMPUSER|The username to be used for the ADS instance|
|ANSWER_AMPPASS|The password to be used for the above user|
|ANSWER_SYSPASSWORD|The password to be used for the `amp` system user|
|ANSWER_INSTALLJAVA|Set to `y` to specify that you'd like an appropriate Java version to be installed for running Minecraft|
|ANSWER_INSTALLSRCDSLIBS|Set to `y` to specify that you'd like 32-bit C++ libraries and other dependencies of Source Dedicated Servers (and other applications that rely on SteamCMD) to be installed|
|ANSWER_INSTALLDOCKER|Set to `y` to specify that you'd like Docker to be installed and configured, and for AMP to create instances inside containers by default|
|ANSWER_EMAIL|The email address to be used for LetsEncrypt certificate warnings (Optional)|
|SKIP_INSTALL|Set to `y` to install the AMP Instance Manager and dependencies, but do not create the ADS instance or set up a reverse proxy. Useful for Docker scripts|

# Arguments

The GetAMP script accepts a number of arguments to perform individual tasks without performing a full installation, this takes the syntax of:

    bash <(wget -qO- getamp.sh) ARGUMENT

|Argument|Description|
|-|-|
|addRepo|Adds the CubeCoders repository to the system|
|installAMP|Installs `ampinstmgr`, requires that the repository has already been added|
|installDocker|Installs Docker, enables the Docker service, and adds the `amp` user to the `docker` group|
|installJava|Installs Adopt OpenJDK 8 and 11 onto the system|
|installSrcdsDeps|Installs 32-bit dependencies and libraries for games based on the Source engine or that use SteamCMD|t
|postSetupHTTPS|Installs and configures nginx and certbot for use with AMP|
|showSystemInfo|Displays information about the system gathered by GetAMP|
|update|Updates `ampinstmgr` to the latest version, and upgrades all AMP instances to the latest version|
|updateSystem|Applies any pending system updates using the systems package manager|