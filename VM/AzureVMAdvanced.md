## Azure VM Advanced 
1. Scale Sets:
  - a group of identical load-balanced VMs
  - increase/decrease numbe based on demand/predefined schedule
  - allows you to perform maintenance and update without downtime
  - Azure load balancers for basic traffic Layer 4 distribution
  - Azure Application Gateway for advanced Layer 7 distribtion, like SSL termination
2. Vertical Scaling/Horizontal Scaling
3. Configuration Management
  - ANSIBLE
    - VM creation, app deployment, configuration management
    - automation engine that uses an agentless model
  - CHEF:
    - configure, deploy and manage infrastructure
    - requires Chef client
  - puppet
    - automate the deployment process and application delivery
    - install agent
  - CloudInit
    - LinuxVM
    - no agent
    - define a list of packages to install
  - Azure Custom Scipt Extension
    - Downnload and execute scripts on both Linux and Windows Vms
    - during and after VM creation
  - Virtual Mahcine Extensions
    - perform post-deployment configuration and automation tasks on Azure VMs
    - small applications for perform VM configuration install applicaitons and deploy monitoring and security solutions to VMs
  - Powershell Desired State Configuration
4. Managed Disks
  - 99.999% availability
  - 3 replica of the data stored
  - allows up to 50,000 VM disks of a type per region in each subscription
  - integrated with Availability Set and Availability Zone
  - Azure Backup, upto 32 TB
  - Role Baed Access Control
  - Support for direct upload of VHD files
  - Two types of encryption:
    - server-side encryption: by Azure storage service, by default
    - Azure disk encryption: by OS and 
  - Three roles:
    - data disks: 32TB attached to a VM, SCSI drive
    - OS disks: 4TB
    - temporary disks: D on windows /dev/sdb on Linux
 5. Disk Types
   - Ultra-disks: High IOPS usage, data intensive workload, only as data disks
   - premium SSD: high performance and low latency, io-inensive workloads
     - bursting: for uneven traffice
   - standard ssd: cost efective
   - standard hdd: low cost disks
6. snapshot: a copy of a specific disk at a specific point of time, applies to only one disk
7. imagae: includes all disks attached to the VM being imaged
8. Azure Monitor for VMs: identify performance bottlenecks and network issues
  - Trending performance chart
  - Dependency Map: Azure VM dependency agent extension
9. Azure Monitor for VMs + Azure Monitor Logs
  - aggregation
  - filtering
  - analyze VM data trends over time
  - Insightes for Azure Monitor
10. Single VM or scale set: Insigts
11. More than one VM or scale set: Azure Policy or Powershell
12. Log analytics contributor role to enable and access the Azure Monitor for VM features.
13. Monitoring reader role for the particular Azure VM's performance health and map data