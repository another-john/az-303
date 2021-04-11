## Azure Network Watcher
1. Network Watcher is a acollection of network monitoring and troubleshooting tools
2. IP Flow Verify 
  - Tests whether packets can flow between a VM and an endpoint
  - It checks them at network security groups that are associated with the VM and tells you which rule allows or denies the connection
  - Only checks the security groups associated with the VM. It doesn't check the security associated with the endpoint.
  - For V1<->V2, need to verify the other direction as well
3. Next Hop
  - If you have a VM that can't connect to something else and you've used IP Flow Verify to ensure a security group isn't blocking it. It may be a routing problem and Next Hop might help
4. Connection Troubleshoot
  - Have to install an extension the VM that's having the connection problem
5. VPN Troubleshoot
  - If the connection you're troubleshooting involves a virtual network gateway
6. Connection Monitor
  - Monitors connection between a VM and an endpoint(VM/Address)
7. Logs
  - If you have intermittent networking issues or a large number of connections to monitor, you'll need to get more detailed information
  - types:
    - NSG flow logs: Keeps track of what traffic was allowed through an NSG and asdwhat was denied
    - Diagnostic logs: Track both NSGs and network interfaces
      - it does not record as much infromation about NSG events as flow logs do
8. Traffic Analysis
  - gives you a dashboard that makes it easy to see what's happening with your network
8. Network Performance Monitor
  - Peformance Monitor
  - ExpressRoute Monitor
  - Service Connectivity Monitor (Office 365/ Dynamics 365)
  - Can be configured using either ICMP or TCP
    - ICMP
      - Less accurate for latency and packet loss
      - Doesn't monitor ExpressRoute connections
    - TCP
      - Requires you to run a PowerShell script called EnableRules on each Windwos VM that has an agent

