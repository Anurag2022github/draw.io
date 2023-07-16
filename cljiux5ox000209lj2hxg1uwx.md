---
title: "Managing systems using the RHEL Web console(Cockpit)"
datePublished: Fri Jun 30 2023 17:37:17 GMT+0000 (Coordinated Universal Time)
cuid: cljiux5ox000209lj2hxg1uwx
slug: managing-systems-using-the-rhel-web-consolecockpit
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688145519768/b37cbb58-d31e-4ece-9256-a8d3a47f7cf0.jpeg
tags: devops, redhat, devops-articles, shubhamlondhe, trainwithshubham

---

What is Cockpit tool?

**Cockpit is a Linux tool that allows you to perform system administration tasks via a graphical user interface (GUI), namely, a web browser**.

CHAPTER 1. GETTING STARTED USING THE RHEL WEB CONSOLE

Install the web console in Red Hat Enterprise Linux 8 and learn how to add remote hosts and monitor them in the RHEL 8 web console.

Prerequisites

 Installed Red Hat Enterprise Linux 8.

 Enabled networking.

 Registered system with appropriate subscription attached.

To obtain a subscription, see [Managing subscriptions in the web console](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/managing_systems_using_the_rhel_8_web_console/managing-subscriptions-in-the-web-console_system-management-using-the-rhel-8-web-console) .

 1.1. WHAT IS THE RHEL WEB CONSOLE

The RHEL web console is a Red Hat Enterprise Linux 8 web-based interface designed for managing and monitoring your local system, as well as Linux servers located in your network environment.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688145351527/fe78ddfc-9e9b-44a7-987f-b20f55a45746.png align="center")

 The RHEL web console enables you a wide range of administration tasks, including:

 Managing services

 Managing user accounts

 Managing and monitoring system services

 Configuring network interfaces and firewall

 Reviewing system logs

 Managing virtual machines

 Creating diagnostic reports

 Setting kernel dump configuration

 Configuring SELinux

 Updating software

 Managing system subscriptions

 The RHEL web console uses the same system APIs as you would in a terminal, and actions performed in a terminal are immediately reflected in the RHEL web console.

 You can monitor the logs of systems in the network environment, as well as their performance, displayed as graphs. In addition, you can change the settings directly in the web console or through the terminal.

 1.2. INSTALLING AND ENABLING THE WEB CONSOLE

To access the RHEL 8 web console, first enable the **cockpit.socket** service.

 Red Hat Enterprise Linux 8 includes the RHEL 8 web console installed by default in many installation variants. If this is not the case on your system, install the **cockpit** package before enabling the **cockpit.socket** service.

 Procedure

 1. If the web console is not installed by default on your installation variant, manually install the

**cockpit** package:

 **\# yum install cockpit**

 2\. Enable and start the **cockpit.socket** service, which runs a web server:

 **\# systemctl enable --now cockpit.socket**

 3\. If the web console was not installed by default on your installation variant and you are using a custom firewall profile, add the **cockpit** service to **firewalld** to open port 9090 in the firewall:

 **\# firewall-cmd --add-service=cockpit --permanent # firewall-cmd --reload**

 Verification steps

 1. To verify the previous installation and configuration, open the web console.

  1.3. LOGGING IN TO THE WEB CONSOLE

Use the steps in this procedure for the first login to the RHEL web console using a system user name and password.

 Prerequisites

 Use one of the following browsers for opening the web console:

 Mozilla Firefox 52 and later

 Google Chrome 57 and later

 Microsoft Edge 16 and later

 System user account credentials

