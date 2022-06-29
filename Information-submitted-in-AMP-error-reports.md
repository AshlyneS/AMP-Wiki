When AMP experiences an error from which it cannot recover and can no longer continue, then if permitted AMP may submit an automated error report to CubeCoders for analysis to help us track down the issue and prevent it from happening in future versions.

In this event, the following data may be securely sent to CubeCoders (this is an exhaustive list):

* A unique, random ID for the crash report.
* The type of Operating System (Windows/Linux).
* The system architecture (x86_64/aarch64).
* The full platform name (E.g. Windows Server 2016 Standard, Debian GNU/Linux 8 (jessie))
* What type of virtualization is being used if any (E.g. HyperV, KVM, VMware ESX, etc)
* Which application module is loaded by AMP (E.g. ADSModule, MinecraftModule)
* A list of AMP Plugins that are loaded (E.g. LocalFileBackupPlugin, FileManagerPlugin, steamcmdplugin)
* The exception message (e.g. System.InvalidOperationException)
* The stack trace, which shows which functions AMP was executing (and where those function calls came from) at the time of the incident.

If AMP is not the latest version as of when it was most recently started, it will not submit crash/error reports. It will submit crash reports at a maximum rate of once per hour.

Crash reports are not associated with the user that submitted the report. They are always anonymous.