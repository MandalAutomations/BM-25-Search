# Enabling GitHub Packages with AWS

Set up GitHub Packages with AWS as your external storage.

> \[!WARNING]
>
> * It is critical that you configure any restrictive access policies you need for your storage bucket, because GitHub does not apply specific object permissions or additional access control lists (ACLs) to your storage bucket configuration. For example, if you make your bucket public, data in the bucket will be accessible to the public internet. For more information, see [Setting bucket and object access permissions](https://docs.aws.amazon.com/AmazonS3/latest/user-guide/set-permissions.html) in the AWS Documentation. If restrictions by IP address have been set up, please include IP addresses for your GitHub Enterprise Server instance and the end users who will be using the your GitHub Enterprise Server instance.
> * We recommend using a dedicated bucket for GitHub Packages, separate from the bucket you use for GitHub Actions storage.
> * Make sure to configure the bucket you'll want to use in the future. We do not recommend changing your storage after you start using GitHub Packages.

## Prerequisites

Before you can enable and configure GitHub Packages on your GitHub Enterprise Server instance, you need to prepare your AWS storage bucket. To prepare your AWS storage bucket, we recommend consulting the official AWS docs at [AWS Documentation](https://docs.aws.amazon.com/index.html).

Ensure your AWS access key ID and secret have the following permissions:

* `s3:PutObject`
* `s3:GetObject`
* `s3:ListBucketMultipartUploads`
* `s3:ListMultipartUploadParts`
* `s3:AbortMultipartUpload`
* `s3:DeleteObject`
* `s3:ListBucket`

## Enabling GitHub Packages with AWS external storage

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

4. In the left sidebar, click **Packages**.

5. Under "GitHub Packages", select the **Enable GitHub Packages** checkbox.

6. Under "Packages Storage", select **Amazon S3** and enter your storage bucket's details:
   * **AWS Service URL:** The service URL for your bucket. For example, if your S3 bucket was created in the `us-west-2 region`, this value should be `https://s3.us-west-2.amazonaws.com`.

     For more information, see [AWS service endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html) in the AWS documentation.

   * **AWS S3 Bucket:** The name of your S3 bucket dedicated to GitHub Packages.

   * **AWS S3 Access Key** and **AWS S3 Secret Key:** The AWS access key ID and secret key to access your bucket.

     For more information on managing AWS access keys, see the [AWS Identity and Access Management Documentation](https://docs.aws.amazon.com/iam/index.html).

7. Under the "Settings" sidebar, click **Save settings**.

   > \[!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

8. Wait for the configuration run to complete.

## Next steps

As a next step, you can customize which package ecosystems you would like to make available to end users on GitHub. For more information, see [Configuring package ecosystem support for your enterprise](/en/enterprise-server@3.20/admin/packages/configuring-package-ecosystem-support-for-your-enterprise).

For an overview of getting started with GitHub Packages on GitHub, see [Getting started with GitHub Packages for your enterprise](/en/enterprise-server@3.20/admin/packages/getting-started-with-github-packages-for-your-enterprise).