## Azure Virtual Machine
1. Benefits:
  - Not need to buy or maintain physical hardware
  - Still have to manage server-associated tasks
    - configuration
    - patch maangement
    - software installation
2. Considerations:
  - naming conventions
  - deployment locaiton
  - VM sizing requirements
  - quantity of VMs needed
  - OS
  - Configuration
3. Related Resources:
  - Resource Group
  - Virtual Network
  - Virtual NIC
  - Storage Account: if Unmanaged Disk is used
  - Managed Disk
  - Public Address
4. Pricing:
  - Pay-as-you-go
    - Pay by the second
    - No long-term commitment
    - No upfront payments, increase/decrease capacity as needed
    - Pay only for what you use
    - Low cost and flexible option
  - Reserved VM instances
    - Advanced purchase
    - 1-year or 3-year commitment
    - Upfront payment (up to 72% cheaper than payg)
    - application with steady state usage
    - offers budget predictability
  - Spot Pricing
    - purchase unused compite capacity
    - up to 90% cheaper than payg
    - must tolerate interruptions
    - very low compute costs
 5. VM Options:
   - General Purpose
     - dev/test
     - small databases
     - low traffice web servers
   - Compute Optimized
     - medium traffic web servers and network applicances
     - batch processing 
     - application servers
   - Memory Optimized
     - RDB
     - Large caches
     - in-memory analytics
   - Storage Optimized
     - big data
     - SQL and NoSQL databases
   - GPU
     - rendering 
     - video editing
   - High performance compute
     - molecular modeling
     - genomic research
     - financial risk modeling
 6. Availability Sets
   - 2+ VMs in an availability set = VM SLA of 99.95% uptime
   - 1 VM = 99.9% uptime (if premium SSD/ ultra-disk)
   - Every VM is assigned a Fault Domain and Update Domain
   - 1 Availability Set -> 5 Update Domains by default (upto 20)
   - Update Domain: a group of virtual machines and underlying physical hardware that can be rebooted at the same time
   - Planned Maintenanace->One update domain is rebooted at a time
   - Fault Domain: shares a common power source and a common network switch
   - Add VMs to an Availability Set:
     - Resource Manager Deployments: distribute to 3 different FD
     - Classic Deployments: 2 different FD
   - Availability Set protection:
     - Network Outages
     - Physical hardware failures
     - power interruptions
 7. Availability Zone:
   - Prevent data center failurs
   - 99.99 VM uptime SLA
 8. Resize VM:
   - The change depends on the hardware cluster
   - if the new size is not available, need to deallocate VM first
   - if use Premium Storage, need to make sure the new size is an S version
   - if in availability set, might need to deallocate all other VM in the set
   - 