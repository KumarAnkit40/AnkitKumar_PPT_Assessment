## Objective
Launch and configure a basic virtual machine in Azure and access it remotely.

## Steps

1. Open Azure Portal
   - Go to Virtual Machines → Create → Azure Virtual Machine

2. Configure basics
   - Resource group: create new
   - Virtual machine name: myvm
   - Region: any region
   - Image: Ubuntu Server
   - Size: Standard B1s

3. Authentication
   - Username: azureuser
   - Authentication type: Password
   - Set password

4. Inbound port rules
   - Allow SSH (Port 22)

5. Review and create
   - Click Create and wait for deployment

6. Get public IP address
   - Open the VM → Overview → Copy Public IP

7. Connect to VM
   ssh azureuser@<Public-IP>

8. Verify connection
   whoami

## Result
The Azure virtual machine is successfully deployed and accessible through SSH.