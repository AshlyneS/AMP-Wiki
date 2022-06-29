If you need to relocate the AMP datastore, the best way to do this on both platforms is using a symbolic link.

## Linux

1. As root or sudoer, make a new directory (call it whatever you want) for the datastore or instance(s) in the new /PATH. This could be for example in `/mnt` or `/srv`, or wherever you want the datastore or instance(s) to be moved to. The `amp` user must have access to /PATH, although it does not need to be the owner - `755` permissions are sufficient.

   In the commands below, substitute the full path for `/PATH`:
```
sudo mkdir -p /PATH/amp
sudo chown amp. /PATH/amp
sudo chmod 775 /PATH/amp
```
2. Switch to the `amp` user and stop AMP:
```
sudo su -l amp
ampinstmgr -o
```

3. Still as the `amp` user, move the existing data and then symlink it back to its original location:
```
mv /home/amp/.ampdata /PATH/amp/
ln -s /PATH/amp/.ampdata /home/amp/.ampdata
```

## Windows

Todo: Using `mklink`

Alternatively on Windows, you can edit the `InstanceStore` field in the `HKEY_LOCAL_MACHINE/SOFTWARE/CubeCoders/AMP/InstanceManager` registry entry. You'll also need to edit the Instances.json file (while all AMP instances are stopped!) to update the locations. If you are running an instance as a Windows Service you will have to reinstall the service.