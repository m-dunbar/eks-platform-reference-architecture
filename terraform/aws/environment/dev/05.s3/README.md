# Simple Storage Service (S3)

AWS Simple Storage Service is an Object Store -- NOT a filesystem.  It is implemented with a single, flat, AWS-wide namespace.  What this means is that bucket names are not account specific, and must be unique throughout all of AWS.  Thoughtful naming practices should includes account or project specific naming rather than general names.  

This also means if you are testing this code, you might need to tweak the "bucket" attribute within `s3.bucket.tf-integration-template-terraform-state-us-east-1`, if the specified bucket is currently instantiated within S3.

## General S3 best practices

- Always use encryption at rest within S3 buckets
- Always use encryption in transit when creating or accessing objects in S3 buckets
- Create managed policies to enforce access controls - policies can be added in IAM, attached directly to buckets, or both
- Enforce standards through the use of sane module-based defaults when creating and managing buckets

## Security Edge Case

As an aside, consideration should be given to the risk that the potential bad actors to leverage taking over old bucket names previously used by other account holders once those buckets are deleted.  This means when coding apps that use S3, the s3 bucket path URLs should never be directly exposed.  It is best practice to use edge services such as CloudFront Distributions instead for all exposed, world-facing path references.  This allows the use of fully-managed URLs for resource access, which precludes takeover at an unspecified future date if a bucket is no longer in use, deleted, and returned to the global namespace.

## TODO

- implement module for creation of standardized buckets using an s3.bucket_list.auto.tfvars

## Further Reading

For further information regarding AWS KMS concepts, the service it provides, and it's implementation, see [AWS S3 Documentation](https://docs.aws.amazon.com/s3/).

For further information regarding Terraform's Resource configuration, see Hashicorp's S3 Resource Documentation for (at an absolute minimum) [aws_s3bucket](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_bucket), and [aws_s3_bucket_server_side_encryption_configuration](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_bucket_server_side_encryption_configuration).

---

© 2025 Matthew Dunbar  
(See LICENSE for details.)
