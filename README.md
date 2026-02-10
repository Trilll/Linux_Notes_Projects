# Linux_Notes_Projects
This repository is documentation of my journey through Linux.

<h1>RHEL 9 Storage Stack (LVM Layout)</h1>

Apps / Users
|
V
Paths (/, /home, /var, /data...)
|
V
Mounts (mount points) <--- controlled by mount / systemd + /etc/fstab
|
V
Filesystem (usually XFS on RHEL 9; sometimes ext4)
|
V
Block device node (/dev..)
|
+-----------------------------------+
|                                   |
V                                   V
LVM Logical Volume (/dev/vg/lv)     Plain partition (/dev/sda2)   (either is possible)
|
V
LVM Physical Volumes (PV)  /dev/sda3, /dev/sdb1 
|
V
Partitions (GPT)  /dev/sda1 /dev/sda2 /dev/sda3
|
V
Disk (SATA/SCSI/NVMe)   /dev/sda,  /dev/nvme0n1
|
V
Hardware / Virtual disk (VirtualBox, SAN, etc)
