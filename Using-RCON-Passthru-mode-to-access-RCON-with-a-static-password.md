# About Passthru Mode

RCON passthru mode allows you to use a standard RCON client with a fixed password in situations where AMP has taken over a servers standard RCON.

AMP takes control over RCON because it is an insecure protocol with no means of tracking which actions were performed by which user. AMPs passthru mode allows you to know which user performed what actions.

As a side effect, it also allows you to use a standard RCON client to manage game servers that do not have RCON support, or use a different protocol.

# Enabling Passthru Mode

 * Manage the specific instance you want to be able to connect to via RCON
 * Under Configuration -> RCON Passthru, enable the RCON Passthrough setting and verify the IP binding/port you wish for it to use.
 * Restart the AMP instance.
 * Click on your user icon in the top-left
 * Scroll to the bottom and select "Service Login"
 * Enter whatever you'd like as the name of the login request (Something like "RCON Connection")
 * Make a note of the token shown in the advanced details. Copy the entire thing including the username in front.
 * This token is now your RCON password, tied to your account. Connect using your RCON client to the host/port specified using that password. You will now have access to the RCON of the server or AMPs console for applications that don't have this.

# If "RCON Passthru" doesn't show under Configuration 

 * Stop the instance
 * Edit that instances AMPConfig.conf
 * Change the `AMP.LoadPlugins` line to include `RCONPlugin`. Making sure not to remove any existing entries.

```
AMP.LoadPlugins=["FileManager"," EmailSender"," WebRequestPlugin"," LocalFileBackupPlugin", "RCONPlugin"]
```

 * Start the instance back up again, and the menu item will appear.
