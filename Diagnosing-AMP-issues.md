Most issues with AMP are usually caused by minor configuration issues that can be easily solved.

# Diagnosing application startup issues

AMP can produce startup scripts equivalent to what it's trying to start to let you start applications from outside of AMP to view any extra console output and to reproduce behaviour outside of AMP.

Stop the instance, and then in AMPConfig.conf for your instance turn on both `Monitoring.ProduceStartupScripts` and `Security.LogSensitiveProcArgs`.

With these turned on, whenever AMP starts another process - it'll generate a file in its datastore directory with the name of the executable and a timestamp. This will be a .bat file on Windows and a .sh file on Linux. You can run this (**make sure you do this as your AMP user and not as a different user!**) to run the program in the exact same way AMP would with the same arguments and startup environment.

# Diagnosing issues with AMP itself

**DO NOT** attempt to uninstall/reinstall AMP. AMP cannot be 'fixed' by reinstalling it, and by doing so you will destroy any information that would help you solve the issue.

## Web interface issues after updating

If you've just updated AMP and the web interface no longer works or throws an error when you visit it, press CTRL+F5 to reload the page without using the cache. This will fix most in-browser issues.

## Debug Logging
Enable AMPs 'Debug Logging' mode to obtain additional information about what it's doing to aid in diagnostics.
In AMPConfig.conf you will find a setting called `Monitoring.LogLevel` - change it's value to `0` to enable debug logging.

With that done, check AMPs most recent log file. Every AMP instance creates a log file as soon as it starts up. This can be found in the AMP_LOGS directory for that specific instance in the datastore. Under Linux the default datastore directory is `/home/amp/.ampdata/instances`, under Windows you can right click on an instance in the Instance Manager and hit 'browse datastore'. The log files are ordered by date and time, so make sure you're picking the most recent.

Skip to the end of the log file. If AMP knows exactly what went wrong then it'll show you a diagnostics message, explaining what the problem is and possibly how to fix it.

If it is not clear what the problem is, upload a copy of the most recent log to a paste service like hastebin.net/pastebin.net, and post a link to the log to either the support board, or to Discord - making sure to include the following:
  * What OS you're using
  * What version of AMP you're using (*Do not* say 'Latest', always check the actual version - it's shown in the log)
  * What you're trying to do
  * What actually happens (*Do not* say 'Nothing', always be brutally specific)
