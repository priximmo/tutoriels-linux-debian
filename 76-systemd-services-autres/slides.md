%title: LINUX
%author: xavki


# LINUX : SYSTEMD - L'Environnement & Exec


<br>

```
man systemd.service
```

Objectif : comment permettre de l'auto-guerisson de vos services ?

* gérées par le [Unit]

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Propriétés de restart & Fails

<br>


WorkingDirectory=

defines on which directory the service will be launched, same as when you use cd to change a directory when you're working in the shell.

That doesn't mean that all the other paths (including that from ExecStart=) will now be relative to it, so you still need to fully specify the path to your script in that directive:

RootDirectory= 

User=penguin-web
Group=penguin-web
EnvironmentFile=/etc/penguin-web-app/environment

RemainAfterExit=: This directive is commonly used with the oneshot type. It indicates that the service should be considered active even after the process exits.

RuntimeDirectory=IPS-JAI1
PIDFile=: If the service type is marked as “forking”, this directive is used to set the path of the file that should contain the process ID number of the main child that should be monitored.
BusName=: This directive should be set to the D-Bus bus name that the service will attempt to acquire when using the “dbus” service type.
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
