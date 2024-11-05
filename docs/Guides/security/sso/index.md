---
layout: default
title: Configure SSO
description: Learn about how to set up SSO authentication for Firebolt.
nav_order: 2
parent: Configure security
grand_parent: Guides
has_toc: false 
has_children: true
---

# Configure your IdP

Single-sign on (SSO) is an authentication process that allows users to access multiple applications or services with a single set of credentials. It provides a centralized authentication mechanism for organizations so that it's easier to manage user access, enforce security policies, and revoke access when necessary.

## Pre-requisites

Before you can use SSO with Firebolt, you must complete specific configuration steps in your Identity Provider (IdP) system, which is responsible for authenticating users and managing their credentials. Part of these steps include defining an **Audience URI**, which specifies the intended recipient of a SAML assertion about a user's authentication. The configuration of an Audience URI depends on your IdP. See the following list of supported IdPs for specific instructions.

{: .note}
If your Audience URI is not configured correctly, Security Assertion Markup Language (SAML) assertions used for authentication will fail, preventing users from signing in using SSO.

## Supported IdPs

Firebolt allows users to sign in using their federated identities. The SSO implementation supports the following IdPs:

- [Auth0](../sso/auth0.md)
- [Okta](../sso/okta.md)
- [OneLogin](../sso/onelogin.md)
- [Salesforce](../sso/salesforce.md)
- [PingFederate (Ping Identity)](../sso/pingfederate.md)
- [Custom Identity provider](../sso/custom-sso.md)

If your IdP is not listed but supports SAML2.0, contact the [Firebolt support team](mailto:support@firebolt.io). 

