# Configuring TLS

You can configure Transport Layer Security (TLS) on GitHub.com so that you can use a certificate that is signed by a trusted certificate authority.

## About Transport Layer Security

TLS, which replaced SSL, is enabled and configured with a self-signed certificate when GitHub Enterprise Server is started for the first time. As self-signed certificates are not trusted by web browsers and Git clients, these clients will report certificate warnings until you disable TLS or upload a certificate signed by a trusted authority, such as Let's Encrypt.

The GitHub Enterprise Server appliance will send HTTP Strict Transport Security headers when SSL is enabled. Disabling TLS will cause users to lose access to the appliance, because their browsers will not allow a protocol downgrade to HTTP. For more information, see [HTTP Strict Transport Security (HSTS)](https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security) on Wikipedia.

> \[!WARNING]
> When terminating HTTPS connections on a load balancer, the requests from the load balancer to GitHub Enterprise Server also need to use HTTPS. Downgrading the connection to HTTP is not supported.

To allow users to use FIDO U2F for two-factor authentication or deploy GitHub Pages sites with GitHub Actions, you must enable TLS for your instance. For more information, see [Configuring two-factor authentication](/en/enterprise-server@3.20/authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication).

## Prerequisites

To use TLS in production, you must have a certificate in an unencrypted PEM format signed by a trusted certificate authority. To use a certificate signed by an internal certificate authority, you must install the root certificate and any intermediate certificates. For more information, see [Troubleshooting TLS errors](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/troubleshooting-tls-errors#installing-self-signed-or-untrusted-certificate-authority-ca-root-certificates).

Your certificate will also need Subject Alternative Names configured for the subdomains listed in [Enabling subdomain isolation](/en/enterprise-server@3.20/admin/configuration/configuring-network-settings/enabling-subdomain-isolation#about-subdomain-isolation) and will need to include the full certificate chain if it has been signed by an intermediate certificate authority. For more information, see [Subject Alternative Name](https://en.wikipedia.org/wiki/SubjectAltName) on Wikipedia.

You can generate a certificate signing request (CSR) for your instance using the `ghe-ssl-generate-csr` command. For more information, see [Command-line utilities](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/command-line-utilities#ghe-ssl-generate-csr).

Your key must be an RSA key and must not have a passphrase. For more information, see [Troubleshooting TLS errors](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/troubleshooting-tls-errors#removing-the-passphrase-from-your-key-file).

## Uploading a custom TLS certificate

> \[!WARNING]
> Configuring TLS causes a small amount of downtime for your GitHub Enterprise Server instance.

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

4. In the "Settings" sidebar, click **Privacy** and uncheck **Private mode**.

5. Select **TLS only (recommended)**.

6. Under "TLS Protocol support", select the protocols you want to allow.

7. Under "Certificate", click **Choose File**, then choose a TLS certificate or certificate chain (in PEM format) to install. This file will usually have a *.pem*, *.crt*, or *.cer* extension.

8. Under "Unencrypted key", click **Choose File**, then choose an RSA key (in PEM format) to install. This file will usually have a *.key* extension.

9. Under the "Settings" sidebar, click **Save settings**.

   > \[!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

10. Wait for the configuration run to complete.

## About Let's Encrypt support

Let's Encrypt is a public certificate authority that issues free, automated TLS certificates that are trusted by browsers using the ACME protocol. You can automatically obtain and renew Let's Encrypt certificates on your appliance without any required manual maintenance.

To use Let's Encrypt automation, your appliance must be configured with a hostname that is publicly accessible over HTTP. The appliance must also be allowed to make outbound HTTPS connections.

When you enable automation of TLS certificate management using Let's Encrypt, your GitHub Enterprise Server instance will contact the Let's Encrypt servers to obtain a certificate. To renew a certificate, Let's Encrypt servers must validate control of the configured domain name with inbound HTTP requests.

You can also use the `ghe-ssl-acme` command line utility on your GitHub Enterprise Server instance to automatically generate a Let's Encrypt certificate. For more information, see [Command-line utilities](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/command-line-utilities#ghe-ssl-acme).

## Configuring TLS using Let's Encrypt

To use Let's Encrypt automation, your appliance must be configured with a hostname that is publicly accessible over HTTP. The appliance must also be allowed to make outbound HTTPS connections.

> \[!WARNING]
> Configuring TLS causes a small amount of downtime for your GitHub Enterprise Server instance.

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

4. In the "Settings" sidebar, click **Privacy** and uncheck **Private mode**.

5. Select **TLS only (recommended)**.

6. Select **Enable automation of TLS certificate management using Let's Encrypt**.

7. Under the "Settings" sidebar, click **Save settings**.

   > \[!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

8. Wait for the configuration run to complete.

9. In the "Settings" sidebar, click **Privacy** and uncheck **Private mode**.

10. Click **Request TLS certificate**.

11. Wait for the "Status" to change from "STARTED" to "DONE".

    ![Screenshot of the "Requesting TLS Certificate" dialog. At the top of the dialog, "STATUS: DONE" is highlighted with an orange outline.](/assets/images/enterprise/management-console/lets-encrypt-status.png)

12. Click **Save configuration**.

### Troubleshooting TLS with Let's Encrypt

You can troubleshoot issues that affect your TLS certificate from Let's Encrypt.

#### Error: "Security error prevented the resource from being loaded"

In some cases, end users may report that pages for services on your GitHub Enterprise Server instance respond with the following error in a browser's developer tools.

```text
Security error prevented the resource from being loaded
```

To resolve these errors, you must update the Subject Alternative Names (SANs) your Let's Encrypt certificate by reissuing the certificate. Replacement of an instance's certificate requires user-facing downtime.

1. Communicate the upcoming downtime to your users, and consider enabling maintenance mode. For more information, see the following articles.

   * [Customizing user messages for your enterprise](/en/enterprise-server@3.20/admin/managing-accounts-and-repositories/communicating-information-to-users-in-your-enterprise/customizing-user-messages-for-your-enterprise#creating-a-mandatory-message)
   * [Enabling and scheduling maintenance mode](/en/enterprise-server@3.20/admin/administering-your-instance/configuring-maintenance-mode/enabling-and-scheduling-maintenance-mode)

2. SSH into your GitHub Enterprise Server instance. If your instance comprises multiple nodes, for example if high availability or geo-replication are configured, SSH into the primary node. If you use a cluster, you can SSH into any node. Replace HOSTNAME with the hostname for your instance, or the hostname or IP address of a node. For more information, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh).

   ```shell copy
   ssh -p 122 admin@HOSTNAME
   ```

3. To disable Let's Encrypt, run the following command.

   ```shell copy
   ghe-ssl-acme -d
   ```

4. To clear the existing settings for Let's Encrypt, run the following command.

   ```shell copy
   ghe-ssl-acme -x
   ```

5. To request and install a new certificate from Let's Encrypt, run the following command.

   ```shell copy
   ghe-ssl-acme -e
   ```

6. To apply the configuration, run the following command.

   > \[!NOTE]
   > During a configuration run, services on your GitHub Enterprise Server instance may restart, which can cause brief downtime for users.

   ```shell copy
   ghe-config-apply
   ```

7. Wait for the configuration run to complete.

8. If you configured a user message or maintenance mode, remove the message and disable maintenance mode.

## Configuring cipher suites and cryptographic algorithms

You can configure the cipher suites and cryptographic algorithms that GitHub Enterprise Server uses for TLS and SSH connections. For more information, see [Configuring TLS and SSH ciphers](/en/enterprise-server@3.20/admin/configuring-settings/hardening-security-for-your-enterprise/configuring-tls-and-ssh-ciphers).