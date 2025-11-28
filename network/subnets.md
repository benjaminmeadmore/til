# subnets

## subnets are vpc partitions

A subnet (subnetwork) is a logical subdivision of an IP network. Subnets divide a larger network into smaller, manageable segments. In AWS, a subnet is a range of IP addresses in your VPC. 

FYI, subnets can't communicate with non-routed networks.

## maths

### CIDR notation and sizing

Subnets are defined using CIDR notation (e.g., `10.0.1.0/24`):
- `/24` = 256 IP addresses (254 usable)
- `/25` = 128 IP addresses (126 usable)
- `/26` = 64 IP addresses (62 usable)
- `/27` = 32 IP addresses (30 usable)
- `/28` = 16 IP addresses (14 usable)

**Formula**: A `/N` CIDR block provides `2^(32-N)` IP addresses

### reserved ips

AWS reserves **5 IP addresses** in every subnet:
- `.0` - Network address
- `.1` - VPC router
- `.2` - DNS server
- `.3` - Reserved for future use
- `.255` - Network broadcast (not supported but reserved)

So if you configure a subnet with 256 CIDR suffix, you actually only get 251 usable Ips. From there, between your NAT gateway and your infrastructure overhead, you might only make it out with 240. 

In a practical sense, what that means is that if you provision 10 users each with a cluster that can run 20 workers, you'll almost max out your headroom! If we included autoscaling, multiple concurrent users, job clusters, interactive clusters in there the maths get even worse. 

it therefore makes sense to use /19 (8187 usable Ips) as a reasonable production-grade estimate. 

### numbers

**Common sizes**:
   - `/24` (251 IPs) - General purpose, good default
   - `/22` (1019 IPs) - Large container clusters (EKS/ECS)
   - `/28` (11 IPs) - Small utility subnets

Use `/20` or `/22` for private subnets with Kubernetes - ENI-based CNIs consume IPs quickly.

**VPC Sizing Pattern**:
```
/16 VPC = 65,536 IPs
  ’ Split into /24 subnets = 256 possible subnets
  ’ Each subnet = 251 usable IPs
```

### architecture

Standard 3-tier subnet design per AZ:
1. **Public** (`/24`) - Load balancers, bastion
2. **Private** (`/22`) - Application servers, containers
3. **Data** (`/24`) - Databases, cache

## subsets of subnets

The route table determines whether a subnet is public or private:

### public
- Has a route to an **Internet Gateway** (`0.0.0.0/0` ’ `igw-xxxxx`)
- Resources get public IPs (if enabled)
- Can directly communicate with the internet
- Use for: Load balancers, bastion hosts, NAT gateways

### private
- No direct route to Internet Gateway
- May route to **NAT Gateway** for outbound internet access
- Resources only have private IPs
- Use for: Application servers, databases, internal services

**Key Point**: A subnet is not inherently public or private - it's the route table configuration that determines this.

## availability zones

- Each subnet exists in **exactly one** Availability Zone
- Subnets cannot span multiple AZs
- For high availability, create subnets in multiple AZs
- Standard pattern: 2-3 AZs per region

## easy mistakes

- Public subnets need auto-assign public IPs enabled AND a route to IGW
- NAT Gateway costs are exorbitatnt: will run you ~$32/month per AZ + data transfer fees
- Kubernetes/ECS can consume IPs rapidly (pod/task per IP) so plan accordingly
- Cross AZ costs are $0.01-0.02 per GB
- VPC peering requires non-overlapping CIDR blocks across VPCs
