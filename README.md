# What makes containers possible?
# What are namespaces?
https://rootlesscontaine.rs/getting-started/common/subuid/
http://www.haifux.org/lectures/299/netLec7.pdf
There are currently 6 namespaces: ● mnt (mount points, filesystems) ● pid (processes) ● net (network stack) ● ipc (System V IPC) ● uts (hostname) ● user (UIDs)
User ID
Group ID

# Creating your own “Docker” like tool using unshare?
tbd
# How does chroot work?
tbd
# What are cgroups



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
