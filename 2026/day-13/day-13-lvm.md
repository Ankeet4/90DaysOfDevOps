# Day 13 – Linux Volume Management (LVM)

Today I practiced Linux LVM (Logical Volume Management) to understand how storage can be created, managed, mounted, and extended dynamically.

---

# Task 1 – Check Current Storage

## Check Block Devices

```bash
lsblk
```

Used to display disks, partitions, and mounted devices.

---

## Check Physical Volumes

```bash
pvs
```

Used to display physical volumes.

---

## Check Volume Groups

```bash
vgs
```

Used to display volume groups.

---

## Check Logical Volumes

```bash
lvs
```

Used to display logical volumes.

---

## Check Disk Usage

```bash
df -h
```

Used to display mounted storage and free space.

---

# Task 2 – Create Physical Volume

## Create Virtual Disk

```bash
dd if=/dev/zero of=/tmp/disk1.img bs=1M count=1024
```

Used to create a 1GB virtual disk file.

---

## Attach Loop Device

```bash
losetup -fP /tmp/disk1.img
```

Used to attach virtual disk as loop device.

---

## Verify Loop Device

```bash
losetup -a
```

Used to check loop device information.

---

## Create Physical Volume

```bash
pvcreate /dev/loop0
```

Used to initialize disk as physical volume for LVM.

---

## Verify Physical Volume

```bash
pvs
```

---

# Task 3 – Create Volume Group

## Create Volume Group

```bash
vgcreate devops-vg /dev/loop0
```

Used to create a volume group.

---

## Verify Volume Group

```bash
vgs
```

---

# Task 4 – Create Logical Volume

## Create Logical Volume

```bash
lvcreate -L 500M -n app-data devops-vg
```

Used to create a 500MB logical volume.

---

## Verify Logical Volume

```bash
lvs
```

---

# Task 5 – Format and Mount

## Format Logical Volume

```bash
mkfs.ext4 /dev/devops-vg/app-data
```

Used to format logical volume with ext4 filesystem.

---

## Create Mount Directory

```bash
mkdir -p /mnt/app-data
```

Used to create mount directory.

---

## Mount Logical Volume

```bash
mount /dev/devops-vg/app-data /mnt/app-data
```

Used to mount logical volume.

---

## Verify Mounted Storage

```bash
df -h /mnt/app-data
```

Used to check mounted filesystem and storage usage.

---

# Task 6 – Extend the Volume

## Extend Logical Volume

```bash
lvextend -L +200M /dev/devops-vg/app-data
```

Used to increase logical volume size.

---

## Resize Filesystem

```bash
resize2fs /dev/devops-vg/app-data
```

Used to resize filesystem after extending storage.

---

## Verify Extended Storage

```bash
df -h /mnt/app-data
```

---

# Commands Used

```bash
lsblk
pvs
vgs
lvs
df -h
pvcreate
vgcreate
lvcreate
mkfs.ext4
mount
lvextend
resize2fs
```

---

# What I Learned

- Difference between Physical Volume, Volume Group, and Logical Volume
- How LVM allows flexible storage management
- How to create and mount logical volumes
- How to extend storage dynamically
- Basic Linux storage administration workflow
