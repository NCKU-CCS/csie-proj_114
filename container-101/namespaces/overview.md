"If host is a house, namespace is the room within the house assigned to each children providing privacy. Each child can only see inside their own room but not anything outside their room." -- KodeKloud (Youtuber)

What is namespace?
Namespace are used by container to implement network isolation.

Process ID(PID) namespace:
PID helps system tracks a specific task on the computer.
Ex. When you have safari and chrome searching on google for things, PID is used to identify where to direct the package sent back from google.
PID == 1 means it is the common ancestor to all the processes below.

Net namespace:
Network namespaces allow processes inside each namespace instance to have access to a new IP address along with the full range of ports.
Ex. Allowing us to run multiple versions of an email server listening on port 25 without any software conflicts.

UTS namespace:
Allows a single system to have different host and domain name to different processes.

User namespace:
Allows system to restrict access to sensitive files.
Ex. Not letting people using the same computer to access files that should not be seen by them.

Mount(mnt) namespace:
The mount namespace is used to isolate mount points such that processes in different namespaces cannot view each others' files.(just like chroot cmd)


RESOURCES:
1. https://www.youtube.com/watch?v=j_UUnlVC2Ss (Network Namespaces Basics Explained in 15 Minutes)(Youtube)
2. https://www.redhat.com/sysadmin/7-linux-namespaces (The 7 most used Linux namespaces)(Web)