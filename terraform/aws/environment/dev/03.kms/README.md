# AWS Key Management Service (KMS)

Unsurprisingly, provides centralized management of encryption keys.

In this example, a Custom KMS key, and supporting key alias (`terraform`) have been created, for use encrptying the contents of the bucket in S3 where a centralized tfstate backend (including a hierarchical folder structure for tfstate files) will be maintained, and for the terrform_locks dynamodb table, used to prevent terraform management collisions from more than one administrator being applied simultaneously.

## TODO

While the initial `terraform` key is sufficient for initial implementation, any additional keys that may be needed later should also be managed here.  Alternately, dedicated project, service, or stack-related keys can be created within those specific related segmentation domains.

- add a kms.keys.tf template, along with supporting variables declaration, and a list of additional keys to be maintained.

## Further Reading

For further information regarding AWS KMS concepts, the service it provides, and it's implementation, see [AWS KMS Documentation](https://docs.aws.amazon.com/kms/).

For further information regarding Terraform's Resource configuration, see Hashicorp's [KMS Resource Documentation](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/kms_key).

Best practice also dictates all keys should be defined with a matching [kms_key_alias](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/kms_alias), and wherever possible the key alias object should be referenced, under the principal that internal Terraform resource or data object references are _always_ to be preferred over hardcoding key references, which is brittle, and a bad practice.

---

© 2025 Matthew Dunbar  
(See LICENSE for details.)
