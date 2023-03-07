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
`https://wiki.archlinux.org/title/cgroups`

## Check cgroup version used by kernel
`systemctl status`

# Mini project: cute-micro-servers.com
tbs

# Podman as alternative to Docker
### Rootles with same user/group IDs as current user
[Rootles Explained](https://www.tutorialworks.com/podman-rootless-volumes)

Use flag `-userns=keep-id`

Example:
`$ podman run -ti --userns=keep-id  localhost/ansible:5 bash`

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


# Reference

https://www.kernel.org/doc/html/latest/admin-guide/cgroup-v2.html  
https://www.redhat.com/sysadmin/fedora-31-control-group-v2  
https://www.kernel.org/doc/html/latest/admin-guide/cgroup-v1/cgroups.html  
https://www.kernel.org/doc/html/latest/admin-guide/cgroup-v1/cpuacct.html  
https://www.kernel.org/doc/html/latest/admin-guide/cgroup-v1/cpusets.html  
https://www.kernel.org/doc/html/latest/admin-guide/cgroup-v1/blkio-controller.html  
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/resource_management_guide/ch01  
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/resource_management_guide/sec-relationships_between_subsystems_hierarchies_control_groups_and_tasks  
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/resource_management_guide/sec-implications_for_resource_management  
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/resource_management_guide/ch-using_control_groups  
https://www.redhat.com/en/blog/world-domination-cgroups-rhel-8-welcome-cgroups-v2  
https://www.redhat.com/en/blog/world-domination-cgroups-part-1-cgroup-basics  
https://www.redhat.com/en/blog/world-domination-cgroups-part-2-turning-knobs  
https://www.redhat.com/en/blog/world-domination-cgroups-part-3-thanks-memories  
https://www.redhat.com/en/blog/world-domination-cgroups-part-4-all-ios  
https://www.redhat.com/en/blog/world-domination-cgroups-part-5-hand-rolling-your-own-cgroup  
https://www.redhat.com/en/blog/world-domination-cgroups-part-6-cpuset  
https://rootlesscontaine.rs/getting-started/common/subuid/  
https://rootlesscontaine.rs/getting-started/common/cgroup2/  
https://rootlesscontaine.rs/getting-started/common/sysctl/  
https://askubuntu.com/questions/1442826/systemd-in-degraded-state-after-enabling-in-wsl  
https://www.freedesktop.org/software/systemd/man/systemd.unit.html  
https://www.nginx.com/blog/what-are-namespaces-cgroups-how-do-they-work/  
https://adil.medium.com/how-to-monitor-server-via-psi-pressure-stall-information-and-cgroupv2-2d944a9e732e  
https://systemd.io/CGROUP_DELEGATION/  
https://www.kernel.org/doc/html/latest/admin-guide/cgroup-v2.html  
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/resource_management_guide/ch01  
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/resource_management_guide/sec-relationships_between_subsystems_hierarchies_control_groups_and_tasks  
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/resource_management_guide/ch-subsystems_and_tunable_parameters  
https://www.redhat.com/en/blog/world-domination-cgroups-rhel-8-welcome-cgroups-v2  
https://facebookmicrosites.github.io/cgroup2/docs/overview.html  
https://www.steamship.com/build/langchain-apps  
https://learn.microsoft.com/en-us/windows/wsl/wsl-config  
https://rootlesscontaine.rs/getting-started/common/subuid/  
https://oldgitops.medium.com/setting-up-podman-on-wsl2-in-windows-10-be2991c2d443  
https://rootlesscontaine.rs/getting-started/common/cgroup2/
https://www.grant.pizza/blog/understanding-cgroups/



