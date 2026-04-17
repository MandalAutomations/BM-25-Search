# Working with the Gradle registry

You can configure Gradle to publish packages to the GitHub Packages Gradle registry and to use packages stored on GitHub Packages as dependencies in a Java project.

<!-- 2148AF7B-5FF8-4B28-A808-D692FEE2225A -->

## Authenticating to GitHub Packages

> \[!NOTE]
> GitHub Packages only supports authentication using a personal access token (classic). For more information, see [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

You need an access token to publish, install, and delete private, internal, and public packages.

You can use a personal access token (classic) to authenticate to GitHub Packages or the GitHub API. When you create a personal access token (classic), you can assign the token different scopes depending on your needs. For more information about packages-related scopes for a personal access token (classic), see [About permissions for GitHub Packages](/en/packages/learn-github-packages/about-permissions-for-github-packages#about-scopes-and-permissions-for-package-registries).

To authenticate to a GitHub Packages registry within a GitHub Actions workflow, you can use:

* `GITHUB_TOKEN` to publish packages associated with the workflow repository.
* A personal access token (classic) with at least `read:packages` scope to install packages associated with other private repositories (`GITHUB_TOKEN` can be used if the repository is granted read access to the package. See [Configuring a package's access control and visibility](/en/packages/learn-github-packages/configuring-a-packages-access-control-and-visibility)).

For more information about `GITHUB_TOKEN` used in GitHub Actions workflows, see [Use GITHUB\_TOKEN for authentication in workflows](/en/actions/security-guides/automatic-token-authentication#using-the-github_token-in-a-workflow). For more information about using `GITHUB_TOKEN` with Gradle, see [Publishing Java packages with Gradle](/en/actions/publishing-packages/publishing-java-packages-with-gradle#publishing-packages-to-github-packages).

### Authenticating with a personal access token

You must use a personal access token (classic) with the appropriate scopes to publish and install packages in GitHub Packages. For more information, see [Introduction to GitHub Packages](/en/packages/learn-github-packages/introduction-to-github-packages#authenticating-to-github-packages).

You can authenticate to GitHub Packages with Gradle using either Gradle Groovy or Kotlin DSL by editing your *build.gradle* file (Gradle Groovy) or *build.gradle.kts* file (Kotlin DSL) file to include your personal access token (classic). You can also configure Gradle Groovy and Kotlin DSL to recognize a single package or multiple packages in a repository.

Replace USERNAME with your GitHub username, TOKEN with your personal access token (classic), REPOSITORY with the name of the repository containing the package you want to publish, and OWNER with the name of the personal account or organization on GitHub that owns the repository. Because uppercase letters aren't supported, you must use lowercase letters for the repository owner even if the GitHub user or organization name contains uppercase letters.

> \[!NOTE]
> GitHub Packages supports `SNAPSHOT` versions of Apache Maven. To use the GitHub Packages repository for downloading `SNAPSHOT` artifacts, enable SNAPSHOTS in the POM of the consuming project or your *\~/.m2/settings.xml* file. For an example, see [Working with the Apache Maven registry](/en/packages/working-with-a-github-packages-registry/working-with-the-apache-maven-registry).

#### Example using Gradle Groovy for a single package in a repository

```shell
plugins {
    id("maven-publish")
}
publishing {
    repositories {
        maven {
            name = "GitHubPackages"
            url = uri("https://maven.pkg.github.com/OWNER/REPOSITORY")
            credentials {
                username = project.findProperty("gpr.user") ?: System.getenv("USERNAME")
                password = project.findProperty("gpr.key") ?: System.getenv("TOKEN")
            }
        }
    }
    publications {
        gpr(MavenPublication) {
            from(components.java)
        }
    }
}
```

#### Example using Gradle Groovy for multiple packages in the same repository

```shell
plugins {
    id("maven-publish") apply false
}
subprojects {
    apply plugin: "maven-publish"
    publishing {
        repositories {
            maven {
                name = "GitHubPackages"
                url = uri("https://maven.pkg.github.com/OWNER/REPOSITORY")
                credentials {
                    username = project.findProperty("gpr.user") ?: System.getenv("USERNAME")
                    password = project.findProperty("gpr.key") ?: System.getenv("TOKEN")
                }
            }
        }
        publications {
            gpr(MavenPublication) {
                from(components.java)
            }
        }
    }
}
```

#### Example using Kotlin DSL for a single package in the same repository

```shell
plugins {
    `maven-publish`
}
publishing {
    repositories {
        maven {
            name = "GitHubPackages"
            url = uri("https://maven.pkg.github.com/OWNER/REPOSITORY")
            credentials {
                username = project.findProperty("gpr.user") as String? ?: System.getenv("USERNAME")
                password = project.findProperty("gpr.key") as String? ?: System.getenv("TOKEN")
            }
        }
    }
    publications {
        register<MavenPublication>("gpr") {
            from(components["java"])
        }
    }
}
```

#### Example using Kotlin DSL for multiple packages in the same repository

```shell
plugins {
    `maven-publish` apply false
}
subprojects {
    apply(plugin = "maven-publish")
    configure<PublishingExtension> {
        repositories {
            maven {
                name = "GitHubPackages"
                url = uri("https://maven.pkg.github.com/OWNER/REPOSITORY")
                credentials {
                    username = project.findProperty("gpr.user") as String? ?: System.getenv("USERNAME")
                    password = project.findProperty("gpr.key") as String? ?: System.getenv("TOKEN")
                }
            }
        }
        publications {
            register<MavenPublication>("gpr") {
                from(components["java"])
            }
        }
    }
}
```

## Publishing a package

By default, GitHub publishes the package to an existing repository with the same name as the package. For example, GitHub will publish a package named `com.example.test` in the `OWNER/test` GitHub Packages repository.

After you publish a package, you can view the package on GitHub. For more information, see [Viewing packages](/en/packages/learn-github-packages/viewing-packages).

1. Authenticate to GitHub Packages. For more information, see [Authenticating to GitHub Packages](#authenticating-to-github-packages).
2. After creating your package, you can publish the package.

   ```shell
    gradle publish
   ```

## Using a published package

To use a published package from GitHub Packages, add the package as a dependency and add the repository to your project. For more information, see [Declaring dependencies](https://docs.gradle.org/current/userguide/declaring_dependencies.html) in the Gradle documentation.

1. Authenticate to GitHub Packages. For more information, see [Authenticating to GitHub Packages](#authenticating-to-github-packages).

2. Add the package dependencies to your *build.gradle* file (Gradle Groovy) or *build.gradle.kts* file (Kotlin DSL) file.

   Example using Gradle Groovy:

   ```shell
   dependencies {
       implementation 'com.example:package'
   }
   ```

   Example using Kotlin DSL:

   ```shell
   dependencies {
       implementation("com.example:package")
   }
   ```

3. Add the repository to your *build.gradle* file (Gradle Groovy) or *build.gradle.kts* file (Kotlin DSL) file.

   Example using Gradle Groovy:

   ```shell
   repositories {
       maven {
           url = uri("https://maven.pkg.github.com/OWNER/REPOSITORY")
           credentials {
               username = project.findProperty("gpr.user") ?: System.getenv("USERNAME")
               password = project.findProperty("gpr.key") ?: System.getenv("TOKEN")
           }
      }
   }
   ```

   Example using Kotlin DSL:

   ```shell
   repositories {
       maven {
           url = uri("https://maven.pkg.github.com/OWNER/REPOSITORY")
           credentials {
               username = project.findProperty("gpr.user") as String? ?: System.getenv("USERNAME")
               password = project.findProperty("gpr.key") as String? ?: System.getenv("TOKEN")
           }
       }
   }
   ```

## Further reading

* [Working with the Apache Maven registry](/en/packages/working-with-a-github-packages-registry/working-with-the-apache-maven-registry)
* [Deleting and restoring a package](/en/packages/learn-github-packages/deleting-and-restoring-a-package)