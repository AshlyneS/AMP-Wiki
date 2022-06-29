Web interface doesn't load remotely on CentOS despite firewall rules
-

The exact cause of this issue isn't entirely known, but appears to be down to an issue with the CentOS Firewall.
Running the following as root appears to alleviate the issue:

```
yum update
wget dl.fedoraproject.org/pub/epel/7/x86_64/Packages/e/epel-release-7-11.noarch.rpm
rpm -ihv epel-release-7-11.noarch.rpm
yum install iptables-services
yum -y reinstall "*"
sync
reboot
```

**Do not skip the reboot!**
