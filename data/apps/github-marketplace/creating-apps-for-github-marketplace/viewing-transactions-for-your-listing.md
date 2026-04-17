# Viewing transactions for your listing

The GitHub Marketplace transactions page allows you to download and view all transactions for your GitHub Marketplace listing. You can view transactions for the past day (24 hours), week, month, or for the entire duration of time that your GitHub App has been listed.

> \[!NOTE]
> This article applies to publishing apps in GitHub Marketplace only. For more information about publishing GitHub Actions in GitHub Marketplace, see [Publishing actions in GitHub Marketplace](/en/actions/creating-actions/publishing-actions-in-github-marketplace).

> \[!NOTE]
> Because it takes time to aggregate data, you'll notice a slight delay in the dates shown. When you select a time period, you can see exact dates for the metrics at the top of the page.

You can view or download the transaction data to keep track of your subscription activity. Click the **Export CSV** button to download a `.csv` file. You can also select a period of time to view and search within the transaction page.

## Transaction data fields

* **date:** The date of the transaction in `yyyy-mm-dd` format.
* **app\_name:** The app name.
* **user\_login:** The login of the user with the subscription.
* **user\_id:** The id of the user with the subscription.
* **user\_type:** The type of GitHub account, either `User` or `Organization`.
* **country:** The three letter country code.
* **amount\_in\_cents:** The amount of the transaction in cents. When a value is less the plan amount, the user upgraded and the new plan is prorated. A value of zero indicates the user canceled their plan.
* **renewal\_frequency:** The subscription renewal frequency, either `Monthly` or `Yearly`.
* **marketplace\_listing\_plan\_id:** The `id` of the subscription plan.
* **region:** The name of the region present in billing address.
* **postal\_code:** The postal code value present in billing address.

![Screenshot of the "Transactions" tab in an app listing. Transactions from the past week are listed in a table with a search field.](/assets/images/marketplace/marketplace-transactions.png)

## Accessing GitHub Marketplace transactions

To access GitHub Marketplace transactions:

1. In the upper-right corner of any page on GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**.

2. In the left sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code" aria-label="code" role="img"><path d="m11.28 3.22 4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L13.94 8l-3.72-3.72a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215Zm-6.56 0a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042L2.06 8l3.72 3.72a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L.47 8.53a.75.75 0 0 1 0-1.06Z"></path></svg> Developer settings**.

3. In the left sidebar, click either **OAuth Apps** or **GitHub Apps** depending on the GitHub Marketplace listing you'd like to manage.

   > \[!NOTE]
   > You can also manage your listing by navigating to <https://github.com/marketplace/manage>.

   ![Screenshot of the sidebar on the "Developer Settings" page of GitHub. Options labeled "GitHub Apps" and "OAuth apps" are outlined in dark orange.](/assets/images/settings/apps-choose-app.png)

4. Select the GitHub App that you'd like to view transactions for.

5. On the app settings landing page, scroll down to the Marketplace section and click **List in Marketplace**. If you already have a Marketplace draft listing, click **Edit Marketplace listing**. The Marketplace section is only visible if you allowed your app to be installed by any user or organization when registering the app. For more information, see the list of [Marketplace requirements](/en/apps/publishing-apps-to-github-marketplace/creating-apps-for-github-marketplace/requirements-for-listing-an-app).

6. Click the **Transactions** tab.

7. Optionally, select a different time period by clicking the Period dropdown in the upper-right corner of the Transactions page.