%title: LINUX
%author: xavki


# LINUX : SYSTEMD - Types de Services


<br>

```
man systemd.service
```

Types :

	* simple : daemon d'un simple process (classique)

	* oneshot : pour lancer une fois (exemple au démarrage), reste en attente

	* forking : l'ExecStart doit utiliser le syscall fork()

	* dbus

	* notify

	* idle

	* exec

<br>

* OneShot

```
[Unit]
Description=My Hello app
[Service]
Type=oneshot
ExecStart=/usr/bin/sleep 10
RemainAfterExit=true
[Install]
WantedBy=multi-user.target
```

Note : RemainAfterExit permet de conserver le service actif après la fin du process

After=dirsrv.target - Will ensure the smb.service is started after dirsrv.target.

For robustness, (which will be worth while if you're tinkering with this stuff) you may also wish to include some of the following:

Requires=dirsrv.target - Activate dirsrv.target when smb.service is activated. Will cause smb.service to fail if dirsrv.target fails.

Wants=dirsrv.target - Activate dirsrv.target when smb.service is activated. Won't cause smb.service to fail if dirsrv.target fails.

BindsTo=dirsrv.target - If dirsrv.target is deactivated, deactivate smb.service.

https://www.golinuxcloud.com/beginners-guide-systemd-tutorial-linux/

https://trstringer.com/Getting-systemd-Unit-Dependencies/
