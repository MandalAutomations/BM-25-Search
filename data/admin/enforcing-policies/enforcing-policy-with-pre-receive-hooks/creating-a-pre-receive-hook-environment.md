# Creating a pre-receive hook environment

To execute pre-receive hooks, use either the default pre-receive environment, or create a custom environment.

A pre-receive environment for GitHub Enterprise Server is a Linux [`chroot`](https://en.wikipedia.org/wiki/Chroot) environment. Because pre-receive hooks execute on every push event, they should be fast and lightweight. The environment needed for such checks will typically be minimal.

GitHub Enterprise Server provides a default environment which includes these packages: `awk`, `bash`, `coreutils`, `curl`, `find`, `gnupg`, `grep`, `jq`, `sed`.

If you have a specific requirement that isn't met by this environment, such as support for a particular language, you can create and upload your own 64-bit Linux `chroot` environment.

The Git version used in the pre-receive hook environment must be at least 2.11, or if you are using libgit2 you must use at least version 0.18.
If you are using another Git implementation, it must support relative paths in the `info/alternates` file.

## Creating a pre-receive hook environment using Docker

You can use a Linux container management tool to build a pre-receive hook environment. This example uses [Debian Linux](https://www.debian.org/) and [Docker](https://www.docker.com/).

1. [Ensure Docker is installed](https://www.docker.com/) locally.
1. Create the file `Dockerfile.debian` that contains this information:

   ```dockerfile
   FROM --platform=linux/amd64 debian:stable
   RUN apt-get update && apt-get install -y git bash curl
   RUN rm -fr /etc/localtime /usr/share/zoneinfo/localtime
   ```

>[!NOTE] The Debian image includes some symlinks by default, which if not removed, may cause errors when executing scripts in the custom environment. Symlinks are removed in the last line of the example above.

1. From the working directory that contains `Dockerfile.debian`, build an image:

   ```shell
   $ docker build -f Dockerfile.debian -t pre-receive.debian .
   > [+] Building 0.6s (6/6) FINISHED                                                                   docker:desktop-linux
   > => [internal] load build definition from Dockerfile.debian
   > => [1/2] FROM docker.io/library/debian:latest@sha256:80dd3c3b9c6cecb9f1667e9290b3bc61b78c2678c02cbdae5f0fea92cc6
   > => [2/2] RUN apt-get update && apt-get install -y git bash curl
   > => exporting to image
   > => => exporting layers
   > => => writing image sha256:b57af4e24082f3a30a34c0fe652a336444a3608f76833f5c5fdaf4d81d20c3cc
   > => => naming to docker.io/library/pre-receive.debian
   ```

1. Create a container:

   ```shell
   docker create --name pre-receive.debian pre-receive.debian /bin/true
   ```

1. Export the Docker container to a `gzip` compressed `tar` file:

   ```shell
   docker export pre-receive.debian | gzip > debian.tar.gz
   ```

   This file `debian.tar.gz` is ready to be uploaded to the GitHub Enterprise Server appliance.

## Creating a pre-receive hook environment using chroot

1. Create a Linux `chroot` environment.
1. Create a `gzip` compressed `tar` file of the `chroot` directory.

   ```shell
   cd /path/to/chroot
   tar -czf /path/to/pre-receive-environment.tar.gz .
   ```

   > [!NOTE]
   > * Do not include leading directory paths of files within the tar archive, such as `/path/to/chroot`.
   > * `/bin/sh` must exist and be executable, as the entry point into the chroot environment.
   > * Unlike traditional chroots, the `dev` directory is not required by the chroot environment for pre-receive hooks.

For more information about creating a chroot environment, see [Chroot](https://wiki.debian.org/chroot) from the Debian Wiki.

## Uploading a pre-receive hook environment on GitHub Enterprise Server

1. In the top-right corner of GitHub Enterprise Server, click your profile picture, then click **Enterprise settings**.
1. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.
1. Under "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings", click **Hooks**.
1. Click **Manage environments**.
1. Click **Add environment**.
1. In the "Environment name" field, enter the desired name.
1. In the "Upload environment from a URL" field, enter the URL of the `*.tar.gz` file that contains your environment.
1. Click **Add environment**.

## Uploading a pre-receive hook environment via the administrative shell

1. Upload a readable `*.tar.gz` file that contains your environment to a web host and copy the URL or transfer the file to the GitHub Enterprise Server appliance via `scp`. When using `scp`, you may need to adjust the `*.tar.gz` file permissions so that the file is world readable.
1. Connect to the administrative shell.
1. Use the `ghe-hook-env-create` command and type the name you want for the environment as the first argument and the full local path or URL of a `*.tar.gz` file that contains your environment as the second argument.

   ```shell
   admin@ghe-host:~$ ghe-hook-env-create DebianTestEnv /home/admin/debian.tar.gz
   > Pre-receive hook environment 'DebianTestEnv' (2) has been created.
   ```