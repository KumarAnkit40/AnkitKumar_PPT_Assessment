## Objective
Create and manage disk partitions using MBR in Linux and GPT in Windows.

## Steps

### Linux (MBR Partition using fdisk)

1. Attach a new disk to the virtual machine (example: /dev/xvdf)

2. Verify disk
   lsblk

3. Start partition tool
   sudo fdisk /dev/xvdf

4. Inside fdisk:
   - Press n (new partition)
   - Select p (primary)
   - Partition number: 1
   - Accept default sectors
   - Press w (write changes)

5. Format the partition
   sudo mkfs.ext4 /dev/xvdf1

6. Create mount directory
   sudo mkdir /mnt/data

7. Mount partition
   sudo mount /dev/xvdf1 /mnt/data

8. Verify
   df -h


### Windows (GPT Partition)

1. Open Disk Management
   Win + R → diskmgmt.msc

2. Locate the new disk
   - It will show as unallocated

3. Initialize disk
   - Select GPT (GUID Partition Table)

4. Create New Volume
   - Right click → New Simple Volume
   - Assign drive letter
   - Format as NTFS

5. Finish and verify drive is accessible in File Explorer

## Result
The disk is successfully partitioned and accessible in both Linux (mounted directory) and Windows (new drive letter).