## Where does AMP store its data?

On Linux, AMP stores everything in `/home/amp/.ampdata` by default (assuming you used the GetAMP installer and used the default settings) - make sure you are logged in as the amp user - **being logged in as root while editing/moving files will cause damage to your installation.**

On Windows, the datastore location is specified during setup. By default this will be a directory called "AMPDatastore" in the root of one of your drives, usually the one with the most free space. make sure you are logged in as the user AMP was installed as - **being logged in as Administrator while editing/moving files will cause damage to your installation.**

## How do I reset my login information?

This can be done by running `ampinstmgr resetlogin ADS01` on the command line (both Windows and Linux) as your amp user.

Note that this will not reset any per-instance users created within individual instances.

## Can I change the backup location?

Yes! This can be done individually for each instance.

First make sure the new backup location has the same ownership as the instance (such as the `amp` user on Linux). You should also have separate backup locations for each instance (subdirectories are fine), so that backups don’t mix.

Then edit `LocalFileBackupPlugin.kvp` in the instance’s datastore, and change the location in `Storage.StorePath=` so that it points to the full path of the new backup location.

Finally, restart the instance. 