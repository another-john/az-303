## Azure Load Balancing

1. Azure Load Balancer
  - Transport Layer
  - OSI 4
  - Two varieties:
    - Public: 
      - Load balance incoming internet traffic to virtual machines
      - Requires to assign a public ip address to the frontend of the laod balancer
      - can provide outbound connections to the internet for VMs that are located inside your Azure virtual network,b y translating the vprivate IP addresses of the virtual machines to public IPs
    - Internal (Private)
      - Used in situations where only private IP addresses are required on the frontend
      - Limited to use cases where you only need to laod balance traffic within your Azure virtual network, or from an on-prem network that has been connected to your virtual network through a VPN or ExpressRoute connection
  - Two SKU
    - Basic Load Balancer
      - 300 Instances
      - No support for availability zones
    - Standard Load Balancer
      - 1000 instances
      - Supports zone-redundant/zonal frontends for inbound & outbound traffic
  - Components
    - Frontend IP Configuration
    - Backend Pool
    - Health Probes
    - Load Balancing Rules
    - High Availability Ports
      - Protocol -all and port -0
      - allow you to use a single rule to load balance all TCP flows and UDP flows
      - if you need to load balance a large number of ports
    - Inbound NAT Rules
    - Outbound Rules
      - Only supported on the standard load balancer

2. Application Gateway
  - use HTTP attributes to make routing decisions
  - Application layer
  - OSI 7
  - Key features:
    - 