### _This page was contributed by a member of the AMP community_

On a standard AMP installation, there is one ADS instance that is the "Auth Server" - that is, it provides login authentication for all managed instances, both local and remote.

On a Standalone installation, that is the local ADS instance. On a Target installation, that is the Controller ADS.

If the IP or port of the Auth Server ADS is changed (eg if the ADS's port is changed using the `ampinstmgr rebind` command), then AMP's configuration needs to be updated.

## Updating existing instances

The configuration of existing instances can be updated either:
* manually by editing `instances.json` and each instance's `AMPConfig.conf` (do this as the relevant AMP user, eg `amp` on Linux or `AMP` on Windows, and while the ADS and the other instances are stopped); or
* preferably, by using the command line (in the case of Docker instances, manual updating may be required, particularly if you are not using host networking). You can use the command line to update instances individually, or all at once.

### Updating an individual instance

The following commands should be run as the relevant AMP user, eg `amp` on Linux or `AMP` on Windows.

To change one instance's configuration on the command line, first stop ADS and the relevant instance (using `ampinstmgr stop ADS` and `ampinstmgr stop INSTANCENAME`, substituting INSTANCENAME as appropriate). Then use the following:
```
ampinstmgr reconfigure INSTANCENAME +Core.Login.AuthServerURL http://ADS_IP:ADS_PORT
```
Substitute the relevant INSTANCENAME, ADS_IP and ADS_PORT as appropriate. For Standalone instances, and for local instances on a Hybrid installation, use `localhost` as the ADS_IP (except if those instances are in Docker and not using host networking). **Note that `0.0.0.0` is not a valid IP.**

If you are using AMP's internal HTTPS (rather than HTTPS through a reverse proxy), the URL should be `https://ADS_DOMAIN:ADS_PORT` (substituting ADS_DOMAIN and ADS_PORT as appropriate).

### Updating all instances

The following commands should be run as the relevant AMP user, eg `amp` on Linux or `AMP` on Windows.

To change all local instances at once on the command line, first stop the ADS and all other instances (using `ampinstmgr stopall`). Then use the following:
```
ampinstmgr reconfiguremultiple "*" +Core.Login.AuthServerURL http://ADS_IP:ADS_PORT
```
Substitute the relevant INSTANCENAME, ADS_IP and ADS_PORT as appropriate. Again, for Standalone instances, and for local instances on a Hybrid installation, use `localhost` as the ADS_IP (except if those instances are in Docker and not using host networking). **Note that `0.0.0.0` is not a valid IP.**

If you are using AMP's internal HTTPS (rather than HTTPS through a reverse proxy), the URL should be `https://ADS_DOMAIN:ADS_PORT` (substituting ADS_DOMAIN and ADS_PORT as appropriate).

## Updating new instances

For instances to be created in the future, update the "Default auth server" setting in the Configuration->New Instance Defaults menu for the ADS. This should match what is used for existing instances as per the above.