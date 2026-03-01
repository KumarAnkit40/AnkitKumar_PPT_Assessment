## Objective
Create a snapshot of an EBS volume and restore it in another Availability Zone, then attach it to an EC2 instance.

## Steps

1. Launch an EC2 instance in Availability Zone A.

2. Create a new EBS volume
   - Go to Volumes → Create Volume
   - Same AZ as EC2
   - Size: 8 GB
   - Attach to the EC2 instance

3. Connect to EC2
   ssh -i keypair.pem ubuntu@<Public-IP>

4. Verify attached disk
   lsblk

5. Create filesystem
   sudo mkfs.ext4 /dev/xvdf

6. Create mount directory
   sudo mkdir /data

7. Mount volume
   sudo mount /dev/xvdf /data

8. Add sample file
   echo "EBS Snapshot Test" | sudo tee /data/test.txt

9. Unmount volume
   sudo umount /data

10. Create snapshot
   - Go to Volumes
   - Select volume → Actions → Create Snapshot

11. Create new volume from snapshot
   - Select snapshot → Create Volume
   - Choose a DIFFERENT Availability Zone

12. Launch a new EC2 instance in the new Availability Zone.

13. Attach the new volume to the second EC2 instance.

14. Connect to second EC2
   ssh -i keypair.pem ubuntu@<Public-IP>

15. Verify disk
   lsblk

16. Mount volume
   sudo mkdir /data
   sudo mount /dev/xvdf /data

17. Verify file
   cat /data/test.txt

## Result
The data stored in the original EBS volume is successfully restored and accessible from the EC2 instance in a different Availability Zone.