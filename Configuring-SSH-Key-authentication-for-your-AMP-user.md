This tutorial assumes you're on a Windows computer with the PuTTY SSH client installed, connecting to a Linux server running AMP, and it assumes you correctly followed the AMP install guide and have a Linux system user called AMP.

* Open up PuTTYgen (PuTTY Key Generator)
* Click `Generate`
* Move your mouse for a moment over the blank area
* Click "Save private key", click "Yes" when asked to save the file without a passphrase and save the file somewhere you can find it
* **Be warned, this file must be kept safe - anyone who can access it can access your server!**
* Open up an SSH session to your server, and login as the AMP user. If you cannot login as the AMP user then login as root and run `su -l AMP` 
* Run the following commands:

```cd ~/
mkdir .ssh
chmod 700 .ssh
cd .ssh
touch authorized_keys
chmod 600 authorized_keys
cat > authorized_keys
```

* In PuTTYGen, select the public key (right click -> select all)
* Select the PuTTY window to your server and right click once in the window (this will paste your public key)
* Press CTRL+D and you'll be returned to the prompt
* Close your SSH session
* Re-open PuTTY, and under Connection -> SSH -> Auth, pick "Private key file for authentication" and select the key file that was saved earlier from PuTTY gen
* You should connect immedaiately