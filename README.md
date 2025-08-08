# 🔐 Azure Networking Lab: NSGs & Secure Storage Access  
A hands-on Azure lab focused on configuring Network Security Groups (NSGs) to control traffic to a public subnet using the Azure Portal.  
Includes secure access to a storage account using service endpoints and firewall rules.

## 🧠 Key Learnings  
- Created one subnet:  
  - **Public Subnet**: Hosts the web server  
- Configured NSG rules to:  
  - ✅ Allow inbound traffic on **port 80 (HTTP)** and **443 (HTTPS)** to the public subnet  
- Deployed a storage account for blob storage and restricted access to only allow traffic from within the Virtual Network using **storage firewall rules**  
- Enabled a **service endpoint for Microsoft.Storage** to allow secure access inside the virtual network to the storage account  
- Accessed blob data publicly using a **Shared Access Signature (SAS) token**  
- Remoted into the web server to install roles and features via RDP (port 3389)

## 🛠️ Tech Stack  
- Azure Portal  
- Virtual Network (VNet) with one subnet  
- Network Security Groups (NSGs)  
- Storage Account with service endpoints  
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
Storage account created with a service endpoint. Ended up adding the service endpoint from the subnets instead.

### Step 7
Attempted to access the blob via browser but failed — despite having service endpoints enabled. Learned that service endpoints only allow access from within the virtual network. Confirmed this by running the following PowerShell script from the VM:

Invoke-WebRequest -Uri "https://<your-storage-account>.blob.core.windows.net/<container>/<blob-name>" -OutFile "blob.jpg"

✅ Blob access worked from inside the VNet, proving the firewall and service endpoint setup was correct.

### Step 8
Generated a Shared Access Signature (SAS) token to enable public access. ✅ Successfully accessed the blob via browser using the SAS URL.