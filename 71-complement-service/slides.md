%title: LINUX
%author: xavki


# LINUX : SYSTEMD - Premier Service


<br>


    /etc/systemd/system: Local configuration
    /run/systemd/system: Runtime configuration
    /lib/systemd/system: Distribution-wide configuration
    /usr/lib/systemd/system/: Contains default systemd unit configurations as per contained in the rpm


```
[Unit]
Description=My app
[Service]
Type=simple
ExecStart=/usr/bin/sleep infinity
[Install]
WantedBy=multi-user.target
```

Description : 


systemctl list-units --type target



systemctl
systemctl list-units
systemctl list-units --type service

systemctl start hello
systemctl status hello
systemctl stop hello
systemctl restart hello


    start Start (activate) one or more units specified on the command line.
    stop Stop (deactivate) one or more units specified on the command line.
    reload Asks all units listed on the command line to reload their configuration.
    restart Restart one or more units specified on the command line. If the units are not running yet, they will be started.
    try-restart Restart one or more units specified on the command line if the units are running. This does nothing if units are not running. Note that, for compatibility with Red Hat init scripts, condrestart is equivalent to this command.
    reload-or-restart Reload one or more units if they support it. If not, restart them instead. If the units are not running yet, they will be started.
    reload-or-try-restart Reload one or more units if they support it. If not, restart them instead. This does nothing if the units are not running. Note that, for compatibility with SysV init scripts, force-reload is equivalent to this command.

```
ExecReload=/usr/bin/bash -c '/usr/bin/touch /tmp/xavki-$$(date +%%Y%%m%%d%%H%%M%%S)'
```

systemctl enable hello
systemctl disable hello


After=dirsrv.target - Will ensure the smb.service is started after dirsrv.target.

For robustness, (which will be worth while if you're tinkering with this stuff) you may also wish to include some of the following:

Requires=dirsrv.target - Activate dirsrv.target when smb.service is activated. Will cause smb.service to fail if dirsrv.target fails.

Wants=dirsrv.target - Activate dirsrv.target when smb.service is activated. Won't cause smb.service to fail if dirsrv.target fails.

BindsTo=dirsrv.target - If dirsrv.target is deactivated, deactivate smb.service.

https://www.golinuxcloud.com/beginners-guide-systemd-tutorial-linux/

https://trstringer.com/Getting-systemd-Unit-Dependencies/
