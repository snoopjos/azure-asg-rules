# 🔐 Azure Subnet Security Rules Lab
A hands-on Azure lab focused on configuring Network Security Groups (NSGs) to control traffic between a public and private subnet using the Azure Portal.

## 🧠 Key Learnings
- Created two subnets:
  - **Public Subnet**: Hosts the web server
  - **Private Subnet**: Hosts storage and database resources
- Configured NSG rules to:
  - ✅ Allow inbound traffic on **port 80 (HTTP)** and **443 (HTTPS)** to the public subnet
  - ❌ Deny all inbound traffic to the private subnet for enhanced security
- Deployed a storage account for blob storage and restricted access to only allow traffic from within the Virtual Network using **storage firewall rules**
- Enabled a **service endpoint for Microsoft.Storage** to allow secure access inside the virtual network to the storage account
- Remoted into the web server to install roles and features via RDP (port 3389)

## 🛠️ Tech Stack
- Azure Portal
- Virtual Network (VNet) with two subnets
- Network Security Groups (NSGs)
- Windows Server VM

## 🚀 Next Steps
- Extend the lab by automating NSG setup via Azure CLI
- Explore logging and monitoring with Network Watcher
- Add CI/CD deployment for web server content

---

Feel free to fork, clone, or adapt this lab to suit your own cloud security learning journey.

---

### Step 1
Create resource group.

### Step 2
Create Virtual Network with two Subnets, one public and one private.

### Step 3
Deploy first VMs for the public sub, NSG rule with port 3389 open, a NIC and a public IP address.

### Step 4
Updated NIC from dynamic to static IP as I will be adding DHCP and DNS servers to my VM.

### Step 5
RDP into VM and install following roles and features: AD DS, DHCP server, DNS server, Print and Documents Services and Web Server (IIS).

### Step 6
Storage account created with a service endpoint.