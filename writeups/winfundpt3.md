# Windows Fundamentals 3

In part 3 of the Windows Fundamentals module, learn about the built-in Microsoft tools that help keep the device secure, such as Windows Updates, Windows Security, BitLocker, and more...

---

# Task 1 - Introduction

We will continue our journey exploring the Windows operating system.

To summarize the previous two rooms:

In [Windows Fundamentals 1](https://tryhackme.com/room/windowsfundamentals1xbx), we covered the desktop, the file system, user account control, the control panel, settings, and the task manager. 
In [Windows Fundamentals 2](https://tryhackme.com/room/windowsfundamentals2x0x), we covered various utilities, such as System Configuration, Computer Management, Resource Monitor, etc.

This module will attempt to provide an overview of the security features within the Windows operating system.

Launch the attached virtual machine. If you wish to access the virtual machine via Remote Desktop, use the credentials below.

Machine IP: _MACHINE_IP_

User: _administrator_

Password: _letmein123!_

![remmina](https://github.com/djiotua/tryhackme/assets/134016731/162706ec-bcc1-4f5f-8215-28983cb44523)

Accept the Certificate when prompted, and you should be logged into the remote system now.

_Note: The virtual machine may take up to 3 minutes to load._

---

_1. Read the above and start the virtual machine._

No answer needed.

---

# Task 2 - Windows Updates

Let's start things off with _Windows Update_.

Windows Update is a service provided by Microsoft to provide security updates, feature enhancements, and patches for the Windows operating system and other Microsoft products, such as Microsoft Defender.

Updates are typically released on the 2nd Tuesday of each month. This day is called _Patch Tuesday_. That doesn't necessarily mean that a critical update/patch has to wait for the next Patch Tuesday to be released. If the update is urgent, then Microsoft will push the update via the Windows Update service to the Windows devices.

Refer to the following link to see the _Microsoft Security Update Guide_ [here](https://msrc.microsoft.com/update-guide).

Windows Update is located in Settings. See below.

_Tip: Another way to access Windows Update is from the Run dialog box, or CMD, by running the command "control /name Microsoft.WindowsUpdate"._

![windows-update2](https://github.com/djiotua/tryhackme/assets/134016731/14461d4b-16ae-481d-812f-64f2dd960fb8)

In the attached VM, there are a few things to highlight. 

1. The Windows Update settings are 'managed'. (Typically, home users will not see this type of message)
2. There are no available updates available for the virtual machine. (The attached virtual machine does not have Internet access to communicate with Microsoft to obtain new updates)

![windows-update2b](https://github.com/djiotua/tryhackme/assets/134016731/9cb87cc0-b491-4593-b26a-7d83c3cdfe2b)

Throughout the years, Windows users have grown accustomed to pushing Windows Updates off to a later date or not installing the updates at all. Various reasons caused this action, one being the fact that a reboot is typically required after a Windows update.

Microsoft notably addressed this issue with Windows 10. The updates can no longer be ignored or pushed to the side until forgotten. Windows updates can only be postponed, but eventually, the update will happen, and your computer will reboot. Microsoft provides these updates to keep the device safe and secure. 

Below is an image showing how a _Restart required_ looks and the several options available regarding scheduling the restart.

![windows-update3](https://github.com/djiotua/tryhackme/assets/134016731/01ab5094-84d8-4482-9a1b-db7363d84275)

Refer to the Windows Updates [FAQ](https://support.microsoft.com/en-us/windows/windows-update-faq-8a903416-6f45-0718-f5c7-375e92dddeb2) for more information.

---

_1. There were two definition updates installed in the attached VM. On what date were these updates installed?_

  <details>
    <summary>Answer</summary>

    5/3/2021
  </details>

  <details>
    <summary>Explanation</summary>

    Using Windows Update, I went to "View update history", followed by "Definition Updates", to which they are two that were installed.
  </details>

---

# Task 3 - Windows Security

Per Microsoft, "_Windows Security is your home to manage the tools that protect your device and your data_".

In case you missed it, _Windows Security_ is also available in _Settings_.

![windows-security](https://github.com/djiotua/tryhackme/assets/134016731/f34e5f7f-9653-4f80-b0c7-cc5c165b3424)

In the above image, focus your attention on _Protection areas_.

- Virus & threat protection
- Firewall & network protection
- App & browser control
- Device security

Each following task will briefly touch on these areas.

Before proceeding, let's provide a quick comment on the status icons.

- _Green_ means your device is sufficiently protected, and there aren't any recommended actions.
- _Yellow_ means there is a safety recommendation for you to review.
- _Red_ is a warning that something needs your immediate attention.
  
Click on _Open Windows Security_. 

![windows-security2](https://github.com/djiotua/tryhackme/assets/134016731/588ac02b-1d2a-4e8c-a088-768db550074f)

_Note: Since the attached VM is a Windows Server 2019 edition, it looks different from a Windows 10 Home or Professional edition._

The below image is from a Windows 10 device.

![windows-security1b](https://github.com/djiotua/tryhackme/assets/134016731/af140ef2-6d0f-40d6-9093-18b0e10641ff)

Next, we'll look at _Virus & threat protection_.

---

_1. In the above image, which area needs immediate attention?_

  <details>
    <summary>Answer</summary>

    Virus & threat protection
  </details>

---

# Task 4 - Virus & threat protection

Virus & threat protection is divided into two parts:

- Current threats
- Virus & threat protection settings
  
The image below only focuses on _Current threats_.

![windows-security3](https://github.com/djiotua/tryhackme/assets/134016731/49be0111-242c-4287-9f44-28290b36df3b)

## Current threats

_Scan options_

- Quick scan - Checks folders in your system where threats are commonly found.
- Full scan - Checks all files and running programs on your hard disk. This scan could take longer than one hour.
- Custom scan - Choose which files and locations you want to check.

_Threat history_

- Last scan - Windows Defender Antivirus automatically scans your device for viruses and other threats to help keep it safe.
- Quarantined threats - Quarantined threats have been isolated and prevented from running on your device. They will be periodically removed.
- Allowed threats - Allowed threats are items identified as threats, which you allowed to run on your device.

_Warning: Allow an item to run that has been identified as a threat only if you are 100% sure of what you are doing._

Next is _Virus & threat protection settings_.

![windows-security4](https://github.com/djiotua/tryhackme/assets/134016731/cff88467-d2aa-42aa-a549-622ebeef3474)

## Virus & threat protection settings

_Manage settings_

- Real-time protection - Locates and stops malware from installing or running on your device.
- Cloud-delivered protection - Provides increased and faster protection with access to the latest protection data in the cloud.
- Automatic sample submission - Send sample files to Microsoft to help protect you and others from potential threats.
- Controlled folder access - Protect files, folders, and memory areas on your device from unauthorized changes by unfriendly applications.
- Exclusions - Windows Defender Antivirus won't scan items that you've excluded.
- Notifications - Windows Defender Antivirus will send notifications with critical information about the health and security of your device.

_Warning: Excluded items could contain threats that make your device vulnerable. Only use this option if you are 100% sure of what you are doing._

_Virus & threat protection updates_

- Check for updates - Manually check for updates to update Windows Defender Antivirus definitions.

_Ransomware protection_

- Controlled folder access - Ransomware protection requires this feature to be enabled, which in turn requires Real-time protection to be enabled.

_Note: Real-time protection is turned off in the attached VM to decrease the chances of performance issues. Since the VM can't reach the Internet and there aren't any threats in the VM, this is safe to do. Real-time protection should definitely be enabled in your personal Windows devices unless you have a 3rd party product that provides the same protection. Ensure it's always up-to-date and enabled._

_Tip: You can perform on-demand scans on any file/folder by right-clicking the item and selecting 'Scan with Microsoft Defender'._

The below image was taken from another Windows device to show this feature.

![windows-defender-scan](https://github.com/djiotua/tryhackme/assets/134016731/fef54c6a-9cde-4417-89c8-b6063c71525b)

---

_1. Specifically, what is turned off that Windows is notifying you to turn on?_

  <details>
    <summary>Answer</summary>

    Real-time protection
  </details>

---

# Task 5 - Firewall & network protection

What is a _firewall_?

Per Microsoft, "_Traffic flows into and out of devices via what we call ports. A firewall is what controls what is - and more importantly isn't - allowed to pass through those ports. You can think of it like a security guard standing at the door, checking the ID of everything that tries to enter or exit_".

The below image will reflect what you will see when you navigate to _Firewall & network protection_.

![windows-firewall](https://github.com/djiotua/tryhackme/assets/134016731/87c64c9e-8a96-445c-a464-2cf25477416d)

_Note: Each network may have different status icons for you._

What is the difference between the 3 (Domain, Private, and Public)?

Per Microsoft, "_Windows Firewall offers three firewall profiles: domain, private and public_".

- _Domain_ - The domain profile applies to networks where the host system can authenticate to a domain controller.
- _Private_ - The private profile is a user-assigned profile and is used to designate private or home networks.
- _Public_ - The default profile is the public profile, used to designate public networks such as Wi-Fi hotspots at coffee shops, airports, and other locations.

If you click on any firewall profile, another screen will appear with two options: _turn the firewall on/off_ and _block all incoming connections_.

![windows-firewall2](https://github.com/djiotua/tryhackme/assets/134016731/6bffbcab-b40b-4db9-b468-6df77354a6c7)

_Warning: Unless you are 100% confident in what you are doing, it is recommended that you leave your Windows Defender Firewall enabled._

_Allow an app through firewall_

![windows-firewall3](https://github.com/djiotua/tryhackme/assets/134016731/ca2b3b03-bdad-4b0d-b049-3d2d72b25c0a)

You can view what the current settings for any firewall profile are. In the above image, several apps have access in the Private and/or Public firewall profile. Some of the apps will provide additional information if it's available via the _Details_ button.

_Advanced Settings_

![windows-firewall4](https://github.com/djiotua/tryhackme/assets/134016731/0f1ab5c7-9266-428c-b8d0-b4e0b58d6b6c)

Configuring the _Windows Defender Firewall_ is for advanced Windows users. Refer to the following Microsoft documentation on best practices [here](https://learn.microsoft.com/en-us/windows/security/operating-system-security/network-security/windows-firewall/best-practices-configuring).

_Tip: Command to open the Windows Defender Firewall is WF.msc._

---

_1. If you were connected to airport Wi-Fi, what most likely will be the active firewall profile?_

  Hint: xyz network

  <details>
    <summary>Answer</summary>

    Public network
  </details>

---

# Task 6 - App & browser control

In this section, you can change the settings for the _Microsoft Defender SmartScreen_.

Per Microsoft, "_Microsoft Defender SmartScreen protects against phishing or malware websites and applications, and the downloading of potentially malicious files_".

Refer to the official Microsoft document for more information on Microsoft Defender SmartScreen [here](https://learn.microsoft.com/en-us/windows/security/operating-system-security/virus-and-threat-protection/microsoft-defender-smartscreen/).

![windows-app-control](https://github.com/djiotua/tryhackme/assets/134016731/c50e13b6-3079-4181-a238-f6191393cc1a)

_Check apps and files_

- _Windows Defender SmartScreen_ helps protect your device by checking for unrecognized apps and files from the web.

![windows-smartscreen](https://github.com/djiotua/tryhackme/assets/134016731/461caf55-1036-4e92-8929-512d1cf521f9)

_Exploit protection_

- Exploit protection is built into Windows 10 (and, in our case, Windows Server 2019) to help protect your device against attacks.

![windows-exploit-protection](https://github.com/djiotua/tryhackme/assets/134016731/1962ced5-2005-48b6-8bf0-3ce647b8cb3e)

_Warning: Unless you are 100% confident in what you are doing, it is recommended that you leave the default settings._

---

_1. Read the above._

No answer needed.

---

# Task 7 - Device security

Even though you'll probably never change any of these settings, for completion's sake, it will be covered briefly.

![windows-device-sec](https://github.com/djiotua/tryhackme/assets/134016731/baacd6e0-238a-4a06-9de7-bb9de7b6f67e)

_Core isolation_

- Memory Integrity - Prevents attacks from inserting malicious code into high-security processes.

![windows-mem-integrity2](https://github.com/djiotua/tryhackme/assets/134016731/32ee770b-6bd9-4ea2-aaa0-191823ac60de)

_Warning: Unless you are 100% confident in what you are doing, it is recommended that you leave the default settings._

The below images are from another machine to show another security feature that should be available in a personal Windows 10 device.

_Security processor_

![windows-sec-processor](https://github.com/djiotua/tryhackme/assets/134016731/02545bfe-b019-4206-94bc-9640b6c25460)

Below are the _Security processor details_.

Below are the Security processor details.

![windows-tpm](https://github.com/djiotua/tryhackme/assets/134016731/0bf38f8a-37e0-4e87-b1e1-38fbf33d759e)

What is the _Trusted Platform Module (TPM)_?

Per Microsoft, "_Trusted Platform Module (TPM) technology is designed to provide hardware-based, security-related functions. A TPM chip is a secure crypto-processor that is designed to carry out cryptographic operations. The chip includes multiple physical security mechanisms to make it tamper-resistant, and malicious software is unable to tamper with the security functions of the TPM_".

---

_1. What is the TPM?_

  <details>
    <summary>Answer</summary>

    Trusted Platform Module
  </details>

---

# Task 8 - BitLocker

What is _BitLocker_?

Per Microsoft, "_BitLocker Drive Encryption is a data protection feature that integrates with the operating system and addresses the threats of data theft or exposure from lost, stolen, or inappropriately decommissioned computers_".

On devices with TPM installed, BitLocker offers the best protection.

Per Microsoft, "_BitLocker provides the most protection when used with a Trusted Platform Module (TPM) version 1.2 or later. The TPM is a hardware component installed in many newer computers by the computer manufacturers. It works with BitLocker to help protect user data and to ensure that a computer has not been tampered with while the system was offline_".

Refer to the official Microsoft documentation to learn more about BitLocker [here](https://learn.microsoft.com/en-us/windows/security/operating-system-security/data-protection/bitlocker/). 

_Note: The BitLocker feature is not included in the attached VM._

---

_1. What must a user insert on computers that DO NOT have a TPM version 1.2 or later?_

  Hint: Refer to the Microsoft documentation on BitLocker.

  <details>
    <summary>Answer</summary>

    USB startup key
  </details>

---

# Task 9 - Volume Shadow Copy Service

Per [Microsoft](https://learn.microsoft.com/en-us/windows-server/storage/file-server/volume-shadow-copy-service), the _Volume Shadow Copy Service_ (VSS) coordinates the required actions to create a consistent shadow copy (also known as a snapshot or a point-in-time copy) of the data that is to be backed up.

Volume Shadow Copies are stored on the System Volume Information folder on each drive that has protection enabled.

If VSS is enabled (_System Protection_ turned on), you can perform the following tasks from within _advanced system settings_.

- Create a restore point
- Perform system restore
- Configure restore settings
- Delete restore points

From a security perspective, malware writers know of this Windows feature and write code in their malware to look for these files and delete them. Doing so makes it impossible to recover from a ransomware attack unless you have an offline/off-site backup.

If you wish to configure Shadow Copies within the attached VM, see below.

![vss1](https://github.com/djiotua/tryhackme/assets/134016731/7a785f21-c8c4-4f87-847c-73c5d8c131bc)

![vss2](https://github.com/djiotua/tryhackme/assets/134016731/fab87821-32ff-4deb-a6b9-e61250bb084a)

_Bonus: If you wish to interact hands-on with VSS, I suggest exploring Day 23 of [Advent of Cyber 2](https://tryhackme.com/room/adventofcyber2)._

---

_1. What is VSS?_

  <details>
    <summary>Answer</summary>

    Volume Shadow Copy Service
  </details>

---

# Task 10 - Conclusion

In this room, we covered several built-in Windows security tools that ship with the Windows OS to help keep the device protected. 

There is still so much to explain and cover regarding the Windows OS. As mentioned in the [Windows Fundamentals 1](https://tryhackme.com/room/windowsfundamentals1xbx) room, "_The content is aimed at those who wish to understand and use the Windows OS on a more comfortable level._"

To learn more about the Windows OS, you'll need to continue the journey on your own.

Further reading material:

- [Antimalware Scan Interface](https://learn.microsoft.com/en-us/windows/win32/amsi/antimalware-scan-interface-portal)
- [Credential Guard](https://learn.microsoft.com/en-us/windows/security/identity-protection/credential-guard/credential-guard-manage)
- [Windows 10 Hello](https://support.microsoft.com/en-us/windows/learn-about-windows-hello-and-set-it-up-dae28983-8242-bb2a-d3d1-87c9d265a5f0#:~:text=Windows%2010,in%20with%20just%20your%20PIN.)
- [CSO Online - The best new Windows 10 security features](https://www.csoonline.com/article/3253899/the-best-new-windows-10-security-features.html)

_Note: Attackers use built-in Windows tools and utilities in an attempt to go undetected within the victim environment.  This tactic is known as Living Off The Land. Refer to the following resource [here](https://lolbas-project.github.io/) to learn more about this._

---

_1. Read the above._

No answer needed.

---

END OF ROOM
