**Note: While this feature is currently available globally, in the future it will be restricted to AMP Network and Enterprise editions only.**

Deployment overlays allow you to configure AMP to automatically add files to the root of newly created AMP instances. These can either apply globally to all instances or can be module specific.

Overlay archives are extracted into the root of the actual instance directory rather than the application directory, so you can add files/folders that aren't specific to the game/application itself.

To enable this feature, add/edit these two lines in ADSModule.kvp (this will also need doing on remote targets)

```
Defaults.UseOverlays=true
Defaults.OverlayPath=/opt/cubecoders/amp/shared/overlays
```

You can also edit these settings via Configuration -> New Instance Defaults in ADS.

On Linux systems it's strongly advised you keep the existing overlay path, on Windows you will need to change this to a local directory containing the overlay archives.

The two archives that are checked for are: `overlay-common.zip` which is extracted over the top of all new instances, and `overlay-MODULENAME.zip` where `MODULENAME` is replaced with the lower-case name of the module that instance is using. For example `overlay-minecraft.zip` or `overlay-srcds.zip`.