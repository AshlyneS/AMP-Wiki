If you have an existing Minecraft server that you want to manage with AMP, it's trivial to import it along with all of its configuration into a new AMP instance.

## Recommended Method

 * Make a zip of your server, making sure the top level of the zip contains your jar file, `server.properties`, world directories and other data.
 * Make a new Minecraft instance within AMP (or a McMyAdmin3 instance if you are using a legacy McMyAdmin2 licence key with AMP).
 * Manage the new instance and go to the File Manager. This will reveal the contents of the `Minecraft` directory in the instance's datastore.
 * Drag the zip into the File Manager to upload it. Alternatively, upload the zip using [AMP's integrated SFTP server](https://github.com/CubeCoders/AMP/wiki/Configuring-SFTP-in-AMP).
 * Extract the archive in-place (right click in the File Manager). Alternatively, go to the datastore directory for that instance and extract it as the user that AMP is running as.
 * Right click the `server.properties` file and select the 'Import Configuration' option. Note that this option is only available when using the instance's File Manager, not the ADS File Manager.
 * Right click your server's jar file and select the 'Set as startup jar' option.
 * Start the server on the Status tab.

## Other Options

 * In the new instance’s datastore, there will be a file called `MinecraftModule.kvp` containing the configuration data for that module, you can edit the `ServerPath` setting to point to the absolute path on-disk of your existing server. Make sure to check the ownership/permissions to allow the user AMP is running as to have full read/write access.
 * You can symlink the `Minecraft` directory under the new instance’s datastore to your existing directory. Again taking care of permissions.

## Adding Modded Servers

The recommended method above applies equally to adding server modpacks to AMP. However, depending on the modpack, some additional steps may be necessary.
* Make sure that the zipped modpack that you are uploading to AMP is not a zip of a directory containing the modpack files and directories, but rather a direct zip of those files and directories. Otherwise when you extract the zip in AMP it will be installed in a subdirectory of the Minecraft directory, and won't work.
* Some modpacks already include the required server jars and libraries. In that case, you don't need to make any changes to the modpack and can just upload it as outlined in the recommended method above.
* In other cases, you have to run an installer jar directly, or an install script (eg called `Install.bat` for Windows or `Install.sh` for Linux) that runs an installer jar, to download the required server jars and libraries. You can either run this locally (ie before uploading to AMP), or on your server once the modpack is uploaded and extracted. If you run it locally, make sure you install the server jars and libraries alongside the installer jar/script. If running the installer jar directly, select the "Install server" option.
* Often modpacks include a startup script (eg called `ServerStart.bat` for Windows or `ServerStart.sh` for Linux) that has various recommended parameters to start the server. You don't use the script to start the server in AMP, but you can set the same parameters under the Configuration -> Java menu in the instance (the Xmx parameter is set under the Memory Limit, and the other java parameters (those on the command line before the jar) are set under Additional Java Options). Don’t include `java` at the beginning, or `-jar` or anything following it at the end.
* Make sure you select the right startup jar in AMP. For Forge modpacks, there are two jars, a Forge universal jar and the Minecraft jar. Select the Forge universal jar (not the installer jar!).
* Finally, select the appropriate Server Type under the Configuration -> Minecraft menu in the instance. Usually this will be Forge. Don't click Download/Update, as this will replace your server jar with another version, not what the modpack uses.

Note that the above instructions relate to adding server modpacks. Many modpack developers make available both client and server versions of their modpacks. Some however only make available client modpacks. Client modpacks include files that are not required by a server and that in some cases will cause the server to crash. In those cases, you will need to generate your own server version of the modpack by using a launcher app such as ATLauncher, Twitch or Technic, if the modpack is available on those platforms. Otherwise a much more manual process of installing the right Forge jar version for the modpack, and removing client-side only mods from the modpack, will be required.