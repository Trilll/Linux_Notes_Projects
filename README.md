# Linux_Notes_Projects
This repository is documentation of my journey through Linux.

<h1>RHEL 9 Storage Stack (LVM Layout)</h1>
# RHEL 9 / Linux Storage Stack (copy/paste friendly)

+-----------------------------+
|         Apps/Users          |
+--------------+--------------+
               |
               v
+-----------------------------+
|  Paths (/, /home, /var...)  |
+--------------+--------------+
               |
               v
+-----------------------------+
|  Mount points (mount, fstab)|
|  - systemd mounts at boot   |
+--------------+--------------+
               |
               v
+-----------------------------+
|   Filesystem (XFS/ext4)     |
|   - organizes files/dirs    |
+--------------+--------------+
               |
               v
+-----------------------------+
|   Block device (/dev/...)   |
+--------------+--------------+
               |
     +---------+----------+
     |                    |
     v                    v
+------------------+   +----------------------+
| LVM Logical Vol  |   | Plain partition      |
| /dev/VG/LV       |   | /dev/sda2, /dev/nvme |
+--------+---------+   +----------+-----------+
         |                        |
         v                        v
+------------------+      +-------------------+
| LVM Volume Group |      | Partition (GPT)   |
| VG (storage pool)|      | /dev/sda1..n      |
+--------+---------+      +---------+---------+
         |
         v
+------------------+
| LVM Physical Vol |
| PV (/dev/sda3...)|
+--------+---------+
         |
         v
+-----------------------------+
|      Partitions (GPT)       |
|  /dev/sda1 /dev/sda2 ...    |
+--------------+--------------+
               |
               v
+-----------------------------+
|          Disk               |
|  /dev/sda, /dev/nvme0n1     |
+--------------+--------------+
               |
               v
+-----------------------------+
| Hardware / Virtual Disk     |
| (VirtualBox, SAN, SSD, etc) |
+-----------------------------+

Notes:
