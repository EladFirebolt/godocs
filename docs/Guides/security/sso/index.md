---
layout: default
title: Configure SSO
description: Learn about how to setup SSO authentication for Firebolt.
nav_order: 2
parent: Configure security
grand_parent: Guides
has_toc: false 
has_children: true
---

# Configure your IdP

Before you can set up SSO with Firebolt, follow the required configuration steps in your Identity Provider(IdP) to work with the application.

{: .note}
Before creating a SAML integration in your IdP, you must configure the Audience URI. Otherwise, SAML assertions will not pass, and SSO will not allow users to sign in.

Firebolt supports the ability for users to sign into firebolt using their federated identity. Firebolt's SSO implementation supports the following identity providers (IdPs):

- [Auth0](https://firebolt.io/Guides/security/sso/auth0.html)
- [Okta](https://firebolt.io/Guides/security/sso/okta.html)
- [OneLogin](https://firebolt.io/Guides/security/sso/onelogin.html)
- [Salesforce](https://firebolt.io/Guides/security/sso/salesforce.html)
- [PingFederate (Ping Identity)](https://firebolt.io/Guides/security/sso/pingfederate.html)
- [Custom Identity provider](https://firebolt.io/Guides/security/sso/custom-sso.html)

If your IdP is not on the above list but supports SAML2.0, [contact the Firebolt support team for further assistance](support@firebolt.io). 