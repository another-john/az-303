## Azure Network Security Implementation
1. Azure Virtual Network Connectivity
  - VN is scoped to a single Azure region, which is a set of datacenters deployed within a latency-defined parameter
2. Azure Front Door Service
3. Network Security Groups
  - Security Rule:
    - Unique Name
    - Priority: 100-4096
    - Source Destination:
      - Individual Address
      - Any Address
      - CIDR Block
      - Service Tag
      - Application Security Group
    - Protocol
      - TCP
      - UDP
      - ICMP
      - ANY
    - Direction
      - INBOUND
      - OUTBOUND
    - Port Range
      - INDIVIDUAL
      - RANGE
    - Action
      - ALLOW
      - DENY
4. Azure Firewall
  - cloud-based network security service
  - stateful
  - high availability 
  - unrestricted cloud scalability
  - can create policies across Subscriptions and Networks
5. Application Security Groups
  - A grouping of virtual network interfaces that is used to configure network security for the virtual machine machines that the NICs are attached to
  - allow to define network security policies based on the group that you define
  - can reuse defined security policy at scale without the need to manually maintain a list of included IP addresses
  - Constraints:
    - limited to 30,000 application security groups that can be defined within a subscription
    - only one application security group as the source and destination when configuring a security rule
    - all network interfaces that are assigned to the group must exist within the same __virtual network__ as the first network interface that is assigned to the application security group
    - if you specify an application security group as the source and destination in a security rule, the NICs in both groups must exist within the same virtual network.
      - e.g {Group1: NIC1->VNet1} {Group2: NIC2->VNet2} 
      - you cannot assign Group1 as the source and Group 2as the destination in a rule
6. Just-in-time Provisioning
  - useful for protecting against brute-force attacks by limiting the amount of time that the ports for a VM are open
  - access requests are logged in the AZURE ACTIVITY LOG
  - need to be in the Standard pricing tier of Azure Security Center

7. Tools:
  - Azure Security Center
  - Azure Vault
  - Azure AD
  - Azure Policy
  - Azure Monitor