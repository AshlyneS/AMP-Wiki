What is hidepid?
---

"hidepid" is a setting applied to the /proc filesystem - it prevents users from being able to see information about processes that do not belong to them (with the exception of the root user, which can always see other users processes)

This prevents information leakage in the case where sensitive information (such as passwords) are included in command line arguments for running executables, as that information remains available so long as it is running and by default is accessible by all users.

AMP requires this to be in use for all Enterprise deployments as a security precaution. This check cannot be sidestepped or disabled.

How do you enable it?
---
You can enable hidepid immediately by running the following as root:

    mount -o remount,rw,hidepid=2 /proc

To make this effect permanent and persist across a reboot, edit the proc line of `/etc/fstab` with your text-editor of choice. 

    proc    /proc    proc    defaults,hidepid=2     0     0

If this line does not exist, you should add it to the end of the file.