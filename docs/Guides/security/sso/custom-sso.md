---
layout: default
title: Custom Identity Provider
description: Learn how to configure a custom Identity Provider integration with Firebolt. 
parent: Configure SSO
nav_order: 6
---

# Custom Identity Provider

A custom Identity Provider (IdP) allows you to use your organization's existing authentication system for secure access to Firebolt using Single Sign-On (SSO). By configuring a custom IdP, you ensure that your team can securely and efficiently access Firebolt resources using familiar credentials. 

To integrate a custom IdP with Firebolt's platform, you need to [configure your IdP for Firebolt](#configure-custom-identity-provider-idp) and [Firebolt's SSO for your custom IdP](#configure-firebolt-for-custom-idp). Detailed instructions can be found in the following sections:

## Configure Custom Identity Provider (IdP)

In order to set up a SAML 2.0 compliant service or application as your Identity Provider (IdP) for Single Sign-On (SSO) with Firebolt, follow these steps:
1. **Define a custom SHA-256**
   
   In the service/application interface, define a custom SHA-256 application specifically for Firebolt. Follow the service or application's instructions to create this custom application.
2. **Create Users in the Service/Application**

   For each end-user that needs access to Firebolt:
    * Create a user in the service/application interface.
    * Ensure that each user’s email address is correctly specified. Firebolt uses these email addresses to create corresponding logins in Firebolt.
   For more details, refer to [setting up SSO]({% link Guides/security/sso/index.md %}).

3. **Obtain Required Values for IdP Setup**

   To properly configure your IdP, you’ll need the following values:

   **Audience URI and ACS (Consumer) URL**

   These values are crucial for successful SSO authentication. If not configured properly, authentication will fail.
      For example, if your organization name is `acmeorg` and the provider name is `custom`:
       - Audience URI: `urn:auth0:firebolt-app-v2:acmeorg-custom`
       - ACS URL: `https://id.app.firebolt.io/login/callback?connection=acmeorg-custom&organization=<organization_identifier>`

    > **`<org_name>`** : The organizational name used to create your Firebolt account, as seen in your vanity URL.
    
    > **`<provider>`** : The provider being configured as your IdP.
    
    > **`<organization_identifier>`** : A unique identifier for your organization. To retrieve this value, navigate to **Configure > SSO** in the Firebolt UI and select Copy organization SSO identifier.

        {: .note} 
        The **Audience URI** (or Audience Restriction) defines the intended recipient of the SAML (Security Assertion Markup Language) Assertion. Depending on the vendor, this might also be   
        referred to as the **Entity ID**.

5. **Obtain SSO URL and Certificate**

   Retrieve the following from your custom IdP:
    * **SSO URL** : The endpoint where Firebolt sends SAML requests.
    * **Certificate** : Used to verify communication between the IdP and Firebolt.

With all required information, you are now ready to integrate your Identity Provider with Firebolt.

## Configure Firebolt for custom IdP
Once your Identity Provider(IdP) is configured, you can now configure Firebolt to integrate with your IdP. This can be done using either the Firebolt UI, or using SQL.

### Integrate with IdP using the UI
1. To configure the Firebolt SSO integration using the UI, Navigate to **Configure > SSO** in Firebolt. 
2. Enter the following information:
- ```Sign-on URL```: The URL provided by your SAML identity provider where Firebolt sends SAML requests. This URL is IdP-specific and is determined during the identity provider's configuration. 

  Example (for Okta):  
  `https://okta_account_name.okta.com/app/okta_firebolt_app_id/sso/saml`
  
- ```Issuer```:   A unique value generated by the SAML identity provider, identifying the issuer.
- ```Provider```: The name of your identity provider, such as `JumpCloud`.  
  If you are using a SAML 2.0-compliant service or application as your IdP, select the **Custom** label.

- ```Label```:   The text displayed on the SSO login button. If left blank, the value from the **Provider** field will be used.
- ```Certificate```:   The certificate used to verify communication between the identity provider and Firebolt. It must be in PEM or CER format. You can upload it using the **Import certificate** button or paste it directly into the provided text box.
- ```Sign-out URL```:   The URL provided by the application owner to redirect users when they sign out.
- ```Field mapping```: Mapping to your identity provider's first and last name in key-value pairs. If additional fields are required, choose **Add another key-value pair**. Mapping is required for Firebolt to fill in the login’s given and last names the first time the user logs in using SSO. If this field remains empty when a login that represents the user is being created (read more in the [log in using SSO](#log-in-using-sso) section), the login's first and last name fields will contain “NA”. Those fields can be updated later by running the [ALTER LOGIN]({% link sql_reference/commands/access-control/alter-login.md %}) command. 
      Here’s an example of how to set up **Field mapping**:

      ```json  
        {
            "given_name": "name",
            "family_name": "surname"
        }
      ```

   In this example:
     * given_name (first name) is mapped to the ```name``` field from the IdP.
     * family_name (last name) is mapped to the ```surname``` field from the IdP. 

3. Select **Update changes**.

### Integrate with IdP using SQL

To create your SSO connection in Firebolt, you can use the following SQL as an example:
```sql
ALTER ORGANIZATION vsko SET SSO = '{
  "signOnUrl": "https://dev-a8jnpkgk4y7gylt5.us.auth0.com/samlp/9aLOXgDHcqxW1gWtBuWNxVLbKNyv1LQV",
  "issuer": "okta",
  "provider": "okta",
  "label": "Okta Company IdP",
  "fieldMapping": {
    "given_name": "name",
    "family_name": "surname"
  },
  "certificate": "<certificate>",
}';
```

## Log in using SSO

1. Visit <a href="https://go.firebolt.io/login">go.firebolt.io/login</a>.
2. Enter your organization name and select **Continue to login**. If you don’t remember your organization name, select **Find out** next to **Don’t know your organization name?**.
3. Enter the email address you use for Firebolt and select **Send link**.  
4. Check your inbox for an email containing a direct login link for your organization. Bookmark this link for future use.  
5. Select **Login with <IDP>**.  
You’ll be redirected to your identity provider (IdP) for authentication. Once authenticated, you’ll return to Firebolt. 

**During Login**
- **New Users**:  
  If a login with your email doesn’t already exist, Firebolt will create one based on the email, first name, and last name provided in the SAML assertion from the IdP.  
  The new login will be SSO-only, with the `IS_PASSWORD_ENABLED` property set to `False`.  

- **Existing Users**:  
  If the login already exists and **Field Mapping** is set:  
  - If your first or last name differs from what’s specified in the IdP, Firebolt will update those fields.  
  - If the names match or Field Mapping is empty, the existing fields will remain unchanged and it will authenticate as usual.

## Edit SSO settings

SSO settings can be edited in two ways - using SQL or the UI.  To edit SSO settings using SQL, use the [ALTER ORGANIZATION]({% link sql_reference/commands/data-definition/alter-organization.md %}) statement. For example:

```sql
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

To edit SSO settings using the UI, see [Configure Firebolt to integrate with IdP using the UI](#integrate-with-idp-using-the-ui). 

## Delete SSO

To disable SSO login, you can delete the SSO settings using either SQL or the UI. To modify SSO settings using SQL, use the following command:

```sql
ALTER ORGANIZATION SET SSO = DEFAULT;
```

To modify SSO settings using the UI:
1. Select **Configure** to open the **Configure Space**, then choose **SSO**.

2. Select **Clear SSO configuration**.

3. Select **Update changes**.


After the SSO configuration is deleted:  
- Users who were created through SSO will remain in your organization but will no longer be able to log in to Firebolt unless password-based login is enabled for them. You can enable this using the [ALTER LOGIN]({% link sql_reference/commands/access-control/alter-login.md %}) command.  
- All logins with `is_sso_provisioned=true` will automatically be updated to `sso_provisioned=false`.