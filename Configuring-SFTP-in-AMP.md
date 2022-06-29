# As of version 2.0.6.6 - SFTP is enabled in AMP by default and no further setup is required.

All that is required is that you connect with your SFTP client, by default it's on port 2223.

---

As of version 2.0.2.0 - AMP includes an integrated SSH/SCP server, replacing the original 'plain' FTP server from 1.9.1.0. It's not enabled by default. When enabled you will be able to connect with standard SCP clients such as WinSCP or Filezilla using your AMP login details.

Note that like the file manager, there's no fine-grain permissions yet - so users have full access to the instances files when using this. The FTP gives the exact same level of access as the in-browser file manager.

This can be used alongside your systems existing SFTP/SSH daemon without conflits.

**These instructions apply to both Windows and Linux based systems.**

# Basic Setup

To enable it, **stop the instance you want to be able to connect to**, and edit your `FileManagerPlugin.kvp` file. Modify (or if needed add) the following line to read:

```
SFTP.SFTPEnabled=True
```

You can also change the IP/port binding by modifying (or if needed adding) the following lines:

```
SFTP.SFTPPortNumber=2223
SFTP.SFTPIPBinding=0.0.0.0
```

**Linux Users: Linux requires root access for ports below 1024. You must ensure the SFTP port is above this. You cannot use the standard SSH port of 22.**