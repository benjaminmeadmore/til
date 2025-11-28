# Ips 

## Example 

Let's say you want to connect a Databricks Workspace to your AWS data plane, and want to start provisioning compute. Now subnet sizes actually determine how many compute nodes you can run simultaneously. Why? 

Each compute node requires an IP address from your subnet:
  - 1 Driver node = 1 IP
  - Each Worker node = 1 IP
  - Example: A cluster with 1 driver + 20 workers = 21 IPs consumed

the slash value (/25) sets how many bits can vary, and therefore how many IP addresses are available. When we subtract reserved IPs (AWS and Databricks)

## reservation dogs 

Databricks will needs IPs for NAT Gateways, internal load balancers, control plane communications. 