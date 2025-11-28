Traffic goes through the firewall, into the TGW, into 

Ingress: Firewall - TGW - Privte Network - SAG1
Egress: SAG1 - private network - TGW - Egress

Allows you to hub and then spoke off:

Shared Principal to Organisation - how every one in your org gets acccess to the router - based on management account IDs - currently pointing at our Prod account 

Make the attachment 
Make the association 
Make the route table 

The VPC that the RDS instance is in has got a DNS 
That DNS is now going to broadcast to all the netwreorks in the Range right 
So then when you go into Databricks euw2 and you netcat with the DNS with the domain name, then it will got to that IP
There's a certain amount of IPs that get consumed by default. There's a DNS server that is one of those IPs. The DNS server broadcasts and consumes. So all the DNS Servers in all the VPCs are broadcasting and consuming at the same time. Google has a DNS Server, Cloudflare has a DNS server. You don't want all DNS servers to look at all servers for lookups. So if I want to go to google.com I hit my DNS server, then that DNS records bounce around the world. 
So we have to explicitly tell it that when you get a request from this address, this CIDR block, then go to the transit gateway
Update the routes in the VPC that it's in PROD

Severless is not in our network - it's in the Databricks private network. 
It's to do with roles and IAM
Because our Datab ricks account has access to their role 
Our Databricks accoutns have access to our AWS account via our IAM roles 
