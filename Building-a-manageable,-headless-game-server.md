# A guide for game developers and publishers.

This document is a series of short bullet-point issues that game developers and publishes should consider when shipping standalone dedicated servers to ensure that they can be easily managed.

## Set up experience

 * If not being shipped via Steam, the latest version of the server should be attainable from a fixed, static URL - or at least a highly predicable URL that can be derived from the version. E.g. https://example.com/mygame/server/win64/server-v1234.zip
 * Version numbers should ideally be of a manner that can be easily comparable by software, avoiding random text tags.
 * If being shipped via Steam, the server should ideally be a separate repo/product ID so that it can be set up without authentication.
 * Data about the currently available version(s) should be made available in a machine readable format. Ideally JSON or similar. A running server should also expose its current version.
 * Neither of the above should be behind any actions that require manual human interaction (such as Cloudflare challenges)
 * Binaries should be available for both Windows and Linux, and ideally ship with a sample batch/shell script that can start a minimally functional server as-is.
 * On Linux, you should publish a formal list of dependencies, and ideally stick to those that come as standard with modern distros or those commonly used on servers. Avoid requiring use of a custom LD_LIBRARY_PATH if possible by statically linking any libraries as this can be a security hazard.

## Configuring the server

 * All aspects of the servers networking should be configurable, including IP bindings and port numbers. Any built in remote-administration (RCON, etc - see 'Management') should have the option to use a different IP/port binding from the game itself.
 * The log file location should be configurable. The log implementation should be tested to verify it can write to named pipes/fifo streams.
 * Command line flags should be able to change the value of any setting, and take precedent over those found in any config file(s).
 * Config files should be human and machine readable/writable, using an appropriate format. XML for example is not suitable for basic key/value pairings. JSON isn't too bad, but a simple Key=Value settings file is ideal.
 * If possible the server should have an option to re-load its config file at runtime.
 * Avoid mixing critical settings (networking settings, player limits) with gameplay settings in the same file. Use multiple config files if necessary.

## Running/Managing the server

 * The server must be able to operate headless with zero graphical output.
 * The server should write its log to standard output if possible. Avoid direct console buffer writes (especially on Windows!) - if this is unavoidable then a robust remote management system is critical. If possible it should also read commands from standard input.
 * Implementing a standard/common remote administration protocol is essential. Source RCON is well documented, and widely supported. Log output should be piped out to connected remote admin clients (in the case of Source RCON, you can send packets out with an ID of 0) Careful with line ending differences. Recommending accepting \n and ignoring any \r characters.
 * Log output should be in a consistent format regardless of the message so that it can be parsed reliably.
 * Server should log as a minimum:
   * Once startup has completed, including information on listening sockets.
   * When any user joins/leaves - including their name, account ID, and IP address.
   * When any chat message is sent by a user.
   * When any action is performed via remote admin.
 * Basic commands should be included for:
   * Kicking/banning users by name/id/ip
   * Chatting with users
   * Displaying a prevalent 'banner' to all users.
   * Stopping the server