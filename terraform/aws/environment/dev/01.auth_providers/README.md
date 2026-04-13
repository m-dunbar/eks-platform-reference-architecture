# Security Assertion Markup Language (SAML) Provider

The AWS SAML 2.0 provider connects back to the Auth0 IdP, and is the foundation for implementing Role Based Access Control (RBAC).

This is what allows the use of the Trust Authority to determine which Auth0 users may assume which roles.

## Further Reading

For further information regarding SAML concepts, the service it provides, and it's implementation, see [AWS SAML 2.0 Federation Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_saml.html).

For further information regarding Terraform's Resource configuration, see Hashicorp's [AWS Resource IAM SAML Provider Documentation](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_saml_provider).

For further information on how Auth0 factors into this implementation, please review Auth0's documentation to [Configure SAML Identify Provider](https://auth0.com/docs/authenticate/single-sign-on/outbound-single-sign-on/configure-auth0-saml-identity-provider) or [OpenID Connect Identity Provider](https://auth0.com/docs/authenticate/identity-providers/enterprise-identity-providers/oidc). 

---

© 2025 Matthew Dunbar  
(See LICENSE for details.)
