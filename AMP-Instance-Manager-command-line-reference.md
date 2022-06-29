Syntax
---

    ampinstmgr [Flags] [Operation] [Arguments] (Optional Arguments)

Available Flags
---

* --nocache       : When creating/updating instances, do not use an existing cached copy of AMP
* --advanced      : Show advanced operations when using the help command
* --shared        : (Linux Only, Experimental Feature) When creating instances, created as 'shared' instances that lack their own copy of AMP. Saves disk space, but means that all instances are always the latest version as included in the main AMP package.
* -version        : Display the version and exit
* --sync-certs    : (Linux Only) sync against the system certificate store. Normally performed automatically.
* --log-sensitive : Include sensitive arguments (passwords, etc) in the main log. Use with care.
* --docker        : (Linux Only) When creating instances, create inside Docker containers (requires that your AMP user is a member of the 'docker' group)
* --strict        : Errors out if a parameter is missing. For use in non-interactive scripts.

Specifying Provision Settings
---

Commands such as `createinstance` and `reconfiguremultiple` will accept provisioning settings. These will apply any settings to the affected AMP instances. They take the format of `+Area.Setting.Key Value` - for example, 

    ampinstmgr reconfiguremultiple * +Core.Login.AuthServerURL http://localhost:8080

Available Operations (The -- is optional)
---

```
 --BrowseInstance [Instance Name]
   Browse to an instance

 --ChangeInstanceStream [Instance Name] [Release Stream] (Force)
   Switch an instance to a different release stream

 --CreateInstance, -c [Module] [Instance Name] [IP Binding] [Port Number] [Licence Key] [Admin Username] [Admin Password] [Provision Settings]
   Create a new standalone AMP instance

 --DeleteInstance, -d [Instance Name] (Skip Verification)
   Delete an existing AMP instance

 --Help, -? (Command)
   Display Help

 --LastLog [Instance Name]
   View the most recent log file for a given AMP instance

 --QuickStart, -quick [Username] [Password] (IP Binding) (Port) (Provision Settings)
   Create an ADS instance

 --RebindInstance [Instance Name] [IP Binding] [Port Number]
   Change the IP/Port binding of an existing AMP instance

 --ReconfigureInstance [Instance Name] [Provision Settings]
   Reconfigure an AMP instance

 --ResetLogin, -e [Instance Name] [Username] [Password]
   Reset a standalone instances login details

 --RestartAllInstances (Instances) (Delay)
   Restart all AMP instances

 --RestartInstance, -r [Instance Name]
   Restart a running AMP instance. If the instance is already stopped it will be started.

 --SetStartBoot, -x [Instance Name]
   Toggle boot-time flag

 --ShowAllInstancePorts
   Show port usage for all instances

 --ShowInstanceInfo, -i [Instance Name]
   Show the information for a given instance.

 --ShowInstancePorts [Instance Name]
   Show port usage by a specific instance

 --ShowInstancesList, -l
   Print the information for current instances as a list.

 --ShowInstancesTable, -t
   Show a table of current instances.

 --ShowModuleList, -m
   Display a list of available modules

 --StartAllInstances, -a (Instances) (Delay)
   Start all AMP instances. Delay is in milliseconds between instances to wait before moving onto the next.

 --StartBoot, -b (Delay)
   Start boot-time AMP instances. Delay is in milliseconds between instances to wait before moving onto the next.

 --StartInstance, -s [Instance Name]
   Start an existing AMP instance

 --StopAllInstances, -o (Instances)
   Stop all running AMP instances

 --StopInstance, -q [Instance Name]
   Stop a running AMP instance

 --UpgradeAll, -p (Restart Running Instances) (Mainline Instances Only)
   Upgrade all AMP instances. If Restart Running Instances is True, then any running instances will be automatically be restart (default behaviour). If Mainline Instances Only is 'True' then only instances whose current release stream is set to Mainline will be upgraded.

 --UpgradeInstance, -u [Instance Name]
   Upgrade an existing AMP instance in-place

 --Version
   Display the version

 --View [Instance Name] (Force)
   View the console of a running AMP instance. A Force value of 'True' will attempt to attach to the console of an instance even if it doesn't look like it's running.
```