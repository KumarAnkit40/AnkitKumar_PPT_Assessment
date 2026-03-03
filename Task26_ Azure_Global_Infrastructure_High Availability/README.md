# Azure Highly Available VM Infrastructure (Free Tier - 2 VMs)

## Objective

To deploy a highly available Virtual Machine infrastructure in Microsoft Azure using:

* Availability Set
* Public Load Balancer
* Azure Monitor
* Storage Account for Diagnostics

---

## Architecture Overview

This project includes:

* 1 Resource Group
* 1 Virtual Network with Subnet
* 2 Virtual Machines (inside Availability Set)
* 1 Public Azure Load Balancer
* Azure Monitor Alert Rule
* Storage Account for Diagnostic Logs

This setup ensures high availability within Free Tier limits.

---

## Implementation Steps

### Step 1: Create Resource Group

* Login to Azure Portal
* Go to Resource Groups → Create
* Enter Name, Subscription, Region
* Click Review + Create

Screenshot: screenshots/step1-resource-group.png

---

### Step 2: Create Virtual Network and Subnet

* Go to Virtual Networks → Create
* Address Space: 10.0.0.0/16
* Create Subnet: 10.0.1.0/24

Screenshot: screenshots/step2-vnet-subnet.png

---

### Step 3: Deploy 2 VMs in Availability Set

* Create first VM
* Select Availability Option → Availability Set
* Create new Availability Set

  * Fault Domains: 2
  * Update Domains: 5
* Deploy second VM in same Availability Set

Purpose:

* Protects from hardware failure
* Protects during planned maintenance

Screenshot: screenshots/step3-availability-set.png

---

### Step 4: Create Public Load Balancer

* Go to Load Balancers → Create
* Type: Public
* SKU: Standard
* Associate Public IP

Screenshot: screenshots/step4-load-balancer.png

---

### Step 5: Add VMs to Backend Pool

* Open Load Balancer
* Go to Backend Pools
* Add both Virtual Machines

Screenshot: screenshots/step5-backend-pool.png

---

### Step 6: Configure Health Probe & Load Balancing Rule

Health Probe:

* Protocol: TCP
* Port: 80
* Interval: 5 seconds

Load Balancing Rule:

* Frontend IP: Public IP
* Backend Pool: Both VMs
* Protocol: TCP
* Port: 80

Screenshot: screenshots/step6-health-rule.png

---

### Step 7: Enable Azure Monitor Alert

* Go to Azure Monitor → Alerts
* Create Alert Rule

  * Scope: Virtual Machines
  * Condition: CPU > 70%
  * Action: Email Notification

Screenshot: screenshots/step7-alert-rule.png

---

### Step 8: Create Storage Account & Enable Diagnostics

* Create Storage Account
* Go to VM → Diagnostic Settings
* Enable Boot Diagnostics
* Enable Logs & Metrics
* Select Storage Account

Screenshot: screenshots/step8-storage-diagnostics.png

---

### Step 9: Test High Availability

* Copy Load Balancer Public IP
* Access in browser
* Stop one VM
* Refresh browser
* Application remains accessible

Expected Result:
Traffic automatically routes to active VM without downtime.

Screenshot: screenshots/step9-testing.png

---

## High Availability Testing Results

 Scenario             Result                         
 -------------------  ------------------------------ 
 VM1 Shutdown         Application accessible via VM2 
 Planned Maintenance  No downtime                    
 High CPU Usage       Alert triggered                

---

## Limitations

* Only 2 VMs deployed (Free Tier restriction)
* Availability Zones not implemented

---

## Conclusion

This project successfully demonstrates:

* Fault tolerance using Availability Set
* Traffic distribution using Load Balancer
* Monitoring using Azure Monitor
* Diagnostic logging using Storage Account

High availability achieved within Free Tier constraints.
