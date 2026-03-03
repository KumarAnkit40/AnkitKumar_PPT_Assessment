# Task 4 — Hybrid Architecture Simulation

## Objective

Simulate secure on-prem to cloud architecture using Bastion Host, Private Subnet, Route Tables, and controlled access.

---

## Step 1 — Create VPC/VNet

* Created a Virtual Private Network (VPC/VNet).
* Created:

  * One Public Subnet
  * One Private Subnet

---

## Step 2 — Launch Bastion Host

* Launched Bastion Host in **Public Subnet**
* Assigned a **Public IP**
* Enabled SSH (Port 22)

---

## Step 3 — Launch Private VM

* Launched Private Virtual Machine in **Private Subnet**
* No Public IP assigned
* Instance not exposed to internet

---

## Step 4 — Configure Security Group / NSG

* Configured Security Group / NSG rules:

  * Allowed SSH (Port 22)
  * Source: Bastion Host only
* No direct SSH allowed from internet to Private VM

---

## Step 5 — Update Route Tables

* Public Subnet:

  * Route `0.0.0.0/0` → Internet Gateway
* Private Subnet:

  * No direct route to Internet Gateway
  * Isolated from public access

---

## Step 6 — Access Private VM via Bastion

* Connected to Bastion Host using Public IP
* From Bastion, SSH into Private VM using Private IP
* Access successful via Jump Server

Traffic flow:
User → Bastion → Private VM

---

## Step 7 — Verify Isolation

* Attempted direct SSH to Private VM from local machine
* Connection failed
* Confirmed Private VM is not directly accessible from internet

---

## Step 8 — Document Traffic Flow Diagram

Created architecture diagram showing:

User → Internet → Bastion Host → Private VM

Private VM isolated inside Private Subnet.

---

## Result

Secure hybrid architecture successfully implemented.
Private VM accessible only through Bastion Host.
Direct internet access blocked.
