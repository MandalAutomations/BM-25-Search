# Configuring interactive maps

You can enable the display of interactive maps in the web interface for GitHub.com.

## About interactive maps

You can allow users of your GitHub Enterprise Server instance to create interactive maps using GeoJSON or TopoJSON syntax. For more information about creation of interactive maps, see [Creating diagrams](/en/enterprise-server@3.20/get-started/writing-on-github/working-with-advanced-formatting/creating-diagrams#creating-geojson-and-topojson-maps).

To enable interactive maps, you must provide authentication credentials for Azure Maps.

## Prerequisites

* To configure interactive maps for your instance, you must have administrative access to a tenant in Microsoft Entra ID. For more information, contact the administrator for Microsoft resources at your company, or see [Quickstart: Create a new tenant in Microsoft Entra ID](https://learn.microsoft.com/entra/fundamentals/create-new-tenant) on Microsoft Learn.

* You must know the tenant ID for your tenant in Entra ID. For more information, see [Get subscription and tenant IDs in the Azure portal](https://learn.microsoft.com/en-us/azure/azure-portal/get-subscription-tenant-id#find-your-microsoft-entra-tenant) on Microsoft Learn.

* Your instance must be able to access <https://login.microsoftonline.com>.

## Generating credentials for Azure Maps

To generate credentials for Azure Maps, you must create an application for your tenant in Entra ID, provide the application access to an Azure Maps account, and configure role-based access control (RBAC).

1. Register a new application on your Entra ID tenant. For more information, see [Quickstart: Register an application with the Microsoft identity platform](https://learn.microsoft.com/entra/identity-platform/quickstart-register-app#register-an-application) on Microsoft Learn.

   * When you specify supported account types, select **Accounts in this organizational directory only**.
2. Add a client secret. For more information, see [Quickstart: Register an application with the Microsoft identity platform](https://learn.microsoft.com/entra/identity-platform/quickstart-register-app#add-a-client-secret) on Microsoft Learn.
3. Store the value of the secret in a secure location that you can reference when you configure authentication on your GitHub Enterprise Server instance. Entra will never display the value after you leave the page.
4. Configure access to the secret by Azure Maps.

   1. While viewing the details for the application you configured on your Entra ID tenant, in the left-hand sidebar, click **API permissions**.
   2. Click **Add a permission**.
   3. Click **Azure Maps**.
   4. Select **Delegated permissions**.
   5. Under "Select permissions", select "`user_impersonation`".
   6. To save the permissions, click **Add permissions**.
5. Sign into an Azure Maps account. If you don't have an account, you can create one. For more information, see the [Azure Maps Account](https://azure.microsoft.com/en-us/products/azure-maps/) website.
6. Configure RBAC for Azure Maps. For more information, see [Authentication with Azure Maps](https://learn.microsoft.com/azure/azure-maps/azure-maps-authentication#authorization-with-role-based-access-control) and [Assign Azure roles using the Azure portal](https://learn.microsoft.com/azure/role-based-access-control/role-assignments-portal) on Microsoft Learn.

   * On your Entra ID tenant, from **Access control (IAM)**, you must assign the role of "Azure Maps Data Reader" to "User, group, or service principal", select the application you created earlier in these instructions, and complete the form.

## Enabling interactive maps

After you create an application on your Entra ID tenant and generate a secret for the use of Azure Maps, you can configure interactive maps on your GitHub Enterprise Server instance.

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

4. In the "Settings" sidebar, click **Privacy** and uncheck **Private mode**.

5. To enable interactive maps, select "Enable GeoJSON rendering".

6. Generate a 32-character string to use as a secret to prevent cross-site request forgery (CSRF). For example, you can access the administrative shell and use `openssl` on your GitHub Enterprise Server instance to generate a string. For more information, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/administering-your-instance/administering-your-instance-from-the-command-line/accessing-the-administrative-shell-ssh).

   ```shell copy
   openssl rand -hex 32
   ```

   Store the string in a secure location that you can reference in the next step.

7. Below the headings, type or paste your authentication details for Azure Maps.

   * If your instance runs GitHub Enterprise Server 3.20, below "Azure Maps API Token", type or paste your token.
   * If your instance runs GitHub Enterprise Server 3.20 or later, below the headings, type or paste the following information.

     * Optionally, to change the style of rendered maps, under "Basemap ID", type the ID for the style you'd like to use.
     * Under the headings, type or paste your authentication details.

       | Value                   | Description                                                                     | More information                                                                                                                                                                                                                |
       | :---------------------- | :------------------------------------------------------------------------------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
       | Azure Map Client ID     | Client ID for your Azure Maps account                                           | [Manage authentication in Azure Maps](https://learn.microsoft.com/azure/azure-maps/how-to-manage-authentication#view-authentication-details) on Microsoft Learn                                                                 |
       | Azure App Client ID     | Application (client) ID for the application you created on your Entra ID tenant | [Create a Microsoft Entra application and service principal that can access resources](https://learn.microsoft.com/entra/identity-platform/howto-create-service-principal-portal#sign-in-to-the-application) on Microsoft Learn |
       | Azure Tenant ID         | ID for your tenant on Entra ID                                                  | [Prerequisites](#prerequisites)                                                                                                                                                                                                 |
       | Azure App Client Secret | Client secret that you generated for the application on your Entra ID tenant    | [Generating credentials for Azure Maps](#generating-credentials-for-azure-maps)                                                                                                                                                 |
       | CSRF Secret             | 32-character string to prevent CSRF attacks                                     | See previous step.                                                                                                                                                                                                              |

8. Under the "Settings" sidebar, click **Save settings**.

   > \[!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

9. Wait for the configuration run to complete.

## Disabling interactive maps

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

4. In the "Settings" sidebar, click **Privacy** and uncheck **Private mode**.

5. To disable interactive maps, deselect "Enable GeoJSON rendering".

6. Under the "Settings" sidebar, click **Save settings**.

   > \[!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

7. Wait for the configuration run to complete.