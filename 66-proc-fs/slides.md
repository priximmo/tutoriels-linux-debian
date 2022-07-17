%title: LINUX
%author: xavki


# LINUX : PROC, le pseudo-fs


<br>

* qu'est-ce que fait PS ??

```
strace -e openat ps
```

-----------------------------------------------

# LINUX : PROC, le pseudo-fs


<br>

* du coup regardons un peu /proc

* quelques génériques

```
cat /proc/version
cat /proc/cmdline
cat /proc/uptime
cat /proc/loadavg
cat /proc/cpuinfo
cat /proc/meminfo
cat /proc/vmstat
cat /proc/diskstats
cat /proc/stat
```

-----------------------------------------------

# LINUX : PROC, le pseudo-fs


<br>

* pour chaque process

```
ls /proc/$(pgrep sleep)/
cat /proc/xx/cmdline
cat /proc/xx/cwd
cat /proc/xx/environ
cat /proc/xx/exe
cat /proc/xx/fdinfo/1
ls /proc/xx/fd/
cat /proc/xx/oom_score
cat /proc/xx/cgroup
cat /proc/xx/ns
cat /proc/xx/stat
cat /proc/xx/statm
```
