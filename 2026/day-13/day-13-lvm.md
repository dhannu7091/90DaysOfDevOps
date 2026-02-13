# Day 13 – Linux Volume Management (LVM)

## Challenge Tasks

### Task 1: Check Current Storage
- Run: `lsblk`, `pvs`, `vgs`, `lvs`, `df -h`
  - Output:
    ```
    root@ip-172-31-17-47:/home/ubuntu# lsblk
    NAME         MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
    loop0          7:0    0 27.6M  1 loop /snap/amazon-ssm-agent/11797
    loop1          7:1    0 27.8M  1 loop /snap/amazon-ssm-agent/12322
    loop3          7:3    0 73.9M  1 loop /snap/core22/2216
    loop4          7:4    0 48.1M  1 loop /snap/snapd/25935
    loop5          7:5    0 50.9M  1 loop /snap/snapd/25577
    loop6          7:6    0   74M  1 loop /snap/core22/2292
    nvme0n1      259:0    0   15G  0 disk 
    ├─nvme0n1p1  259:1    0   14G  0 part /
    ├─nvme0n1p14 259:2    0    4M  0 part 
    ├─nvme0n1p15 259:3    0  106M  0 part /boot/efi
    └─nvme0n1p16 259:4    0  913M  0 part /boot
    nvme1n1      259:5    0   10G  0 disk 
    nvme2n1      259:6    0    5G  0 disk 
    root@ip-172-31-17-47:/home/ubuntu# df -h
    Filesystem       Size  Used Avail Use% Mounted on
    /dev/root         14G  2.3G   12G  18% /
    tmpfs            458M     0  458M   0% /dev/shm
    tmpfs            183M  908K  182M   1% /run
    tmpfs            5.0M     0  5.0M   0% /run/lock
    efivarfs         128K  3.8K  120K   4% /sys/firmware/efi/efivars
    /dev/nvme0n1p16  881M   89M  730M  11% /boot
    /dev/nvme0n1p15  105M  6.2M   99M   6% /boot/efi
    tmpfs             92M   12K   92M   1% /run/user/1000
    ```
    - Checking after completing assignment
      ```
      root@ip-172-31-17-47:/home/ubuntu# pvs
        PV           VG        Fmt  Attr PSize   PFree
        /dev/nvme1n1 devops-vg lvm2 a--  <10.00g 9.31g
      root@ip-172-31-17-47:/home/ubuntu# vgs
        VG        #PV #LV #SN Attr   VSize   VFree
        devops-vg   1   1   0 wz--n- <10.00g 9.31g
      root@ip-172-31-17-47:/home/ubuntu# lvs
        LV       VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
        app-data devops-vg -wi-ao---- 700.00m
      ```
---

### Task 2: Create Physical Volume
```
pvcreate /dev/sdb   # or your loop device
pvs
```
- Output:
  ```
  lvm> pvcreate /dev/nvme1n1
  WARNING: ext4 signature detected on /dev/nvme1n1 at offset 1080. Wipe it? [y/n]: y
    Wiping ext4 signature on /dev/nvme1n1.
    Physical volume "/dev/nvme1n1" successfully created.
  
  lvm> pvs
    PV           VG        Fmt  Attr PSize   PFree 
    /dev/nvme1n1 devops-vg lvm2 a--  <10.00g <9.51g  
  ```

---

## Task 3: Create Volume Group
```
vgcreate devops-vg /dev/sdb
vgs
```
- Output:
  ```
  lvm> vgcreate devops-vg /dev/nvme1n1
    Volume group "devops-vg" successfully created
  lvm> vgs
    VG        #PV #LV #SN Attr   VSize   VFree 
    devops-vg   1   1   0 wz--n- <10.00g <9.51g
  ```

---

## Task 4: Create Logical Volume
```
lvcreate -L 500M -n app-data devops-vg
lvs
```
- Output:
  ```
  lvm> lvcreate -L 500M -n app-data devops-vg
    Logical volume "app-data" created.
  lvm> lvs
    LV       VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
    app-data devops-vg -wi-a----- 500.00m
  ```

---

### Task 5: Format and Mount
```
mkfs.ext4 /dev/devops-vg/app-data
mkdir -p /mnt/app-data
mount /dev/devops-vg/app-data /mnt/app-data
df -h /mnt/app-data
```
- Output:
  ```
  root@ip-172-31-17-47:/home/ubuntu# mkfs.ext4 /dev/devops-vg/app-data
  mke2fs 1.47.0 (5-Feb-2023)
  Creating filesystem with 128000 4k blocks and 128000 inodes
  Filesystem UUID: ca5b6e10-6acb-4851-b449-9f5fe28cae2b
  Superblock backups stored on blocks: 
  	32768, 98304
  
  Allocating group tables: done                            
  Writing inode tables: done                            
  Creating journal (4096 blocks): done
  Writing superblocks and filesystem accounting information: done
  
  root@ip-172-31-17-47:/home/ubuntu# mkdir -p /mnt/app-data
  root@ip-172-31-17-47:/home/ubuntu# mount /dev/devops-vg/app-data /mnt/app-data
  root@ip-172-31-17-47:/home/ubuntu# df -h /mnt/app-data
  Filesystem                        Size  Used Avail Use% Mounted on
  /dev/mapper/devops--vg-app--data  452M   24K  417M   1% /mnt/app-data
  ```

---

### Task 6: Extend the Volume
```
lvextend -L +200M /dev/devops-vg/app-data
resize2fs /dev/devops-vg/app-data
df -h /mnt/app-data
```
- Output:
  ```
  root@ip-172-31-17-47:/home/ubuntu# lvm
  lvm> lvextend -L +200M /dev/devops-vg/app-data
    Size of logical volume devops-vg/app-data changed from 500.00 MiB (125 extents) to 700.00 MiB (175 extents).
    Logical volume devops-vg/app-data successfully resized.
  ```
  ```
  root@ip-172-31-17-47:/home/ubuntu# resize2fs /dev/devops-vg/app-data
  resize2fs 1.47.0 (5-Feb-2023)
  Filesystem at /dev/devops-vg/app-data is mounted on /mnt/app-data; on-line resizing required
  old_desc_blocks = 1, new_desc_blocks = 1
  The filesystem on /dev/devops-vg/app-data is now 179200 (4k) blocks long.
  
  root@ip-172-31-17-47:/home/ubuntu# df -h /mnt/app-data
  Filesystem                        Size  Used Avail Use% Mounted on
  /dev/mapper/devops--vg-app--data  637M   24K  594M   1% /mnt/app-data
  ```


