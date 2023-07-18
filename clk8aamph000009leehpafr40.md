---
title: "Patch Management & Rollbacks in Linux"
datePublished: Tue Jul 18 2023 12:41:54 GMT+0000 (Coordinated Universal Time)
cuid: clk8aamph000009leehpafr40
slug: patch-management-rollbacks-in-linux
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689683106260/ae2c3f6d-5cd2-4270-8a22-deefe80d9582.png
tags: linux, devops, linux-for-beginners, 90daysofdevops, trainwithshubham

---

### 🔥Overview

As a Linux administrator, one of the critical aspects of maintaining a secure and reliable system is effective patch management. In this blog post, we'll delve into what patch management is, why it's essential, and how the process of patching and rolling back works in Linux.

**👍Patch Management: An Overview**

Patch management refers to the process of keeping a computer system up-to-date with the latest software updates, fixes, and security patches. These updates are released by software vendors, including the Linux community, to address various issues such as security vulnerabilities, bugs, performance improvements, and feature enhancements.

Proper patch management is crucial for several reasons:

1. **Security:** Unpatched systems are vulnerable to various cyberthreats. Regularly applying security patches helps protect your Linux system from potential exploits and attacks.
    
2. **Stability:** Patches not only address security concerns but also fix bugs and improve overall system stability, leading to a more reliable computing environment.
    
3. **Performance:** Some patches can optimise system performance, ensuring your Linux system runs efficiently.
    
4. **Compatibility:** Staying updated with patches ensures compatibility with newer software and hardware releases.
    

**The Patching Process in Linux:**

The patching process in Linux typically involves the following steps:

1. **Monitoring:** As a Linux administrator, you need to stay informed about new updates and patches. Monitoring official channels, mailing lists, security advisories, and release notes from Linux distributions and software vendors is crucial.
    
2. **Assessment:** Before applying a patch, it's essential to assess its impact on the system. Some patches may introduce compatibility issues or conflicts with existing configurations. Having a test environment to evaluate patches before deploying them in production is a good practise.
    
3. **Backup:** Before applying any patches, it is essential to back up critical data and configurations. This step acts as a safety net in case anything goes wrong during the patching process.
    

**Applying Patches:** Linux distributions usually come with package managers (e.g., apt for Debian/Ubuntu, yum/dnf for Red Hat/CentOS/Fedora) that simplify the process of downloading and installing patches. By running specific commands, you can update individual packages or the entire system.

# **PATCH MANAGEMENT:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682144919/5b2473ef-a6a3-44ea-afe5-afbcfba3df0a.png align="center")

**Inform the application owners and stakeholders about the updates and changes.**

**Send a list of all the apps and kernel upgrades**

 **Check the module files for pre-checks -** `ls -l /var/lib/ modules/kernel-versions/mod.dep`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682170268/e2e98c38-251d-4162-9ae1-8976e76634a4.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682196755/0e8d178a-1677-4f09-8791-dc75f5adf81c.png align="center")

**To check the list of apps and kernel versions**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682296952/80ab6d43-e9a5-49f3-acf0-873f9fc713f1.png align="center")

###  **Post checks:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682371535/81e58e50-a7b5-4f2a-a052-62d79bf80771.png align="center")

* **Check the mount points if there is an error.**
    
* **Check if the panic attack errors for kernel**
    
* **Check for the latest versions of kernel**
    

**During OS patching, you check mostly the kernel and host file entries**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682380723/be23a2ff-72b7-4bd7-b501-dda3f4369a2f.png align="center")

lsblk **lists information about all available or specified block devices**. The lsblk command reads the sysfs filesystem and udev db to gather information. If the udev database is not available or lsblk is compiled without udev support, then it tries to read LABELs, UUIDs, and filesystem types from the block device.

* **After post-validation checking all these, we forward the server to the database and application teams to check.**
    
* **They will validate from there end and perform the sanity checks (functuality checks, whether their apps are running smoothly or not, and login checks).**
    
* **Lastly, they will check and confirm that the update was successful.**
    

**Roll back patches on Linux Server with Transaction ID:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682434158/7aaae2d6-0fc1-468c-8eba-174199b822b8.png align="center")

 **Command yum history list all gives all the ID's.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682461084/df1d4463-61d5-437d-859a-6d7faa07c146.png align="center")

**<mark>You</mark> *<mark> cannot roll back to the previous version of the kernel.In case you want the old kernel, we need to interrupt the GRUB and then start the process</mark>*<mark>.</mark>**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682532419/21b22b0d-e083-4738-8b12-ea1db02dd8d4.png align="center")

 **Roll back the previous versions using the command:**`-yum history undo 10 (Transaction ID)`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682557929/a78ce97e-59ad-4164-a4d1-ba1b45718f46.png align="center")

 **The downgrade of the packages is visible in the screenshot**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682570335/030940cd-e903-4b69-96cf-cdafd17a6f01.png align="center")

**After every rollback, you need to** `reboot -f.`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682583459/0d10e497-ee65-43eb-add3-203a1b8b3d74.png align="center")

**Check the kernel (glibc) version Previous and current versions can be seen**

**Once done, check with the application team for sanity checks.**

###  ***Troubleshooting:***

**Issues after Patching Activity(Recreate kernel panic issue, then try to fix it.)**

**After a post-patch, sometimes the drive or image of the kernel gets corrupted.**

**<mark>Boot process BIOS first Initramfs runs in GRUB file then kernel boots up and systemd service runs all the processes</mark>**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682683784/55268928-eacb-4b3d-be77-3d2e7c75e7db.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682704342/746b3f58-56c3-4d98-800d-0bcd82a2cfc8.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682728436/9845a3f8-a038-458c-9bc4-b00e479a6642.png align="center")

**You change the priority of the boot menu to CD-ROM and save changes**

**Go to rescue mode and need to recreate the file**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682754669/ccea0b79-709e-4aa6-96f6-dc646a1205e0.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682761060/45b1016c-04ef-465e-b36a-74c458fc2ef8.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682767512/5359e7d0-aa91-46c7-b4e5-3e4bc8164aa3.png align="center")

**Changing the root fs to different mount points**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682810910/809cfa18-a95a-494a-a1a3-b5ee81c950f0.png align="center")

 `Dracut command` **to recreate the initramfs image and file**

**Once the image is created, reboot and change the priority to hard drive in boot.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689682789069/966bb5b2-792c-46de-8949-7c8050479634.png align="center")

To check on the patching management in detail, please check the below video

%[https://www.youtube.com/watch?v=Q3NEEJj49l4]