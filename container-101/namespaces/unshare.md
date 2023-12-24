
input by normal user
```
unshare --user --map-root-user --pid --mount --fork
```

```
ls -l /proc/1/ns
```

```
total 0
lrwxrwxrwx 1 root root 0 Oct  3 17:50 cgroup -> 'cgroup:[4026532388]'
lrwxrwxrwx 1 root root 0 Oct  3 17:50 ipc -> 'ipc:[4026532305]'
lrwxrwxrwx 1 root root 0 Oct  3 17:50 mnt -> 'mnt:[4026532479]'
lrwxrwxrwx 1 root root 0 Oct  3 17:50 net -> 'net:[4026532308]'
lrwxrwxrwx 1 root root 0 Oct  3 17:50 pid -> 'pid:[4026532480]'
lrwxrwxrwx 1 root root 0 Oct  3 17:50 pid_for_children -> 'pid:[4026532480]'
lrwxrwxrwx 1 root root 0 Oct  3 17:50 time -> 'time:[4026531834]'
lrwxrwxrwx 1 root root 0 Oct  3 17:50 time_for_children -> 'time:[4026531834]'
lrwxrwxrwx 1 root root 0 Oct  3 17:50 user -> 'user:[4026532478]'
lrwxrwxrwx 1 root root 0 Oct  3 17:50 uts -> 'uts:[4026532304]'
```

```
$ ls -l /proc/2930/ns/
total 0
lrwxrwxrwx 1 shawn111 shawn111 0 Oct  3 17:50 cgroup -> 'cgroup:[4026532388]'
lrwxrwxrwx 1 shawn111 shawn111 0 Oct  3 17:50 ipc -> 'ipc:[4026532305]'
lrwxrwxrwx 1 shawn111 shawn111 0 Oct  3 17:50 mnt -> 'mnt:[4026532479]'
lrwxrwxrwx 1 shawn111 shawn111 0 Oct  3 17:50 net -> 'net:[4026532308]'
lrwxrwxrwx 1 shawn111 shawn111 0 Oct  3 17:50 pid -> 'pid:[4026532306]'
lrwxrwxrwx 1 shawn111 shawn111 0 Oct  3 17:51 pid_for_children -> 'pid:[4026532480]'
lrwxrwxrwx 1 shawn111 shawn111 0 Oct  3 17:50 time -> 'time:[4026531834]'
lrwxrwxrwx 1 shawn111 shawn111 0 Oct  3 17:51 time_for_children -> 'time:[4026531834]'
lrwxrwxrwx 1 shawn111 shawn111 0 Oct  3 17:50 user -> 'user:[4026532478]'
lrwxrwxrwx 1 shawn111 shawn111 0 Oct  3 17:50 uts -> 'uts:[4026532304]'
```



Unshare is used to create new namespace
```
#sudo unshare -u
```

Shows your current hostname
```
#hostname
ubuntu
```

Change your current hostname
```
#hostname hello
#hostname
hello
```

But when you open a new tab, and check the host name
```
#hostname
ubuntu
```

To see the namespace of the current terminal
```
#ls /proc/$$/ns
cgroup  ipc  mnt  net  pid  pid_for_children  user  uts
#readlink /proc/$$/ns/uts
uts:[4026532341]
```

But at the other terminal you opened
```
#readlink /proc/$$/ns/uts
uts:[4026531838]
```
The uts is different!
Meaning it is at different UTS namespace.
However, if we check the mount namespace, it is the same.
```
#readlink /proc/$$/ns/mnt
mnt:[4026531840]
```
This is because it is mounted on the same mount point. It is just separated under the point.
