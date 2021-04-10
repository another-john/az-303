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
    - SSL termination: offload encryption and decryption to the gateway itself, rather than forcing the backend servers to handle it
    - Autoscaling: Allows you to automatically scale up or down, based on traffic load. (Only by Application Gateway standard V2)
    - Web applicaiton firewall:
      - Offers centrralized protection of web applications
      - Protects applications from common exploits and vulnerabilities like SQL injection attacks, cross site scriptiong attacks, etc
    - Zone redundancy:
      - Can be spanned across multiple availability zones
      - Do not need to provision a separate application Gateway in each zone
  - Components:
    - Frontend IP, Listener, Requesting Routing Rule, HTTP Setting, Backend Pool, Health Probes

3. Frondt Door
  - Offers global load balancing fro applications and even microservices.
  - Can fail over such apps and microservices across different regions or even different clouds
  - Define manage and monitor global routing for web traffic
  - Key features:
    - Improved application performance
      - by use of split TCP-based ancast protocal
      - ensure that users of an applicaiton copnnect to the nearest point of presence
    - Increased availability
      - smart health probes
    - URL based routing
      - Route traffic to backed pools based on the URL paths of the request
    - Cookie-based Session affinity
      - ensure that a specific user session remains on the same backend for the duration of the session
    - TLS ternmination, custom domain support, URL redirection

4. Web Application Firewall
  - With Application Gateway
    - Offers protection for web applicaitons against web vulnerabilities and attacks without any need for changes to the applicaiton code itself
    - Can protect multiple applicaitons simutaneously
    - Can host and protect up to 40 websites on a single instance
    - Custom WAF policies allow you to use different policies for different sites
  - With Front Door
    - Provides centralized protection against web threats
    - Deployed on edge locations on the Azure network around the world
    - Every incoming request is inpected at the edge of the network
    - Attacks are prevented by WAF before they even enter your virtual network
  - With CDN
    - Used to protect web content itself
    - Mitigates malicious attacks closed to their sources, rather than after they reach your network

5. Traffic Manager
  - Load balancer that works by distributing traffic using DNS
  - Typically used to distribute traffic to services that are located across different global azure regions
  - Approach
    - use DNS to send access requests to the service enpoint with the least latency for the requester
    - based on the configured traffic routing method and on the health of the endpoints that have been configured
    - the configured endpoints can be any internet facing service that's hosted inside or outside of Azure
  - Routing Methods
    - Priority: 
      - used to send all incoming traffic to a primary service endpoint, while making backup endpoints available in the event the primary endpint is not
    - Weighted: 
      - used in situations where you need to split traffic out across multiple endpoints, based on weighting that you define.
      - can also be used to evenly split traffic across multiple endpoints
    - Performacne: 
      - used with applications that are distributed across multiple geographic locations. 
      - Allows you to direct users to the closest endpoint, which reduces latency
    - Geographic: 
      - allows you to forece users to and endpoint closest to them. 
      - based on the geographic locaiton of the original DNS query. 
      - Typically used to ensure a user in Europe access your applicaiton from a european endpoint
    - Multivalue:
      - Used for Traffic Manager profiles that can only ahve IPV4 or IPV6 addresses as endpoints
    - Subnet:
      - Allows you to map specific ranges of end-user IP addresses to specifixc endpoints
      - This means you can force specific users, based on their IP addresses, to connect to certain endpoints
  - NOT a proxy or gateway. Client connects directly to selected endpoint, not though Traffic Manager.