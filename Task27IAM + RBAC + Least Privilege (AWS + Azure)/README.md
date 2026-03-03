## Objective

Implement role-based access control with least privilege policy in AWS IAM and Azure Entra ID.


# Part A — AWS IAM Configuration

## Step 1 — Create IAM User

* Open AWS IAM
* Created a user named **Developer**


## Step 2 — Attach EC2 Full Access

* Attached managed policy:
  **AmazonEC2FullAccess**
* Verified that the Developer user can access and manage EC2 resources.


## Step 3 — Create Custom Policy (Deny S3 Delete)

Created a custom IAM policy to deny S3 delete permissions by using aws policy generator.

Policy Name:
**Deny-S3-Delete**


## Step 4 — Attach Policy via IAM Role

* Created an IAM Role
* Attached the custom policy (**Deny-S3-Delete**) to the role
* Assigned the role to the Developer user


## Step 5 — Testing (AWS)

Test Results:

* EC2 access →  Working
* S3 Delete operation →  Access Denied

This confirms least privilege enforcement.


# Part B — Azure Entra ID Configuration

## Step 6 — Open Microsoft Entra ID

* Opened Azure Portal
* Navigated to **Microsoft Entra ID**

## Step 7 — Create New User

* Created a new user in Entra ID


## Step 8 — Assign Reader Role

* Assigned **Reader Role** on the Resource Group
* Verified user can view resources but cannot modify them


## Step 9 — Assign Contributor Role

* Assigned **Contributor Role** on one specific Virtual Machine only
* Verified user can manage that VM


## Step 10 — Testing (Azure)

Test Results:

* User can read all resources in Resource Group → Allowed
* User can modify only the assigned VM → Allowed
* User cannot modify other resources → Restricted

## Result

Role-Based Access Control (RBAC) was successfully implemented with least privilege in both AWS IAM and Azure Entra ID.
