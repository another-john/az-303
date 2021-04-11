## Azure Network Connectivity Name Resolution

1. VNet Peering
  - Global VNet peering
    - peering in different regions or across subscriptions
    - traffic still goes through the Microsoft backbone network rather than through the internet
    - so the connection is private and has high bandwidth and low latency
  - Restrictions
    - You can only peer two VNets if they ahave non-overlapping IP adress spaces
    - Once you've peered two VNets, you cant add or remove any of their address ranges. The only way to do it is to delete the peerings, make the change, and then create the perrings again
    - VNet peering is not transistive:
      - V1<->V2, V2<->V3, V1<->V3 NOT RECOMMENDED
      - Network topology would get pretty complicated
      - might want more control over the traffic between networks
      - Hub-and-spoke topology
        - hub acts as a router
        - the only way for two spokes to communicate with each other is through the hub
      - Advantage: could put shared services in the hub that could be used by all of the spoke.
        - e.g: firewalls, DNS servers, intrusion detection systems
      - Creating a router in the hub network:
        - deploy a simple linux vm that can route traffic
          - need to add route tables with user-defined routes so the spokes will know to send their external traffic to the hub
          - "Allow forwarded traffic" option
        - deploy a virtual network gateway
          - create route tables
          - "Allow gateway transit" option
          - "Use remote gateways" option

2. Virtual Network Gateway
  - Needs to be deployed to its own subnet
  - Recommended 27/28 in the address range

3. Azure DNS
  - When you create a virtual network Azure automatically sets up name resolution so the VMs in it can communicate with each other using hostnames instead of IP addresses
  - It doesn't work across peered VNets
  - Can be solved by setting up a custom DNS server
  - a simpler solution is Azure DNS
  - Split-horizon functionality
    - a zone that's both public and private
  - resolution VNets
    - VNets that dont have autoregistration enabled

