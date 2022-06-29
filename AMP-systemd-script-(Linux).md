AMP has two systemd units that allow it to perform various tasks automatically.

You can find copies of these systemd units at https://github.com/CubeCoders/AMP/tree/master/systemd

`ampinstmgr.service`
---

This unit starts/stops any instances with the 'start on boot' flag set as your system boots or shuts down. **It runs `ampinstmgr startboot` or `ampinstmgr stopall` using the `amp` system user**.

This unit is enabled automatically when you install AMP using either GetAMP or by installing from the deb/rpm repository.

You can enable this service by running:

    systemctl enable ampinstmgr.service

And disable it via:

    systemctl disable ampinstmgr.service

Running `systemctl restart ampinstmgr.service` will re-start any boot time instances that are not currently running.

`ampfirewall.timer`
---

This unit is used by AMP to automatically apply new firewall rules for your AMP instances as you create them. **It runs `ampinstmgr --silent updatefirewall amp` as the `root` user every 5 minutes**. It only considers instances owned by the `amp` system user.

This unit is enabled automatically when you install AMP using GetAMP, but is not enabled by default when using the deb/rpm repository.

You can enable this service by running:

    systemctl enable ampfirewall.timer
    systemctl start ampfirewall.timer

And disable it via:

    systemctl stop ampfirewall.timer
    systemctl disable ampfirewall.timer

`ampfirewall.service`
---

This unit is used by AMP to automatically apply firewall rules for your AMP instances during boot. **It runs `ampinstmgr --silent updatefirewall amp` as the `root` user**. It only considers instances owned by the `amp` system user.

This unit is enabled automatically when you install AMP using GetAMP, but is not enabled by default when using the deb/rpm repository.

You can enable this service by running:

    systemctl enable ampfirewall.service

And disable it via:

    systemctl stop ampfirewall.service
