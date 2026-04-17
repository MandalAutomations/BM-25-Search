# Configuring authentication and provisioning with PingFederate

Set up PingFederate as an identity provider (IdP) for Enterprise Managed Users on GitHub.com or GHE.com.

When you use Enterprise Managed Users, SAML SSO controls and secures access to enterprise resources like repositories, issues, and pull requests. SCIM automatically creates user accounts and manages access to your enterprise when you make changes on your IdP. You can also synchronize teams on GitHub with groups on your IdP. For more information, see [About Enterprise Managed Users](/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/about-enterprise-managed-users).

## Overview

This guide will help you to set up both SAML authentication and SCIM provisioning for GitHub on PingFederate.

Before you start, please note the following:

* This guide is based on PingFederate version 12.1. Instructions may vary for other versions.
* This guide provides the minimal steps to configure a working setup. Because your identity directory may be connected to PingFederate differently, you’ll need to pick the correct data attributes for SAML and SCIM based on what is available from your backing data store.

## Prerequisites

If you're configuring SCIM provisioning for a new enterprise, make sure to complete all previous steps in the initial configuration process. See [Getting started with Enterprise Managed Users](/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/getting-started-with-enterprise-managed-users).

In addition:

* You must have installed the "GitHub EMU connector" on PingFederate. To download and install the connector, see [Install the provisioner](https://docs.pingidentity.com/integrations/github/github_emu_provisioner/pf_gh_emu_install_the_provisioner.html) in the PingIdentity documentation.
* To provision users with SCIM, you must use an LDAP server as the backing data store.
* You may need to configure the firewall in PingFederate to allow outbound connections to the SCIM endpoints on GitHub:
  * For **GitHub.com**: `https://api.github.com/scim/v2/enterprises/ENTERPRISE`
  * For **GHE.com**: `https://api.SUBDOMAIN.ghe.com/scim/v2/enterprises/SUBDOMAIN`
* PingFederate's "provisioner mode" must be set to a value that allows SCIM provisioning. See the "Before you begin" section in PingIdentity's [Configuring outbound provisioning settings](https://docs.pingidentity.com/pingfederate/latest/administrators_reference_guide/help_protocolsettingstasklet_saasglobalprovisioningsettingsstate.html) guide.
* During this procedure, you will need to upload an X509 certificate to PingFederate. You may want to create and store the certificate before proceeding. You will also need the challenge password for the certificate. See the [Example of creating an X509 certificate](#example-of-creating-an-x509-certificate) section later in this article.
* During this procedure, you will need to upload a SAML metadata file to PingFederate. If you're setting up an enterprise that uses **data residency on GHE.com**, it is easiest to create this file before you start. See [Creating a SAML metadata file for GHE.com](#creating-a-saml-metadata-file-for-ghecom).

## 1. Configure SAML

In this section you will create a SAML connector in PingFederate, set up an LDAP IdP adapter instance, and manage SAML output from your IdP adapter.

1. [Create a SAML adapter](#create-a-saml-adapter)
2. [Set up an LDAP IdP adapter instance](#set-up-an-ldap-idp-adapter-instance)
3. [Manage SAML output from your IdP adapter](#manage-saml-output-from-your-idp-adapter)

Before starting this section, ensure you have followed the previous steps in [Getting started with Enterprise Managed Users](/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/getting-started-with-enterprise-managed-users).

### Create a SAML adapter

1. Open the PingFederate administrative console.

2. Click **Applications** in the header, then click **SP Connections** in the left sidebar.

3. Click **Use a template for this connection**, then select the "GitHub EMU Connector" from the "Connection Template" dropdown.

   > \[!NOTE] If you don't see this option, the GitHub EMU Connector has not been installed. If you need assistance, contact your Ping representative.

4. To populate some fields in PingFederate's configuration, you will upload an XML file containing SAML metadata for your enterprise.
   To locate the file:

   * If you're setting up an enterprise on **GitHub.com**, you will find this file in a ZIP file attached to the "GitHub EMU Connector" on PingFederate.
   * If you're setting up an enterprise on **GHE.com**, you will create the file manually. See [Creating a SAML metadata file for GHE.com](#creating-a-saml-metadata-file-for-ghecom).

5. On the PingFederate "SP Connection" page, upload the file from the previous step as the metadata file.

6. Go to the "Connection Type" tab.

7. Select **Browser SSO Profiles**, and deselect **Outbound provisioning** (this will be enabled later).

8. Click **Next**.

9. On the "Connection Options" tab, ensure only **Browser SSO** is selected.

10. Click **Next**.

11. On the "General Info" tab, enter the following details.

    * "Partner’s Entity ID": your GitHub host URL (`https://github.com` or `https://SUBDOMAIN.ghe.com`)
    * "Connection Name": A descriptive name for your SP connection within PingFederate
    * "Base URL": your GitHub host URL (`https://github.com` or `https://SUBDOMAIN.ghe.com`)
    * "Transaction Logging": Standard
    * All other fields may be left blank.

12. Click **Next**.

13. Click **Configure Browser SSO**.

14. Click **Configure Assertion Creation**.

15. On the "Authentication Source Mapping" tab, click **Map New Adapter Instance**.

16. On the "Adapter Instance" Tab, click **Manage Adapter Instances**.

17. Click **Create New Instance**.

### Set up an LDAP IdP adapter instance

1. On the "Create Adapter Instance" page on PingFederate, on the "Type" tab, enter the following details.

   * "Instance Name": A name to identify the instance, such as `pfghadapter`
   * "Instance ID": An ID for the instance, such as `pfghadapter`
   * "Type": HTML Form IDP Adaptor
   * "Parent Instance": None

2. Click **Next**.

3. On the "IDP Adapter" tab, at the bottom of the page, click **Manage Password Credential Validators**.

4. Click **Create New Instance**.

5. On the "Type" tab, enter the following details.

   * "Instance Name": A name to identify the instance, such as `pfghdocscv`
   * "Instance ID": An ID for the instance, such as `pfghdocscv`
   * "Type": LDAP Username Password Credential Validator
   * "Parent Instance": None

6. Click **Next**.

7. On the "Instance Configuration" tab, click **Manage Data Stores**.

8. Click **Add New Data Store**.

9. On the "Data Store Type" tab, enter the following details.

   * "Instance Name": Any unique value, such as `pfghdocsds`
   * "Type": Directory (LDAP)
   * "Mask Values In Log": Deselected

10. Click **Next**.

11. On the "LDAP Configuration" tab, configure your LDAP server details.

12. Click **Test Connection**. You should see "Connectivity test was successful."

13. At the bottom of the page, click **Advanced**.

14. Click the "LDAP Binary Attributes" tab, and add `guidAttribute` and `objectGUID` as attributes.

15. Click **Done**. You should be back on the "LDAP Configuration" tab.

16. Click **Next**, then **Save**.

17. On the "Manage Data Stores" tab, click **Done**.

18. On the "Instance Configuration" tab, enter the following details.

    * "LDAP Datastore": The name of the data store you created above
    * "Search Base": The location in the directory where you want LDAP searches to begin
    * "Search Filter": A filter that ensures the username the user enters when signing in matches a field in the LDAP server (for example: `sAMAccountName=${username}`)
    * "Scope of Search": Subtree
    * "Case-Sensitive Matching": Selected

19. Click **Next**, **Next** again, then **Save**.

### Manage SAML output from your IdP adapter

1. On the "Manage Password Credential Validators" page, click **Done**.

2. On the "IDP Adapter" tab, enter the following details.

   * "Password Credential Validator Instance": The name of the validator instance you created above (for example `pfghdocscv`). Click **Update** to finalize your selection.
   * All other fields can be left as the defaults, or modified to your requirements.

3. Click **Next**, then **Next** again.

4. On the "Adapter Attributes" tab, enter the following details.

   * "Unique User Key Attribute": `username`

   * Next to the `username` attribute, select "Pseudonym".

   > \[!NOTE] This step is important. The adapter attribute is used to uniquely identify a user on GitHub during SCIM provisioning.

5. Click **Next**, then **Next** again.

6. Review your settings on the summary page, then click **Save**.

7. On the "IdP Adapters" tab, you should see the adapter you just created. Click **Done**.

8. On the "Adapter Instance" tab, in the "Adapter Instance" dropdown, select the adapter you just created.

9. Click **Next**.

10. On the "Mapping Method" tab, select **Use only the Adapter Contract Values in the SAML Assertion** (other selections may work, but have not been confirmed).

11. Click **Next**.

12. On the "Attribute Contract Fulfillment" tab, map the `SAML_SUBJECT` to "Adapter" as the source and `username` as the value.

    > \[!NOTE] This step is important. The normalized `SAML_SUBJECT` will need to match the normalized usernames of users provisioned by SCIM.

13. Click **Next**, **Next** again, then **Done**.

14. You should be back on the "Authentication Source Mapping" tab, and the "Adapter Instance Name" section should contain the adapter instance that you just created.

15. Click **Next**.

16. On the "Protocol Settings" tab, click **Configure Protocol Settings**.

17. For the "Assertion Consumer Service URL" add a row with the following details:

    * "Default" selected
    * "Index": 0
    * "Binding": POST
    * "Endpoint URL": `/enterprises/ENTERPRISE/saml/consume`, where ENTERPRISE is your enterprise name or subdomain

18. Click **Next**.

19. On the "Allowable SAML Bindings" tab, ensure only "POST" and "REDIRECT" are selected.

20. Click **Next**.

21. On the "Signature Policy" page, ensure only "SIGN RESPONSE AS REQUIRED" is selected.

22. Click **Next**.

23. On the "Encryption Policy" tab, ensure "NONE" is selected.

24. Click **Next**.

25. Click **Save**.

26. Click **Next** and **Done** until you reach the "Credentials" tab.

27. On the "Credentials" tab, click **Configure Credentials**, then click **Manage Certificates**.

28. On the "Certificate Management" page, click **Import**, then upload an X509 certificate (for help, see the [Example of creating an X509 certificate](#example-of-creating-an-x509-certificate) section).

29. For the "Password," use the challenge password for the certificate.

30. Click **Next**, then **Save**.

31. On the "Certificate Management" tab, you should see the certificate you just imported. Click **Done**.

32. On the "Digital Signature Settings" tab:

    * Select the certificate you just created for the "Signing Certificate."
    * You can leave the secondary certificate blank and the "Include the certificate in the signature" checkbox deselected.
    * The signing algorithm should be "RSA SHA256."

33. Click **Next**, then **Done**, then **Next**.

34. On the "Summary" tab, enable the toggle for "SSO Application Endpoint."

35. Click **Save**. You should be taken back to the list of SP connections, where you should see your newly created SP connection.

### Collect information for your SAML configuration

You will need some details from PingFederate to configure SAML on GitHub.

1. On the "SP Connections" page, in the row for your new connection, click **Select Action**, then **Export Metadata**.
2. On the "Metadata Signing" tab, in the row for your new connection, select the signing certificate you created above. To download the certificate, click **Next**, then click **Export**.
3. On PingFederate, click **System** in the header, then **Server**, then **Protocol Settings**. Check that the `SAML 2.0 ENTITY ID` is defined. Make a note of this, as you will need it for the “Issuer” field in GitHub's SAML settings.
4. Open the metadata file you downloaded, and have it ready for the next steps.

### Configure GitHub

1. Sign in to GitHub as the setup user for your enterprise.

2. Enable SAML in your enterprise settings. See [Configuring SAML single sign-on for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/managing-iam/configuring-authentication-for-enterprise-managed-users/configuring-saml-single-sign-on-for-enterprise-managed-users#configure-saml-sso-for-enterprise-managed-users).

3. Enter the following values from the SAML metadata file from the previous section.

   * For the "Single sign-on URL," use the `location` value of the `<md: SingleSignOnService>` field. This should be a URL ending `/idp/SSO.saml2`.
   * For the "Issuer," use the `entityId` value of the `<md: EntityDescriptor>` field (a URL).

4. For the "Verification certificate," upload the X509 certificate file that you created earlier.

5. Click **Save settings**.

## 2. Configure SCIM

In this section, you'll configure SCIM settings and attribute mapping on PingFederate.

1. [Configure SCIM settings](#configure-scim-settings)
2. [Map LDAP fields to SCIM](#map-ldap-fields-to-scim)
3. [Finish configuration and test](#finish-configuration-and-test)

Before starting this section, ensure you have followed the previous steps in [Getting started with Enterprise Managed Users](/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/getting-started-with-enterprise-managed-users).

### Configure SCIM settings

1. Go back to the "SP Connections" page on PingFederate, and select the SP connection you created earlier.
2. Click the "Connection Type" tab.
3. Select **Outbound Provisioning**.
4. Ensure **Browser SSO Profiles** is selected.
5. Click **Next** until you reach the "Outbound Provisioning" tab, then click **Configure Provisioning**.
6. On the "Target" tab, enter the following details.

   * "Base URL": `https://api.github.com/scim/v2/enterprises/{enterprise}/` or `https://api.SUBDOMAIN.ghe.com/scim/v2/enterprises/SUBDOMAIN`
   * "Access Token": The personal access token (classic) created for the setup user
7. Click **Next**.
8. On the "Manage Channel" tab, click **Create**, then enter a unique channel name, such as `pfghscim`.
9. Click **Next**.
10. On the "Source" tab, choose the data store that you created earlier.
11. Click **Next**.
12. On the "Source Settings" tab, you can keep all default settings. Other settings are likely to work, but have not been confirmed.
13. Click **Next**.
14. On the "Source Location" tab, configure where in your LDAP server you would like provisioned users to come from. This will vary depending on your setup and needs. After configuring, click **Next**.

### Map LDAP fields to SCIM

On the "Attribute Mapping" tab, you will need to map fields from your LDAP server to SCIM fields. See the following list for GitHub's supported SCIM fields and the values expected in each one.

* **Username:** This will be normalized and used as the GitHub username for the provisioned user. See [Username considerations for external authentication](/en/enterprise-cloud@latest/admin/managing-iam/iam-configuration-reference/username-considerations-for-external-authentication#about-username-normalization). This must match the normalization of the subject sent with the SAML assertion that you configured with the `SAML_SUBJECT` property in PingFederate.
* **Email:** A field containing the user's email address.
* **Display Name:** A human-readable name for the user.
* **Formatted Name:** The user's full name, including all middle names, titles, and suffixes, formatted for display.
* **First Name:** The first name of the user.
* **Last Name:** The last name of the user.
* **External ID:** This identifier is generated by an IdP provider.
* **Roles:** This field should contain a string that represents the user's intended role on GitHub. Valid roles are `enterprise_owner`, `user`, `billing_manager`, and `guest_collaborator`.

When you have finished configuring these settings, click **Next**.

### Finish configuration and test

1. On the "Activation & Summary" tab, for the "Channel Status," select **Active**.
2. On the "Manage Channels" tab, click **Done**.
3. On the "Outbound Provisioning" tab, click **Save**. SCIM is now configured and enabled.
4. Wait a few minutes for provisioning to run, then open a new private browser window and navigate to GitHub.
5. Click **Sign in with SAML**. You should be redirected to the PingFederate login page.
6. You should be able to sign in with the credentials for a user in the LDAP server that has been provisioned to GitHub.

PingFederate provisioning handles users and groups independently. Users must be assigned directly in order to be provisioned. Users who are in an assigned group but not directly assigned will not be provisioned.

## Example of creating an X509 certificate

There are multiple ways to create an X509 certificate. Here is an example that may work for your requirements.

1. In a terminal window, check that OpenSSL is installed by running `openssl version`. If it's not installed, install it.

2. Generate the private key using the following command.

   ```shell copy
   openssl req -nodes -sha256 -newkey rsa:2048 -keyout MyPrivateKey.key -out MyCertificateRequest.csr
   ```

   Enter the required information, and **take note** of the challenge password you create.

3. To ensure the key was created, run the following command. A file named `MyPrivateKey.key` should be listed in the command output.

   ```shell copy
   ls | grep MyPrivateKey.key
   ```

4. Generate the certificate using the following command.

   ```shell copy
   openssl x509 -req -days 365 -sha256 -in MyCertificateRequest.csr -signkey MyPrivateKey.key -out pfgh256.crt
   ```

5. To ensure the certificate was created, run the following command. A file named `pfgh256.crt` should be listed in the command output.

   ```shell copy
   ls | grep pfgh256.crt
   ```

6. Export a PKCS #12 file using the following command. This is the file you should **upload to PingFederate**.

   ```shell copy
   openssl pkcs12 -export -in pfgh256.crt -inkey MyPrivateKey.key -out pfgh256.p12
   ```

7. To ensure the file was exported, run the following command. A file named `pfgh256.p12` should be listed in the command output.

   ```shell copy
   ls | grep pfgh256.p12
   ```

## Creating a SAML metadata file for GHE.com

Because some values differ from the metadata file that PingFederate provides for GitHub.com, you will create an XML file for your enterprise's SAML metadata manually.

1. Copy the following XML into a text editor.

   ```xml copy
   <?xml version="1.0"?>
   <md:EntityDescriptor xmlns:md="urn:oasis:names:tc:SAML:2.0:metadata"
     entityID="https://SUBDOMAIN.ghe.com/enterprises/SUBDOMAIN" cacheDuration="PT1440M">
     <md:SPSSODescriptor protocolSupportEnumeration="urn:oasis:names:tc:SAML:2.0:protocol"
       AuthnRequestsSigned="false" WantAssertionsSigned="false">
       <md:NameIDFormat>urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified</md:NameIDFormat>
       <md:AssertionConsumerService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST"
         Location="https://SUBDOMAIN.ghe.com/enterprises/SUBDOMAIN/saml/consume" isDefault="true"
         index="0"/>
     </md:SPSSODescriptor>
   </md:EntityDescriptor>
   ```

2. Replace all instances of SUBDOMAIN with your enterprise's subdomain of GHE.com. For example: `octocorp`.

3. Save the file as an XML file.

4. Return to the instructions in [Creating a SAML adapter](#create-a-saml-adapter).