If you've set up a game server in AMP but are having issues connecting, there are a handful of things you should check.

All of these instructions apply to both Windows and Linux

# Is the application running?

First, check the Status tab for the specific game server instance - and make sure that you have the green light with the text "Application State: Running"

If it's not running, hit start to start the application and check that it remains running.

If the application is running, continue to the next step.

# Is the application listening?

Next we need to check that the application is listening on the ports we're expecting it to.

Open up a command prompt on Windows or a SSH session for Linux servers. Linux users should switch over to the `amp` user by running `sudo su -l amp` first.

Then run `ampinstmgr ports` - and give it the name of the instance you're wanting to check. If you don't know the name of the instance, press CTRL+C to stop and run `ampinstmgr table` to see a list of instances and their names.

If the application is listening (it has a tick at the end of each port) - go to the next section. If not, ask the community for assistance.

# Are the firewall rules correct?

Open up a command prompt on Windows or a *root* SSH session on Linux and run `ampinstmgr dumpfirewall` and check that it lists a firewall rule for each port the application needs. If they're missing - first try simply waiting a few minutes for the sync to complete. Otherwise you can run `ampinstmgr updatefirewall` to sync it immediately.

If no rules are showing up at all, you should ask the community for assistance.

## Linux Users - UFW

If in the output it says "Using UFW Firewall" - run `ufw status` - if it says that it's inactive then this is the source of your problem. AMP is trying to use the UFW firewall but it's not active. UFW either needs enabling, or removing.

# Port Forwarding (Home hosting only)

If you're hosting at home - an excellent step to check where the problem lies is to try and connect to the game server using another device on the same network using your internal IP. If that works, then the game server, firewall and AMP are functioning correctly.

In which case, the problem lies with your port forwarding rules on your router. Check that:

* All of the ports your game requires have been forwarded
* That the correct ports *types* have been forwarded, paying attention to TCP/UDP/Both as per `ampinstmgr ports`
* That the ports are forwarded to the correct IP address (Your internal IP may change from time to time)
