Some server applications (especially those that don't ship separately from their base game) require that you authenticate with Steam in order to download them. This is just the same as logging in using the steam client to download games that you've purchased.

AMP downloads most applications via [SteamCMD](https://developer.valvesoftware.com/wiki/SteamCMD) - which is an official, command line version of the steam client provided by VALVe software. Normally no login is required, but for some applications it is - and in this case AMP will ask you for a set of login details that it will forward to SteamCMD.

## Will AMP store my login details?

AMP itself does not store the login details you provide, it simply sends them straight through to SteamCMD which itself will store a token to remember your login same as the desktop application. Your username, password and steam guard tokens are never stored or logged by AMP itself.

## Why am I being asked for a Steam Guard code?

Logins via SteamCMD are subject to the same restrictions as logging in via the desktop application, so if you have Steam Guard enabled on your account you will need to provide a Steam Guard code for SteamCMD to be able to login and start downloads.

## I'm worried about letting another application see my steam account login details, are there any other options?

If you're concerned you can set up a secondary steam account that's just for use with hosting - but you will need to re-purchase any applications that require purchase before they allow use of the server.