%title: LINUX
%author: xavki


# LINUX : SYSTEMD - Gestion de l'environnement


<br>

```
man systemd.service
```

Objectif : 

* gérées par le [System]

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Gestion de l'environnement

<br>

* WorkingDirectory

```
echo "Test WorkingDirectory" > /tmp/xavki.txt
```

```
[Service]
Type=simple
WorkingDirectory=/tmp/
ExecStart=/usr/bin/cat xavki.txt
```

Note : ne fonctionne pour le chemin (path) vers le script

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Gestion de l'environnement

<br>

* les permissions sur les répertoires :

```
[Service]
Type=simple
ExecStart=/usr/bin/ls /home/oki
InaccessibleDirectories=/home
```
ReadWriteDirectories=
ReadOnlyDirectories=

Note : ajouter "-" pour éviter une erreur si non existant

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Gestion de l'environnement

<br>

* protection de la home (true/false/read-only)

ProtectHome > /home/ ou /run/user/ non accesible

* ProtectSystem (true/false/full) :

ProtectSystem > /usr/ en read-only
		* si full, /etc/ aussi 




----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Gestion de l'environnement

<br>

* le répertoire temporaire privé (True/False)


```
[Service]
Type=simple
ExecStart=/bin/bash -c "echo toto > /tmp/xavki.txt"
PrivateTmp=True
```

Note :
	* pour la sécurité, suppression /tmp/ & /var/tmp/ du process
	* idem pour les networks & pour les devices

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Gestion de l'environnement

<br>

*  répertoire dédié au process (clean au stop)

```
[Service]
Type=simple
ExecStart=/usr/bin/sleep infinity
RuntimeDirectory=xavki
```

RuntimeDirectoryMode : pour spécifier le mode (permissions sur le répertoire)


----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Gestion de l'environnement

<br>

* définir des variables d'environnement

Environment=NODE_ENV=production PORT=1494

```
[Service]
Environment=ENV=production APP=myapp
Type=simple
ExecStart=/bin/bash -c "/usr/bin/echo $ENV; /usr/bin/echo $APP"
```

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Gestion de l'environnement

<br>

* par fichier

EnvironmentFile=/etc/myapp/environment

```
[Service]
EnvironmentFile=/etc/myapp/environment
Type=simple
ExecStart=/bin/bash -c "/usr/bin/echo $ENV; /usr/bin/echo $APP"
```


defines on which directory the service will be launched, same as when you use cd to change a directory when you're working in the shell.

That doesn't mean that all the other paths (including that from ExecStart=) will now be relative to it, so you still need to fully specify the path to your script in that directive:

RootDirectory= 

RootDirectoryStartOnly=yes

InaccessibleDirectories=/home

User=penguin-web
Group=penguin-web
EnvironmentFile=/etc/penguin-web-app/environment
DynamicUser=


RemainAfterExit=: This directive is commonly used with the oneshot type. It indicates that the service should be considered active even after the process exits.

PIDFile=: If the service type is marked as “forking”, this directive is used to set the path of the file that should contain the process ID number of the main child that should be monitored.
NotifyAccess=: This specifies access to the socket that should be used to listen for notifications when the “notify” service type is selected This can be “none”, “main”, or "all. The default, “none”, ignores all status messages. The “main” option will listen to messages from the main process and the “all” option will cause all members of the service’s control group to be processed.



    ExecStart=: This specifies the full path and the arguments of the command to be executed to start the process. This may only be specified once (except for “oneshot” services). If the path to the command is preceded by a dash “-” character, non-zero exit statuses will be accepted without marking the unit activation as failed.
    ExecStartPre=: This can be used to provide additional commands that should be executed before the main process is started. This can be used multiple times. Again, commands must specify a full path and they can be preceded by “-” to indicate that the failure of the command will be tolerated.
    ExecStartPost=: This has the same exact qualities as ExecStartPre= except that it specifies commands that will be run after the main process is started.
    ExecReload=: This optional directive indicates the command necessary to reload the configuration of the service if available.
    ExecStop=: This indicates the command needed to stop the service. If this is not given, the process will be killed immediately when the service is stopped.
    ExecStopPost=: This can be used to specify commands to execute following the stop command.
    RestartSec=: If automatically restarting the service is enabled, this specifies the amount of time to wait before attempting to restart the service.
    Restart=: This indicates the circumstances under which systemd will attempt to automatically restart the service. This can be set to values like “always”, “on-success”, “on-failure”, “on-abnormal”, “on-abort”, or “on-watchdog”. These will trigger a restart according to the way that the service was stopped.
    TimeoutSec=: This configures the amount of time that systemd will wait when stopping or stopping the service before marking it as failed or forcefully killing it. You can set separate timeouts with TimeoutStartSec= and TimeoutStopSec= as well.

StandardOutput=syslog
StandardError=syslog
StandardOutput=append:/var/log/bird_watching.log
StandardError=append:/var/log/bird_watching.log
SyslogIdentifier=bird_watching

Environment=NODE_ENV=production PORT=1494


RequiresMountsFor=

AssertPathExists=/srv/http

PrivateTmp=true


    Use built-in options to sandbox your service instead of chrooting it. Specifically:

    RemoveIPC=true and PrivateTmp=true. These ensure that the lifetime of the IPC objects and temporary files created by the executed process is bound to the runtime of the service. Since /tmp and /var/tmp are usually the only world-writable directories on a system this ensures that the unit cannot leave files around after termination.
    NoNewPrivileges=true and RestrictSUIDSGID=true. These ensure that processes invoked cannot take benefit or create SUID/SGID files or directories.
    ProtectSystem=strict and ProtectHome=read-only prohibits the service from writing to anywhere in your filesystem (exceptions are /dev/ /proc/ and /sys/. In order to allow the service to write to certain directories, they have to be allow-listed using ReadWritePaths=.
    RuntimeDirectory= to assign a runtime directory to the service, which is owned by the service's user, and removed automatically when the system is terminated.
Nice=



