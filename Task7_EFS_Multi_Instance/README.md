## Objective
Create an Elastic File System (EFS) and mount it on multiple EC2 Ubuntu instances to share common storage.

## Steps

1. Launch two EC2 Ubuntu instances
   - Same VPC
   - Allow ports 22 (SSH) and 2049 (NFS) in security group

2. Create EFS
   - Go to EFS → Create file system
   - Select the same VPC
   - Keep default settings and create

3. Modify security group
   - Add inbound rule
   - Type: NFS
   - Port: 2049
   - Source: EC2 security group

4. Connect to first EC2 instance
   ssh -i keypair.pem ubuntu@<Public-IP>

5. Install NFS client
   sudo apt update -y
   sudo apt install nfs-common -y

6. Create mount directory
   sudo mkdir /mnt/efs

7. Mount EFS
   sudo mount -t nfs4 -o nfsvers=4.1 <EFS-DNS>:/ /mnt/efs

8. Create test file
   echo "Shared Storage Working" | sudo tee /mnt/efs/test.txt

9. Connect to second EC2 instance
   ssh -i keypair.pem ubuntu@<Public-IP>

10. Install NFS client
    sudo apt update -y
    sudo apt install nfs-common -y

11. Create mount directory
    sudo mkdir /mnt/efs

12. Mount same EFS
    sudo mount -t nfs4 -o nfsvers=4.1 <EFS-DNS>:/ /mnt/efs

13. Verify file
    cat /mnt/efs/test.txt

## Result
Both EC2 instances access the same shared file through the mounted EFS storage.