# Creating custom properties for repositories in your enterprise

Create and apply custom properties to categorize and manage repositories across your enterprise.

Custom properties allow you to decorate your repositories with information such as compliance frameworks, data sensitivity, or project details. Custom properties are private and can only be viewed by people with read permissions to the repository. An enterprise can have up to 100 property definitions. An allowed value list can have up to 200 items.

Defining custom properties at the enterprise level allows you to create consistent values that users can apply to repositories. With custom properties in place, you can apply consistent governance across repositories in your enterprise by creating a ruleset or repository policy targeting repositories with certain properties.

## Allowed characters

Custom property names and values may only contain certain characters:

* Names: `a-z`, `A-Z`, `0-9`, `_`, `-`, `$`, `#`
* Values: All printable ASCII characters except `"`

## Who can set and view values for custom properties I define?

After you define a custom property, users can set a value for that property in repositories in the enterprise. See [Managing custom properties for repositories in your organization](/en/enterprise-cloud@latest/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization#setting-values-for-repositories-in-your-organization).

* As an enterprise owner, you can set a default value for required properties.
* Organization owners can set values in their organization, either across repositories or at the repository level.
* If enabled, people with repository access, or the `custom properties` fine-grained permission, can set and update the property value for their repository.

People with read permissions to a repository can view the custom property values for that repository.

Additionally, organization owners can search for repositories in their organization by custom property values. See [Managing custom properties for repositories in your organization](/en/enterprise-cloud@latest/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization#searching-and-filtering-repositories-by-custom-property-values).

## Adding custom properties

You can add custom properties to your enterprise to make those properties available in all of your organizations.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

2. In the left sidebar, under "Policies", click **Custom properties**.

3. To add a new custom property, in the upper-right corner, click **New property**.

4. Enter a name, description, and type for the custom property. The name must be unique across all of your organizations, can't contain spaces, and cannot exceed 75 characters in length.

5. Optionally, select **Allow repository actors to set this property**. When enabled, repository users and apps with the repository-level `custom properties` fine-grained permission will be able to set and update the property value for their repository. Additionally, any actor creating a repository can set the property on the repository.

6. Optionally, select **Require this property for all repositories** and add a default value. This means that you require that all repositories in your enterprise have a value for this property. Repositories that don’t have an explicit value for this property will inherit the default value.

   * Optionally, you can select **Require explicit user-specified values**. When this option is enabled, users and apps with permission to set property values must provide an explicit value when setting properties, creating repositories, or transferring repositories. Repositories that don't yet have an explicit value will still inherit the default value.

7. Click **Save property**.

## Next steps

Apply policies to repositories based on their custom properties. See [Defining policies for repositories in your enterprise](/en/enterprise-cloud@latest/enterprise-onboarding/govern-people-and-repositories/create-repository-policies).