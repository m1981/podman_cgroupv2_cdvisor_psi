# What makes containers possible?
# What are namespaces?
https://rootlesscontaine.rs/getting-started/common/subuid/
http://www.haifux.org/lectures/299/netLec7.pdf
There are currently 6 namespaces: ● mnt (mount points, filesystems) ● pid (processes) ● net (network stack) ● ipc (System V IPC) ● uts (hostname) ● user (UIDs)
User ID
Group ID

# What is CRI
# What is runc, crun etc.
# What is OCI?
# Why Docker has deemon?
# Why podman is deamonless?

# Hands on: Creating your own “Docker” like tool?
tbd  
```unshare --user --pid --map-root-user --mount-proc --fork bash```  
https://www.nginx.com/blog/what-are-namespaces-cgroups-how-do-they-work/  
sdsd

# How does chroot work?
show based on fedora root filesystem from this article

tbd
# What are cgroups
cgroup is a mechanism to organize processes hierarchically and distribute system resources along the hierarchy in a controlled and configurable manner.

cgroup is largely composed of two parts - the core and controllers. cgroup core is primarily responsible for hierarchically organizing processes. A cgroup controller is usually responsible for distributing a specific type of system resource along the hierarchy although there are utility controllers which serve purposes other than resource distribution.

cgroups form a tree structure and every process in the system belongs to one and only one cgroup. All threads of a process belong to the same cgroup. On creation, all processes are put in the cgroup that the parent process belongs to at the time. A process can be migrated to another cgroup. Migration of a process doesn’t affect already existing descendant processes.

Following certain structural constraints, controllers may be enabled or disabled selectively on a cgroup. All controller behaviors are hierarchical - if a controller is enabled on a cgroup, it affects all processes which belong to the cgroups consisting the inclusive sub-hierarchy of the cgroup. When a controller is enabled on a nested cgroup, it always restricts the resource distribution further. The restrictions set closer to the root in the hierarchy can not be overridden from further away.  
`https://docs.kernel.org/admin-guide/cgroup-v2.html`

# Mini project: cute-micro-servers.com
tbs

# Podman as alternative to Docker

## Why rootless containers?
tbd

## cgroups v2
## Hands on
Rootless containers
Do steps from this page
https://rootlesscontaine.rs/getting-started/common/login/

If /sys/fs/cgroup/cgroup.controllers is present on your system, you are using v2, otherwise you are using v1.




# Commands

cat /etc/wsl.conf
echo $XDG_RUNTIME_DIR
systemctl --user is-active dbus

Rootless containers
Do steps from this page
https://rootlesscontaine.rs/getting-started/common/login/

https://rootlesscontaine.rs/getting-started/common/subuid/
https://rootlesscontaine.rs/getting-started/common/cgroup2
https://rootlesscontaine.rs/getting-started/common/sysctl/
Cgroups

If /sys/fs/cgroup/cgroup.controllers is present on your system, you are using v2, otherwise you are using v1.

Sprawdzcie sobie na konsoli
ls -l /sys/fs/cgroup/

cat /proc/mounts

/usr/bin/crun --help
michal:524288:65536

/etc/subuid
/etc/subgid

sudo chmod 4755 /usr/bin/newgidmap
sudo chmod 4755 /usr/bin/newuidmap


michal@C-5CG1145GM9:~$ mount | grep cgro
tmpfs on /sys/fs/cgroup type tmpfs (rw,nosuid,nodev,noexec,relatime,mode=755)
cgroup2 on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
