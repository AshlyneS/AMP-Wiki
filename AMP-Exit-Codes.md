|Code|Meaning|
|----|----|
|-1|Catastrophic Failure|
|0|Unspecified / Configuration Only / Normal Exit|
|16|No Module|
|17|Module Init Failed|
|32|No Licence|
|48|Platform Unsupported By Application|
|49|Environment Not 64Bit (Not in use)|
|50|OS Outdated|
|64|Missing Proc FS|
|65|Missing Prerequisite|
|80|Cannot run as root/admin|
|81|Root/admin required|
|85|User identity mismatch|
|144|Update Requested|
|146|Mandatory Update|
|256|Restart Requested|
|2457|Emergency Shutdown|
|65537|Insufficient Arguments|

GetAMP exit codes
---

|Code|Meaning|
|-|-|
|1|Supplied function parameter does not exist.
|10|Unsupported distribution (neither apt nor yum are present)
|11|Failed to add new 'amp' system user.
|12|Failed to install ampinstmgr.
|19|Failed to configure nginx.
|20|No OS info available, missing /etc/os-release
|30|Non UTF-8 system locale
|40|Root access required
|50|Confirmation password for system password did not match
|60|No AMP login user password was supplied
|64|Unsupported architecture. AMD64/x86_64 and Aarch64 only
|65|Unsupported aarch64 distribution (Ubuntu only)
|70|System user and AMP panel passwords are the same (they must be different)
|80|Confirmation password for panel password did not match
|90|Apache is installed but user selected HTTPS which uses nginx
|91|User specified HTTPS but didn't supply a domain.
|100|Supplied domain does not resolve to external IP of the server.
|110|Failed to create ADS instance via ampinstmgr.
|120|/tmp has noexec flag set.
|130|`useradd` could not be found.
|131|The system package manager is not available due a lock. Other installations are in progress.
|132|`tput` could not be found.
|135|AMP already appears to be fully installed and configured.|

