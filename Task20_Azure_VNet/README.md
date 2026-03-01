## Objective
Create a virtual network with subnets and configure basic network security rules.

## Steps

1. Create Virtual Network
   - Open Azure Portal → Virtual networks → Create
   - Resource group: select existing
   - Name: myVNet
   - Address space: 10.0.0.0/16

2. Create Subnet
   - Subnet name: subnet1
   - Subnet address range: 10.0.1.0/24
   - Create VNet

3. Create Network Security Group (NSG)
   - Go to Network security groups → Create
   - Name: myNSG
   - Select resource group

4. Add inbound rule
   - Allow SSH
   - Port: 22
   - Protocol: TCP
   - Action: Allow

5. Associate NSG with subnet
   - Open NSG → Subnets → Associate
   - Select myVNet and subnet1

6. Verify configuration
   - Confirm subnet and NSG association

## Result
The virtual network and subnet are created successfully and secured with network security rules.