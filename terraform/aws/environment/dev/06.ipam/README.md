# IP Address Manager (IPAM)

IPAM allows central definition, allocation and management for IP (CIDR) ranges.  By provisioning CIDRs for VPCs and subnets for an Organization (or on a smaller scale for a single account), via IPAM, collisions in allocations of IP address ranges can be avoided.

## Scope

Scope in this context refers to RFC address space, either Routable (Public), or Non-routable (Private).  

It is most efficient and secure to provision within non-routable RFC ranges.  This provides ample IPv4 address space sufficient for an entire Organization while also providing routing boundaries.  Access to the public routable internet is provided inbound via Load Balancers, and outbound via Internet Gateway.

## Pool

Pool defines the size and range of the overall address space.  In a well-defined environment, CIDR allocations follow a plan, with blocks sized to be large enough, but not wasteful of IP resources.

### Plan pool allocation CIDRs

For a project of this size, a moderately sized block is sufficient.

#### Top-level CIDR

```text
Top Level IPAM Pool (main)
10.0.0.0/18  (AWS account)
```

#### Production

```test
us-east-1 VPC: 10.0.0.0/20
 ├─ AZ-a: [10.0.0.0/22]
 │    ├─ Public:  10.0.0.0/26  (ALB, NAT GW)
 │    └─ Private: 10.0.0.64/22 (EKS nodes/pods)
 ├─ AZ-b: [10.0.4.0/22]
 │    ├─ Public:  10.0.4.0/26
 │    └─ Private: 10.0.4.64/22
 └─ AZ-c: [10.0.8.0/22]
      ├─ Public:  10.0.8.0/26
      └─ Private: 10.0.8.64/22

us-west-2 VPC: 10.0.16.0/20
 ├─ AZ-a: [10.0.16.0/22]
 │    ├─ Public:  10.0.16.0/26v
 │    └─ Private: 10.0.16.64/22
 ├─ AZ-b: [10.0.20.0/22]
 │    ├─ Public:  10.0.20.0/26
 │    └─ Private: 10.0.20.64/22
 └─ AZ-c: [10.0.24.0/22]
      ├─ Public:  10.0.24.0/26
      └─ Private: 10.0.24.64/22
```

#### Staging

```text
us-east-1 VPC: 10.0.32.0/22
 ├─ AZ-a: [10.0.32.0/24]
 │    ├─ Public:  10.0.32.0/26
 │    └─ Private: 10.0.32.64/24
 ├─ AZ-b: [10.0.33.0/24]
 │    ├─ Public:  10.0.33.0/26
 │    └─ Private: 10.0.33.64/24
 └─ AZ-c: [10.0.34.0/24]
      ├─ Public:  10.0.34.0/26
      └─ Private: 10.0.34.64/24

us-west-2 VPC: 10.0.36.0/22
 ├─ AZ-a: [10.0.36.0/24]
 │    ├─ Public:  10.0.36.0/26
 │    └─ Private: 10.0.36.64/24
 ├─ AZ-b: [10.0.37.0/24]
 │    ├─ Public:  10.0.37.0/26
 │    └─ Private: 10.0.37.64/24
 └─ AZ-c: [10.0.38.0/24]
      ├─ Public:  10.0.38.0/26
      └─ Private: 10.0.38.64/24
```

#### QA

```text
us-east-1 VPC: 10.0.40.0/22
 ├─ AZ-a: [10.0.40.0/24]
 │    ├─ Public:  10.0.40.0/26
 │    └─ Private: 10.0.40.64/24
 └─ AZ-b: [10.0.41.0/24]
      ├─ Public:  10.0.41.0/26
      └─ Private: 10.0.41.64/24
```

#### Dev

```text
us-east-1 VPC: 
AZ subnet: [10.0.48.0/24]
 ├─ Public:  10.0.48.0/26
 └─ Private: 10.0.48.64/26
```

## Further Reading

For further information regarding IP Address Manager, concepts, and the service it provides, and it's implementation, see [AWS IPAM Documentation](https://docs.aws.amazon.com/vpc/latest/ipam/what-it-is-ipam.html).

For further information regarding Terraform's Resource configuration, see Hashicorp's [IPAM Resource Documentation](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/vpc_ipam).

---

© 2025 Matthew Dunbar  
(See LICENSE for details.)
