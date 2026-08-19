# Cloud Server Investigation Report

## Operating System

The cloud server is running **Ubuntu 24.04.4 LTS (Noble Numbat)**.

## Kernel Version

The Linux kernel version is:

**6.8.0-136-generic**

## CPU Model

The CPU model is:

**Intel Xeon E312xx (Sandy Bridge, IBRS update)**

## Number of CPU Cores

The server has:

**1 CPU core**

## Total RAM

The system has:

**1.9 GiB of total RAM**

## Disk Capacity

The root filesystem has:

**19G total disk capacity**

The disk is mounted at `/` using the `/dev/vda1` device.

## Mounted File Systems

The cloud server has several mounted file systems. Important mounted
file systems include:

- `/dev/vda1` mounted on `/` with `ext4`
- `/dev/vda16` mounted on `/boot` with `ext4`
- `/dev/vda15` mounted on `/boot/efi` with `vfat`
- `sysfs` mounted on `/sys`
- `proc` mounted on `/proc`
- `devtmpfs` mounted on `/dev`
- `devpts` mounted on `/dev/pts`
- `tmpfs` mounted on `/run`
- `tmpfs` mounted on `/dev/shm`
- `cgroup2` mounted on `/sys/fs/cgroup`
- `securityfs` mounted on `/sys/kernel/security`
- `debugfs` mounted on `/sys/kernel/debug`
- `tracefs` mounted on `/sys/kernel/tracing`

These file systems provide storage and system interfaces required
for the Linux operating environment.

## Hostname

The hostname of the cloud server is:

**ubuntu**

## IP Address

The IP addresses reported by the server are:

- **172.30.1.2**
- **172.17.0.1**

## Conclusion

The investigation shows that the KillerCoda cloud server provides an
Ubuntu 24.04.4 LTS Linux environment with a 6.8.0-136-generic kernel,
one CPU core, approximately 1.9 GiB of RAM, and a 19G disk. The server
also uses several mounted virtual and system file systems to support
Linux operations. Its hostname is `ubuntu`, and it has the IP addresses
172.30.1.2 and 172.17.0.1.
