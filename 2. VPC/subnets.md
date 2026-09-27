# Subnets

Subnets are splits of VPC. Instead of having only one VPC with all resources (app servers, web servers, databases) in one place, we split into subnets for organization and security.

Each subnet has a part of the VPC IP range.

## CIDR Block Distribution

```

VPC: 10.0.0.0/16
├─ Subnet 1: 10.0.1.0/24 (256 IPs)
├─ Subnet 2: 10.0.2.0/24 (256 IPs)
└─ Subnet 3: 10.0.3.0/24 (256 IPs)
```

AWS services live inside subnets (EC2, RDS, Load Balancers), so each service gets a private IP from the subnet's range.

```
Subnet 1: 10.0.1.0/24
├─ EC2: 10.0.1.50
├─ RDS: 10.0.1.100
└─ Load Balancer: 10.0.1.150

Subnet 2: 10.0.2.0/24
├─ EC2: 10.0.2.50
└─ ElastiCache: 10.0.2.75
```

Each service has a different private IP.

## Public vs Private Subnets

### Public Subnet
- Has route to **Internet Gateway (IGW)**
- Instances can receive traffic from internet
- Used for: web servers, load balancers, NAT Gateways
- **Needs public IP** to communicate with internet

### Private Subnet
- NO route to IGW
- Instances cannot receive traffic from internet directly
- Used for: databases, app servers, cache layers
- Can only communicate outbound via **NAT Gateway**

## Reserved IPs

AWS reserves 5 IPs per subnet:
```
Subnet: 10.0.1.0/24 (256 total)
├─ 10.0.1.0 → Network address (reserved)
├─ 10.0.1.1 → VPC router (reserved)
├─ 10.0.1.2 → DNS (reserved)
├─ 10.0.1.3 → Reserved
├─ 10.0.1.4 to 10.0.1.254 → Available for instances
└─ 10.0.1.255 → Broadcast (reserved)
```
Usable: 251 IPs (not 256)


## Route Table Association

Each subnet must be associated with a **Route Table** that defines where traffic goes:
- Public subnet → Route Table points to IGW
- Private subnet → Route Table points to NAT Gateway (or local only)

## Communication Rules

**PRIVATE IPs:**
- ✗ Cannot communicate directly with internet
- ✓ Can communicate with other private IPs inside VPC
- Need IGW (public subnet) or NAT Gateway (private subnet) as intermediary

**PUBLIC IPs:**
- ✓ Can communicate with internet directly
- ✓ Can communicate with private IPs inside VPC