The RHEL web console uses a specific PAM stack located at **/etc/pam.d/cockpit**. Authentication with PAM allows you to log in with the user name and password of any local account on the system.

 Procedure

 1. Open the web console in your web browser:

 Locally: [**https://localhost:9090**](https://localhost:9090)

 Remotely with the server’s hostname: [**https://example.com:9090**](https://example.com:9090)

 Remotely with the server’s IP address: [**https://192.0.2.2:9090**](https://192.0.2.2:9090)

If you use a self-signed certificate, the browser issues a warning. Check the certificate and accept the security exception to proceed with the login.

 The console loads a certificate from the **/etc/cockpit/ws-certs.d** directory and uses the last file with a **.cert** extension in alphabetical order. To avoid having to grant security exceptions, install a certificate signed by a certificate authority (CA).

 2. In the login screen, enter your system user name and password.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688145315445/714ca597-cd08-4333-85ac-756a4c8c3d86.png align="center")

 3. Optionally, click the Reuse my password for privileged tasksoption.

 If the user account you are using to log in has sudo privileges, this makes it possible to perform privileged tasks in the web console, such as installing software or configuring SELinux.

 4. Click Log In.

 After successful authentication, the RHEL web console interface opens.

 1.4. CONNECTING TO THE WEB CONSOLE FROM A REMOTE MACHINE

It is possible to connect to your web console interface from any client operating system and also from mobile phones or tablets.

 Prerequisites

 Device with a supported internet browser, such as:

 Mozilla Firefox 52 and later

 Google Chrome 57 and later

 Microsoft Edge 16 and later

 RHEL 8 server you want to access with an installed and accessible web console. For more information about the installation of the web console see [Installing the web console](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/managing_systems_using_the_rhel_8_web_console/getting-started-with-the-rhel-8-web-console_system-management-using-the-rhel-8-web-console#installing-the-web-console_getting-star).

 Procedure

 1. Open your web browser.

 2. Type the remote server’s address in one of the following formats:

 **a.** With the server’s host name: [**server.hostname.example.com**](http://server.hostname.example.com)**:port\_number**

 **b.** With the server’s IP address: **server.IP\_address:port\_number**

 3\. After the login interface opens, log in with your RHEL machine credentials.

 1.5. LOGGING IN TO THE WEB CONSOLE USING A ONE-TIME PASSWORD

If your system is part of an Identity Management (IdM) domain with enabled one-time password (OTP) configuration, you can use an OTP to log in to the RHEL web console.

 IMPORTANT

 It is possible to log in using a one-time password only if your system is part of an Identity Management (IdM) domain with enabled OTP configuration. For more information about OTP in IdM, see [One-time password in Identity Management](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/configuring_and_managing_identity_management/logging-in-to-the-ipa-web-ui-using-one-time-passwords_configuring-and-managing-idm#one-time-password-authentication-in-identity-man) .

 Prerequisites

 The RHEL web console has been installed. For details, see [Installing the web console](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/managing_systems_using_the_rhel_8_web_console/getting-started-with-the-rhel-8-web-console_system-management-using-the-rhel-8-web-console#installing-the-web-console_getting-star).

 An Identity Management server with enabled OTP configuration.

 For details, see [One-time password in Identity Management](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/configuring_and_managing_identity_management/logging-in-to-the-ipa-web-ui-using-one-time-passwords_configuring-and-managing-idm#one-time-password-authentication-in-identity-man) .

 A configured hardware or software device generating OTP tokens.

  Procedure

 1. Open the RHEL web console in your browser:

 Locally: [**https://localhost:PORT\_NUMBER**](https://localhost:PORT_NUMBER)

 Remotely with the server hostname: [**https://example.com:PORT\_NUMBER**](https://example.com:PORT_NUMBER)

 Remotely with the server IP address:

##### [**https://EXAMPLE.SERVER.IP.ADDR:PORT\_NUMBER**](https://EXAMPLE.SERVER.IP.ADDR:PORT_NUMBER)

If you use a self-signed certificate, the browser issues a warning. Check the certificate and accept the security exception to proceed with the login.

 The console loads a certificate from the **/etc/cockpit/ws-certs.d** directory and uses the last file with a **.cert** extension in alphabetical order. To avoid having to grant security exceptions, install a certificate signed by a certificate authority (CA).

 2. The Login window opens. In the Login window, enter your system user name and password.

 3. Generate a one-time password on your device.

 4. Enter the one-time password into a new field that appears in the web console interface after you confirm your password.

 5. Click Log in.

 6. Successful login takes you to the Overview page of the web console interface.

 1.6. RESTARTING THE SYSTEM USING THE WEB CONSOLE

You can use the web console to restart a RHEL system that the web console is attached to.

 Prerequisites

 The web console is installed and accessible. For details, see [Installing the web console](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/managing_systems_using_the_rhel_8_web_console/index#installing-the-web-console_getting-started-with-the-rhel-8-web-console).

 Procedure

 1. Log into the RHEL 8 web console.

For details, see [Logging in to the web console](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/managing_systems_using_the_rhel_8_web_console/index#logging-in-to-the-web-console_getting-started-with-the-rhel-8-web-console) .

 2. Click Overview.

 3. Click the Restart restart button.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688145266485/9811789d-9ddf-46fa-bd65-c8be12f0af27.png align="center")

 4. If any users are logged into the system, write a reason for the restart in the Restart dialog box.

 5. Optional: In the Delay drop down list, select a time interval.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688145256290/1fa95f53-7b55-4517-a385-e472aba85cf2.png align="center")

 6. Click Restart.

 1.7. SHUTTING DOWN THE SYSTEM USING THE WEB CONSOLE

You can use the web console to shut down a RHEL system that the web console is attached to.

 Prerequisites

 The web console is installed and accessible. For details, see [Installing the web console](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/managing_systems_using_the_rhel_8_web_console/index#installing-the-web-console_getting-started-with-the-rhel-8-web-console).

 Procedure

 1. Log into the RHEL 8 web console.

For details, see [Logging in to the web console](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/managing_systems_using_the_rhel_8_web_console/index#logging-in-to-the-web-console_getting-started-with-the-rhel-8-web-console) .

 2. Click Overview.

 3. In the Restart drop down list, select Shut Down.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688145241540/4735b4c8-639b-4488-ae32-32bbef1e0664.png align="center")

4\. If any users are logged in to the system, write a reason for the shutdown in the Shut Down dialog box.

 5. Optional: In the Delay drop down list, select a time interval.

 6. Click Shut Down.

1.8. CONFIGURING TIME SETTINGS USING THE WEB CONSOLE

You can set a time zone and synchronize the system time with a Network Time Protocol (NTP) server.

 Prerequisites

 he web console is installed and accessible. For details, see [Installing the web console](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/managing_systems_using_the_rhel_8_web_console/getting-started-with-the-rhel-8-web-console_system-management-using-the-rhel-8-web-console#installing-the-web-console_getting-star).

 Procedure

 1. Log in to the RHEL 8 web console.

For details, see [Logging in to the web console](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/managing_systems_using_the_rhel_8_web_console/getting-started-with-the-rhel-8-web-console_system-management-using-the-rhel-8-web-console#logging-in-to-the-web-console_getting-s) .

 2. Click the current system time in Overview.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688145225950/bb7e5c7e-ab1d-4736-8259-4dfafd12aca3.png align="center")

 3. In the Change System Time dialog box, change the time zone if necessary.

 4. In the Set Time drop down menu, select one of the following:

 Manually

Use this option if you need to set the time manually, without an NTP server.

Automatically using NTP server

This is a default option, which synchronizes time automatically with the preset NTP servers.

Automatically using specific NTP servers

Use this option only if you need to synchronize the system with a specific NTP server. Specify the DNS name or the IP address of the server.

 5. Click Change.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688145212938/62f5cd45-289d-4609-b198-b303b0049f34.png align="center")

 Verification steps

 Check the system time displayed in the System tab.

 Additional resources

 [Using the Chrony suite to configure NTP](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/configuring_basic_system_settings/index#using-chrony-to-configure-ntp) .

 1.9. JOINING A RHEL 8 SYSTEM TO AN IDM DOMAIN USING THE WEB CONSOLE

You can use the web console to join the Red Hat Enterprise Linux 8 system to the Identity Management (IdM) domain.

 Prerequisites

 The IdM domain is running and reachable from the client you want to join.

 You have the IdM domain administrator credentials.

 Procedure

 1. Log into the RHEL web console.

For details, see [Logging in to the web console](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/managing_systems_using_the_rhel_8_web_console/index#logging-in-to-the-web-console_getting-started-with-the-rhel-8-web-console) .

 2. Open the System tab.

 3. Click **Join Domain**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688145183936/b03c2c4a-88a2-4fc7-9a7f-e44756764a47.png align="center")

 4. In the Join a Domain dialog box, enter the host name of the IdM server in the Domain Address

field.

 5. In the Authentication drop down list, select if you want to use a password or a one-time password for authentication.

![](file:///C:\Users\anura\AppData\Local\Temp\~tmw0\1ba83709.tmp\img00004.PNG align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688145171937/32591883-28c3-4808-ba67-030f7cffa84a.png align="center")

6\. In the Domain Administrator Name field, enter the user name of the IdM administration account.

7\. In the password field, add the password or one-time password according to what you selected in the Authentication drop down list earlier.

8\. Click **Join**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688145148352/1aa1e62d-5322-4d25-b22e-686fe9aedad8.png align="center")

 Verification steps

 1. If the RHEL 8 web console did not display an error, the system has been joined to the IdM domain and you can see the domain name in the System screen.

 **2\.** To verify that the user is a member of the domain, click the Terminal page and type the **id**

command:**$ id**

##### **euid=548800004(example\_user) gid=548800004(example\_user) groups=548800004(example\_user) context=unconfined\_u:unconfined\_r:unconfined\_t:s0- s0:c0.c1023**

 Additional resources

 [Planning Identity Management](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/planning_identity_management/index)

 [Installing Identity Management](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/installing_identity_management/index)

 [Configuring and managing Identity Management](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/configuring_and_managing_identity_management/index)

 1.10. DISABLING SMT TO PREVENT CPU SECURITY ISSUES USING THE WEB CONSOLE

Disable Simultaneous Multi Threading (SMT) in case of attacks that misuse CPU SMT. Disabling SMT can mitigate security vulnerabilities, such as L1TF or MDS.

 IMPORTANT

 Disabling SMT might lower the system performance.

 Prerequisites

 The web console must be installed and accessible. For details, see [Installing the web console](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/managing_systems_using_the_rhel_8_web_console/index#getting-started-with-the-rhel-8-web-console_system-management-using-the-RHEL-8-web-console).

 Procedure

 1. Log in to the RHEL 8 web console.

For details, see [Logging in to the web console](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/managing_systems_using_the_rhel_8_web_console/index#logging-in-to-the-web-console_getting-started-with-the-rhel-8-web-console) .

 2. Click System.

 3. In the Hardware item, click the hardware information.

 4. In the CPU Security item, click Mitigations.

If this link is not present, it means that your system does not support SMT, and therefore is not vulnerable.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688145117990/dcb01e1e-c52d-477b-b9fe-42de5bf94e88.png align="center")

 5. In the CPU Security Toggles, switch on the Disable simultaneous multithreading (nosmt)

option.

 6. Click on the Save and rebootbutton.

 After the system restart, the CPU no longer uses SMT.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688145104179/8787ba1c-0f13-4dac-b4af-547342cc596a.png align="center")

 Additional resources

 [L1TF - L1 Terminal Fault Attack - CVE-2018-3620 & CVE-2018-3646](https://access.redhat.com/security/vulnerabilities/L1TF)

 [MDS - Microarchitectural Data Sampling - CVE-2018-12130, CVE-2018-12126, CVE-2018-12127, and CVE-2019-11091](https://access.redhat.com/security/vulnerabilities/mds)

 1.11. ADDING A BANNER TO THE LOGIN PAGE

Companies or agencies sometimes need to show a warning that usage of the computer is for lawful purposes, the user is subject to surveillance, and anyone trespassing will be prosecuted. The warning must be visible before login. Similarly to SSH, the web console can optionally show the content of a banner file on the login screen. To enable banners in your web console sessions, you need to modify the

**/etc/cockpit/cockpit.conf** file. Note that the file is not required and you may need to create it manually.

 Prerequisites

 The web console is installed and accessible. For details, see [Installing the web console](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/managing_systems_using_the_rhel_8_web_console/index#installing-the-web-console_getting-started-with-the-rhel-8-web-console).

 You must have sudo privileges.

 Procedure

 1. Create the **/etc/issue.cockpit** file in a text editor of your preference if you do not have it yet. Add the content you want to display as the banner to the file.

Do not include any macros in the file as there is no re-formatting done between the file content and the displayed content. Use intended line breaks. It is possible to use ASCII art.

 2. Save the file.

 3. Open or create the **cockpit.conf** file in the **/etc/cockpit/** directory in a text editor of your preference.

 **$ sudo vi cockpit.conf**

 4\. Add the following text to the file:

 **\[Session\] Banner=/etc/issue.cockpit**

 5\. Save the file.

 6. Restart the web console for changes to take effect.

 **\# systemctl try-restart cockpit**

 Verification steps

 Open the web console login screen again to verify that the banner is now visible.

 Example 1.1. Adding an example banner to the login page

 1. Create an **/etc/issue.cockpit** file with a desired text using a text editor:

 **This is an example banner for the RHEL web console login page.**

 2\. Open or create the **/etc/cockpit/cockpit.conf** file and add the following text:

 **\[Session\] Banner=/etc/issue.cockpit**

 3\. Restart the web console.

 4. Open the web console login screen again.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688145074017/08ec3206-86bc-4fa7-88d5-292b87fbdf27.png align="center")

1.12. CONFIGURING AUTOMATIC IDLE LOCK IN THE WEB CONSOLE

By default, there is no idle timeout set in the web console interface. If you wish to enable an idle timeout on your system, you can do so by modifying the **/etc/cockpit/cockpit.conf** configuration file. Note that the file is not required and you may need to create it manually.

 Prerequisites

 The web console must be installed and accessible. For details, see [Installing the web console](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/managing_systems_using_the_rhel_8_web_console/index#installing-the-web-console_getting-started-with-the-rhel-8-web-console).

 You must have sudo privileges.

 Procedure

 1. Open or create the **cockpit.conf** file in the **/etc/cockpit/** directory in a text editor of your preference.

 **$ sudo vi cockpit.conf**

 2\. Add the following text to the file:

 **\[Session\] IdleTimeout=X**

 Substitute X with a number for a time period of your choice in minutes.

 3. Save the file.

 4. Restart the web console for changes to take effect.

 **\# systemctl try-restart cockpit**

 Verification steps

 Check if the session logs you out after a set pe