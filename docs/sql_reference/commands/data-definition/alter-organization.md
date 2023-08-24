---
layout: default
title: ALTER ORGANIZATION
description: Reference and syntax for the ALTER ORGANIZATION command.
great_grand_parent: SQL reference
grand_parent:  SQL commands
parent: Data definition
---

# ALTER ORGANIZATION

Updates the specified organization to manage Single Sign-On configuration.

For more information, see [Setting up SSO](../../../Guides/managing-your-organization/sso/sso.md), and example configurations in [Configure your identity provider](../../../Guides/managing-your-organization/sso/configuring-idp-for-sso.md). 

## Syntax

```json
ALTER ORGANIZATION SET SSO = ‘{
  “signOnUrl”: “<signOnUrl>”,
  “signOutUrl”: “<signOutUrl>”, 
  “issuer”: “<issuer>”,
  “provider”: “<idp>”,
  “label”: “<label>”,
  “fieldMapping”: “<field_mapping>”,
  “certificate”: “<certficate>”,
}’;
```

| Parameter | Description |
| :--- | :--- |
| `<signOnUrl>` | The sign-on URL, provided by the SAML identity provider, to which Firebolt sends the SAML requests. The URL is IdP-specific and is determined by the identity provider during configuration. |
| `<signOutUrl>` | Optional. The sign-out URL, provided by the application owner, to be used when the user signs out of the application. |
| `<issuer>` | A unique value generated by the SAML identity provider specifying the issuer name. |
| `<idp>` | The provider's name - for example: “Okta”. Possible values are: Okta, Onelogin, Salesforce, PingFederate, or Custom. Use the "Custom" label if you are using a SAML 2.0-compliant service or application as your IdP. Once the provider has been selected, it can't be changed, but you can [delete the SSO configuration](../../../Guides/managing-your-organization/sso/sso.md#delete-sso). |
| `<label>` | The label to use for the SSO login button. If not provided, the IdP field value is used. |
| `<field_mapping>` | Optional.  Mapping to your identity provider's first and last name in key-value pairs. Mapping is required for Firebolt to fill in the login’s given and last names the first time the user logs in using SSO. If this field remains empty when a login that represents the user is being created, the login's first and last name fields will contain “NA”. Those fields can be updated later by running the [`ALTER LOGIN`](../../../sql_reference/commands/access-control/alter-login.md) command. 
| `<certificate>` | The certificate to verify the communication between the identity provider and Firebolt. |


## Example

The following command will configure SSO using the Okta identity provider. For more examples for other IdPs, see [Configure your identity provider](../../../Guides/managing-your-organization//sso/configuring-idp-for-sso.md).

```json
ALTER ORGANIZATION SET SSO = ‘{
  “signOnUrl”: “https://abc.okta.com/app/okta_firebolt_app_id/sso/saml”,
  “signOutUrl”: “https://myapp.exampleco.com/saml/logout”, 
  “issuer”: “issuer”,
  “provider”: “Okta”, 
  “label”: “Okta”,
  “fieldMapping”: “mapping”,
  “certificate”: “XXXXXXXXXXXXXXXX”,
}’;
```