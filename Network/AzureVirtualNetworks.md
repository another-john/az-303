## Azure Virtual Networks

1. vNet Concepts 
  - Address Space
    - Must consist of public or private addresses that conform to the RFC 1918
  - Subnets
  - Regions
  - Sbuscriptions

2. Best Practices
  - When deploying a virtual network, you need to ensure that the __adress space__ that you defin for that virtual network __does not overlap__ with any other network ranges that your organization uses
  - Never create a __subnet__ that encompasses the entire address space of the virtual network
  - Define fewer large vNETs rather than numerous small vNETs
    - Fewer larger networks can prevent or minimize management overhead
  - You should secure all virtual networks that you create with __network security groups__
    - Network Security Group: 
      - used to filter network traffic to and from Azure resources that are attached to a virtual network
      - contains rules that allow or deny inbound and outbound network traffic to and from subnets

3. Communications
  - To enable inbound communication from the internet to an Azure resource, you can either:
    - assign a __public IP__ address to that resource
    - provision a __public load balancer__
  - Service Endpoint
    - allwos you to extend a virtual network;s private address space and identity to certain Azure resources, like Azure Storage account/Azure SQL Databases, over a direct connection
  - vNETs Peering
    - allow azure resource on one virtual network to talk to the other virtual network that you are peered with
    - Microsoft Bckbone Infrastructure
  - On-prem <-> virtual network
    - Point-to-site vpn
      - Often used to allow remote workers to conenc into your Azure virtual network through an encrypted tunnel over the internet
      - Protocols
        - OpenVPN Protocol
          - SSL/TLS-based VPN protocol that can be used through a firewall
          - Can be used to connect from a variey of client machines, Android, Linux, MacOSX
        - Secure Socket Tunneling Protocol (SSTP)
          - A proprietary VPN protocol that leverages TLS
          - Can be used though firewalls
          - Only Windows
        - IKEv2 VPN
          - A standards-based IPSec VPN solution
          - Can be sued to connect from Mac OSX devices
      - Authentication
        - Native Azure certificate authentication
        - Native Azure AD authentication
        - Traditional Active Directory Domain Server
    - site to site vpn
      - When you want to connect an entire on-prem network to an Azure vNET
      - Establishes a secure encrypted connection over the internet between an Azure VPN Gateway that's deployed i nthe vNET and the on-prem VPN device
      - IPSec or IKE VPN tunnel
      - A VPN device must be deployed on-prem with a __public ip address__ assigned to it
      - Process
        - Create the Azure virtual network
        - Create a gateway subnet on your virtual network
        - Create a VPN gateway
        - Create the local network gateway
        - Configure the on-prem VPN device
        - Deploy a VPN connection in Azure
        - Verify the connection
    - Express Route
      - private connection
      - does net flow over the internet

4. Filtering, two key ways to filter traffic between subnets
  - security groups
    - Network Security Groups
      - Can be assigned to a specific Network Interface(NIC) or to an entire subnet
      - Rules that are defined within the network security group are then applied to that NIC or to all NICs and virtual machines on the subnet, when the security group is applied to the entire subnet
      - For most scenarios
    - Application Security Group
      - Logically group the NICs of several different virtual machines on the same virtual network
      - Then apply a network security group rule to only those grouped NICs
  - network virtual appliances
    - a virtual machine that is used to perform a specific network task
    - can act as a firewall or provide WAN optimization
    - Available NVAs include
      - Barracuda CloudGen WAF for Azure
      - Citrix SD-WAN Center

5. Routing
  - Route tables: custom tables that allow to define custom routes that control how traffic is routed for each of your subnets
  - BGP routes, Border Gateway Protocol Routes: typically used to connec an Azure virtual network to an on-prem network via:
    - ExpressRoute Connection
    - Azure VPN Gateway

6. Integration
  - private ip
  - private link
  - service endpoint

7. VPN Gateway
  - one VPN Gateway per virtual network
  - each VPN Gateway supports multiple connections to it
  - what happens:
    - Azure deploys at least two hidden VMs
    - contain routing tables and the gateway services
    - cannot configure
    - need to tell what type

8. vNET Peering 
  - Two types
    - Virtual Network Peering: same region
    - Global Virtual Network Peering: different regions
  - Benefits
    - Low-latency high-bandwidth
    - facilitates data transfer across different virtual networks even when they are in different Azure subscription, AD tenants and regions
    - enables you to connect virtual networks that were created through the Azure Resource Manager
    - Enables you to connect virtual networks that were created through Reource Manager tot htose that were created through the classic deployment model
    - Creating a peering causes no downtime to resources during the peering process nor after the peering isd completed
    - remains on the Microsoft backbone network, remains private without the need for the public Internet, gateways or even encryption