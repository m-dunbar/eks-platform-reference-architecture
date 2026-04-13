# Virtual Private Cloud (VPC)

VPCs are the foundation for many of the most commonly used services, providing a virtual network environment for hosts and microservices.

Leveraging the VPC module, using CIDRs provisioned from our previously defined IPAM pools ensures that any other VPCs that are provisioned from IPAM pools will never result in CIDR collisions.  This also automatically provisions the appropriate supporting resources, providing us with:

## Provisioned resources

- VPC

```text
DEV

us-east-1 VPC: [10.0.48.0/24]
```

- Subnets

```text
Subnets (AZ A): 
 ├─ Private:  10.0.48.0/26
 └─ Public: 10.0.48.64/26
 ```

- Network ACL
- Route Tables (default, private, public)
- Security Group
- Internet Gateway

## Further Reading

For further information regarding AWS KMS concepts, the service it provides, and it's implementation, see [AWS VPC Documentation](https://docs.aws.amazon.com/vpc/).

For further information regarding Terraform's Resource configuration, see Hashicorp's [VPC Module Documentation](https://registry.terraform.io/modules/terraform-aws-modules/vpc/aws/latest).

---

© 2025 Matthew Dunbar  
(See LICENSE for details.)
