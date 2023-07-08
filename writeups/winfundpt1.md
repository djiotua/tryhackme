# Windows Fundamentals 1

In part 1 of the Windows Fundamentals module, we'll start our journey learning about the Windows desktop, the NTFS file system, UAC, the Control Panel, and more...

---

# Task 1 - Introduction to Windows

The Windows operating system (OS) is a complex product with many system files, utilities, settings, features, etc. 

This module will attempt to provide a general overview of just a handful of what makes up the Windows OS, navigate the user interface, make changes to the system, etc. The content is aimed at those who wish to understand and use the Windows OS on a more comfortable level. 

Launch the attached virtual machine. The virtual machine should open within your web browser. 

If you want to access the virtual machine via [Remote Desktop](https://www.cyberark.com/resources/threat-research-blog/explain-like-i-m-5-remote-desktop-protocol-rdp), use the credentials below.

Machine IP: _MACHINE_IP_

User: _administrator_

Password: _letmein123!_

![remmina](https://github.com/djiotua/tryhackme/assets/134016731/297bed68-0d5c-4c62-aa50-0bfabc501a5f)

Accept the Certificate when prompted, and you should be logged into the remote system now.

_Note: The virtual machine may take up to 3 minutes to load._

---

_1. Read above and start the virtual machine._

No answer needed.

  <details>
    <summary>Explanation</summary>

    1. If I wanted to access via Remote Desktop, I open Applications (top left corner of AttackBox) -> Internet -> Remmina. There should be a message asking for a login keyring, to which I clicked "Cancel", which takes us to Remmina.

![Winfundpt1](https://github.com/djiotua/tryhackme/assets/134016731/bfc94574-d4e8-4b0d-89d7-f967cdd9d82f)

    I then pressed "New connection profile" on the top left corner of Remmina, which takes us to the window similar to the screenshot. There, I entered the credentials provided.
    After this, I accepted the certificate, then the Windows virtual machine started.

    2. Another option would not require the above process, directly loading the Windows virtual machine.
  </details>
---

# Task 2 - Windows Editions

The Windows operating system has a long history dating back to 1985, and currently, it is the dominant operating system in both home use and corporate networks. Because of this, Windows has always been targeted by hackers & malware writers.

Windows XP was a popular version of Windows and had a long run. Microsoft announced Windows Vista, which was a complete overhaul of the Windows operating system. There were many issues with Windows Vista. It wasn't received well by Windows users, and it was quickly phased out.

When Microsoft announced the end-of-life date for Windows XP, many customers panicked. Corporations, hospitals, etc., scrambled and tested the next viable Windows version, which was Windows 7, against many other hardware and devices. Vendors had to work against the clock to ensure their products worked with Windows 7 for their customers. If they couldn't, their customers had to break their agreement and find another vendor that upgraded their products to work with Windows 7. It was a nightmare for many, and Microsoft took note of it.

Windows 7, as quickly as it was released soon after, was marked with an end of support date. Windows 8.x came and left and it was short-lived, like Vista.

Then arrived Windows 10, which is the current Windows operating system version for desktop computers.

Windows 10 comes in 2 flavors, Home and Pro. You can read the difference between the Home and Pro [here](https://www.microsoft.com/en-us/windows/compare-windows-10-home-vs-pro). 

Even though we didn't talk about servers, the current version of the Windows operating system for servers is [Windows Server 2022](https://www.microsoft.com/en-us/windows-server).

Many critics like to bash on Microsoft, but they have made long strides to improve the usability and security with each new version of Windows.

_Note: The Windows edition for the attached VM is Windows Server 2019 Standard, as seen in System Information._

_Update: As of June 2021, Microsoft announced the retirement dates for Windows 10 [here](https://learn.microsoft.com/en-us/lifecycle/products/windows-10-home-and-pro?ranMID=24542&ranEAID=kXQk6*ivFEQ&ranSiteID=kXQk6.ivFEQ-4cKUPfbv9lM_IR2EX7K_hw&epi=kXQk6.ivFEQ-4cKUPfbv9lM_IR2EX7K_hw&irgwc=1&OCID=AID2000142_aff_7593_1243925&tduid=(ir__feexvhocigkfqna9kk0sohznb32xutanagupypus00)(7593)(1243925)(kXQk6.ivFEQ-4cKUPfbv9lM_IR2EX7K_hw)()&irclickid=_feexvhocigkfqna9kk0sohznb32xutanagupypus00)._

"Microsoft will continue to support at least one Windows 10 Semi-Annual Channel until October 14, 2025".

As of October 5th, 2021 - [Windows 11](https://www.microsoft.com/en-us/windows/features?activetab=NewPopular&r=1) now is the current Windows operating system for end-users. Read more about Windows 11 [here](https://www.microsoft.com/en-us/windows?wa=wsignin1.0).

---

_1. What encryption can you enable on Pro that you can't enable in Home?_

  <details>
    <summary>Answer</summary>

    BitLocker
  </details>

---

# Task 3 - The Desktop (GUI)

The Windows Desktop, aka the graphical user interface or GUI in short, is the screen that welcomes you once you log into a Windows 10 machine.

Traditionally, you need to pass the login screen first. The login screen is where you need to enter valid account credentials; usually, a username & password of a preexisting Windows account on that particular system or in the Active Directory environment (if it's a domain-joined machine).

![win-desktop2](https://github.com/djiotua/tryhackme/assets/134016731/db93c704-a0ec-4362-ae48-b09cbf43f219)

The above screenshot is an example of a typical Windows Desktop. Each component that makes up the GUI is explained briefly below.

1. The Desktop
2. Start Menu
3. Search Box (Cortana)
4. Task View
5. Taskbar
6. Toolbars
7. Notification Area

### The Desktop

The desktop is where you will have shortcuts to programs, folders, files, etc. These icons will either be well organized in folders sorted alphabetically or scattered randomly with no specific organization on the desktop. In either case, these items are typically placed on the desktop for quick access.

The look and feel of the desktop can be changed to suit your liking. By right-clicking anywhere on the desktop, a context menu will appear. This menu will allow you to change the sizes of the desktop icons, specify how you want to arrange them, copy/paste items to the desktop, and create new items, such as a folder, shortcut, or text document.

![win-desktop-menu](https://github.com/djiotua/tryhackme/assets/134016731/1757d727-af5a-4f61-b82b-3aa61632906f)

Under _Display settings_, you can make changes to the screen's resolution and orientation. In case you have multiple computer screens, you can make configurations to the multi-screen setup here.

![win-desktop-setdisplay](https://github.com/djiotua/tryhackme/assets/134016731/618eb995-6494-4071-aad7-0b27e2e6c445)

_Note: In a Remote Desktop session, some of the display settings will be disabled._

![win-display-settings](https://github.com/djiotua/tryhackme/assets/134016731/befe0ca0-34ed-424b-9086-424829a86491)

You can also change the wallpaper by selecting _Personalize_.

![win-desktop-personalize](https://github.com/djiotua/tryhackme/assets/134016731/8d81bc9e-b15a-4777-a2e0-7132e33b32ae)

Under Personalize, you can change the background image to the Desktop, change fonts, themes, color scheme, etc.

![win-personalize-settings](https://github.com/djiotua/tryhackme/assets/134016731/f2e13857-6e13-43fb-8c06-fc38936ac0c2)

### The Start Menu

In previous versions of Windows, the word Start was visible at the bottom left corner of the desktop GUI. In modern versions of Windows, such as Windows 10, the word 'Start' doesn't appear anymore, but rather a Windows Logo is shown instead. Even though the look of the Start Menu has changed, its overall purpose is the same. 

The _Start Menu_ provides access to all the apps/programs, files, utility tools, etc., that are most useful. 

Clicking on the Windows logo, the Start Menu will open. The Start Menu is broken up into sections. See below.

![win-start-menu](https://github.com/djiotua/tryhackme/assets/134016731/7a8ded29-2662-4f8b-8386-300837540dea)

1. This section of the Start Menu provides quick shortcuts to actions that you can perform with your account or login session, such as making changes to your user account, lock your screen, or signing out of your account. Other shortcuts specific to your account are your Documents (document icon) folder and Pictures folder (pictures icon). Lastly, the gear/cog icon will take you to the Settings screen, and the power icon will allow you to Disconnect from a Remote Desktop session, shut down the computer, or restart the computer.
   
In the below image, you can see what each of the icons represents. To expand this section, click on the icon that resembles a hamburger at the top.

![win-start-hamburger](https://github.com/djiotua/tryhackme/assets/134016731/07356cae-728e-4180-901c-746aca0be568)

2. This section will show all _Recently added_ apps/programs at the top and all the installed apps/programs (that are configured to appear in the Start Menu). In this section, you'll also see the apps/programs will be listed in alphabetical order. Each letter will have its own section. See below.

![win-start-programs](https://github.com/djiotua/tryhackme/assets/134016731/5e3ce885-4f91-4101-85e5-2c798472f8e7)

In the above image, the first box is where the recently added apps/programs will appear. The second box is where all the installed apps/programs will appear. 

_Note: In your VM, Google Chrome will not show up as a Recently Added program anymore._

If you have a _LONG_ list of installed apps/programs, you can jump to a particular section in the list by clicking on the letter headings to launch an alphabet grid. See below.

![win-start-grid](https://github.com/djiotua/tryhackme/assets/134016731/67f5d862-f630-4b50-87f0-5fbc812471fe)

_Note: The white letters match the letter headings._

3. The right side of the Start Menu is where you will find icons for specific apps/programs or utilities. These icons are known as _tiles_. Some tiles are added to this section by default. If you right-click any of the tiles, you guessed it; a menu will appear to allow you to perform more actions on the selected tile; such as resizing the tile, unpinning from Start Menu, view its Properties, etc. See below.

![win-start-tile](https://github.com/djiotua/tryhackme/assets/134016731/b3e62f6e-4a89-482c-92f6-cb7d08294d45)

Apps/programs can be added to this Start Menu section by right-clicking the app/program and selecting Pin to Start. See below.

![win-start-pin](https://github.com/djiotua/tryhackme/assets/134016731/9def813d-7fc9-4d5e-beb5-12b038fcb9c7)

![win-start-pin2](https://github.com/djiotua/tryhackme/assets/134016731/97b8ba85-eeab-4a3a-a083-429ce75d030a)

### The Taskbar

Some of the components are enabled and visible by default. The Toolbar (6), for example, was enabled for demonstration purposes.  

If you're like me and want to disable some of these components, you can right-click on Taskbar to bring up a context menu that will allow you to make changes.

![win-taskbar1](https://github.com/djiotua/tryhackme/assets/134016731/66066eca-9557-4179-98e7-193f245e7d11)

Any apps/programs, folders, files, etc., that you open/start will appear in the taskbar.

![win-taskbar-chrome](https://github.com/djiotua/tryhackme/assets/134016731/494f9101-2dd9-4c9f-8462-06fc322f0f76)

Hovering over the icon will provide a preview thumbnail, along with a tooltip. This tooltip is handy if you have many apps/programs open, such as Google Chrome, and you wish to find which instance of Google Chrome is the one you need to bring in to focus. 

When you close any of these items, they will disappear from the taskbar (unless you explicitly pinned it to the taskbar).

### The Notification Area

The _Notification Area_, which is typically located at the bottom right of the Windows screen, is where the date and time are displayed. Other icons possibly visible in this area is the volume icon, network/wireless icon, to name a few. Icons can be either added or removed from the Notification Area in Taskbar settings.

![win-taskbar-settings](https://github.com/djiotua/tryhackme/assets/134016731/e3067a03-947b-414f-844e-a3bdc3301ff8)

From there, scroll down to the Notification Area section to make changes.

![win-taskbar-notifarea](https://github.com/djiotua/tryhackme/assets/134016731/c5e791b5-d23d-4370-9e1c-96b888d583e9)

Here are Microsoft's brief documents for the [Start Menu](https://support.microsoft.com/en-us/windows/see-what-s-on-the-start-menu-a8ccb400-ad49-962b-d2b1-93f453785a13) and [Notification Area](https://support.microsoft.com/en-us/windows/customize-the-taskbar-notification-area-e159e8d2-9ac5-b2bd-61c5-bb63c1d437c3#WindowsVersion=Windows_10).

_Tip: You can right-click any folder, file, app/program, or icon to view more information or perform other actions on the clicked item._

---

_1. Which selection will hide/disable the Search box?_

  <details>
    <summary>Answer</summary>

    Hidden
  </details>

  <details>
    <summary>Explanation</summary>

    I right-clicked on the Taskbar, then hovered over "Search", which showed the options, including "Hidden".
  </details>

_2. Which selection will hide/disable the Task View button?_

  <details>
    <summary>Answer</summary>

    Show Task View button
  </details>

_3. Besides Clock and Network, what other icon is visible in the Notification Area?_

  Hint: Try right-clicking the icon.

  <details>
    <summary>Answer</summary>

    Action Center
  </details>

  <details>
    <summary>Explanation</summary>

    The answer can be found on the link below. If you spell "Centre", the answer would be incorrect.

  [Link](https://support.microsoft.com/en-us/windows/customize-the-taskbar-notification-area-e159e8d2-9ac5-b2bd-61c5-bb63c1d437c3)
  </details>

---

# Task 4 - The File System

The file system used in modern versions of Windows is the _New Technology File System_ or simply [_NTFS_](https://learn.microsoft.com/en-us/windows-server/storage/file-server/ntfs-overview).

Before NTFS, there was _FAT16_/_FAT32_ (File Allocation Table) and _HPFS_ (High Performance File System). 

You still see FAT partitions in use today. For example, you typically see FAT partitions in USB devices, MicroSD cards, etc. but traditionally not on personal Windows computers/laptops or Windows servers.

NTFS is known as a journaling file system. In case of a failure, the file system can automatically repair the folders/files on disk using information stored in a log file. This function is not possible with FAT.   

NTFS addresses many of the limitations of the previous file systems; such as: 

- Supports files larger than 4GB
- Set specific permissions on folders and files
- Folder and file compression
- Encryption ([_Encryption File System_](https://learn.microsoft.com/en-us/windows/win32/fileio/file-encryption) or EFS)
  
If you're running Windows, what is the file system your Windows installation is using? You can check the Properties (right-click) of the drive your operating system is installed on, typically the C drive (C:\).

![win-file-system](https://github.com/djiotua/tryhackme/assets/134016731/915f5e72-e007-4043-8844-aa5d2cb70b6f)

You can read Microsoft's official documentation on FAT, HPFS, and NTFS [here](https://learn.microsoft.com/en-us/troubleshoot/windows-client/backup-and-storage/fat-hpfs-and-ntfs-file-systems). 

Let's speak briefly on some features that are specific to NTFS. 

On NTFS volumes, you can set permissions that grant or deny access to files and folders.

The permissions are:

- Full control
- Modify
- Read & Execute
- List folder contents
- Read
- Write
  
The below image lists the meaning of each permission on how it applies to a file and a folder. (credit [Microsoft](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-2000-server/bb727008(v=technet.10)?redirectedfrom=MSDN))

![ntfs-permissions1](https://github.com/djiotua/tryhackme/assets/134016731/a329d045-5d87-4f79-a272-4cdf0066f299)

How can you view the permissions for a file or folder?

- Right-click the file or folder you want to check for permissions.
- From the context menu, select _Properties_.
- Within Properties, click on the _Security_ tab.
- In the _Group or user names_ list, select the user, computer, or group whose permissions you want to view.
  
In the below image, you can see the permissions for the _Users_ group for the Windows folder.

![windows-folder-permissions](https://github.com/djiotua/tryhackme/assets/134016731/9a795a63-a527-43e6-b962-1575104026b6)

Refer to the Microsoft documentation to get a better understanding of the NTFS permissions for _Special Permissions_.

Another feature of NTFS is _Alternate Data Streams (ADS)_.

Alternate Data Streams (ADS) is a file attribute specific to Windows _NTFS_ (New Technology File System).

Every file has at least one data stream (_$DATA_), and ADS allows files to contain more than one stream of data. Natively [Window Explorer](https://support.microsoft.com/en-us/windows/find-and-open-file-explorer-ef370130-1cca-9dc5-e0df-2f7416fe1cb1) doesn't display ADS to the user. There are 3rd party executables that can be used to view this data, but [Powershell](https://learn.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7.3&viewFallbackFrom=powershell-7.1) gives you the ability to view ADS for files.

From a security perspective, malware writers have used ADS to hide data.

Not all its uses are malicious. For example, when you download a file from the Internet, there are identifiers written to ADS to identify that the file was downloaded from the Internet.

To learn more about ADS, refer to the following link from MalwareBytes [here](https://blog.malwarebytes.com/101/2015/07/introduction-to-alternate-data-streams/). 

_Bonus: If you wish to interact hands-on with ADS, I suggest exploring Day 21 of [Advent of Cyber 2](https://tryhackme.com/room/adventofcyber2)._

---

_1. What is the meaning of NTFS?_

  <details>
    <summary>Answer</summary>

    New Technology File System
  </details>

---

# Task 5 - The Windows\System32 Folders

The Windows folder (_C:\Windows_) is traditionally known as the folder which contains the Windows operating system. 

The folder doesn't have to reside in the C drive necessarily. It can reside in any other drive and technically can reside in a different folder.

This is where environment variables, more specifically system environment variables, come into play. Even though not discussed yet, the system environment variable for the Windows directory is _%windir%_.

Per [Microsoft](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-7.3&viewFallbackFrom=powershell-7.1), "_Environment variables store information about the operating system environment. This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders_".

There are many folders within the 'Windows' folder. See below.

![windows-folder](https://github.com/djiotua/tryhackme/assets/134016731/cab0ac47-1b3b-41c1-b675-2392befc0a93)

One of the many folders is _System32_.

![windows-system32](https://github.com/djiotua/tryhackme/assets/134016731/04483680-d84c-4b1a-b629-e6ff89be687e)

The System32 folder holds the important files that are critical for the operating system.

You should proceed with extreme caution when interacting with this folder. Accidentally deleting any files or folders within System32 can render the Windows OS inoperational. Read more about this action [here](https://www.howtogeek.com/346997/what-is-the-system32-directory-and-why-you-shouldnt-delete-it/). 

_Note: Many of the tools that will be covered in the Windows Fundamentals series reside within the System32 folder._

---

_1. What is the system variable for the Windows folder?_

  <details>
    <summary>Answer</summary>

    %windir%
  </details>

---

# Task 6 - User Accounts, Profiles, and Permissions

User accounts can be one of two types on a typical local Windows system: _Administrator_ & _Standard User_. 

The user account type will determine what actions the user can perform on that specific Windows system. 

- An Administrator can make changes to the system: add users, delete users, modify groups, modify settings on the system, etc. 
- A Standard User can only make changes to folders/files attributed to the user & can't perform system-level changes, such as install programs.
  
You are currently logged in as an Administrator. There are several ways to determine which user accounts exist on the system. 

One way is to click the _Start Menu_ and type _Other User_. A shortcut to _System Settings > Other users_ should appear.

![win-other-user1](https://github.com/djiotua/tryhackme/assets/134016731/7f2ebb8d-b673-42e2-a5bb-fd48ee78ab0f)

If you click on it, a Settings window should now appear. See below.

![win-other-user](https://github.com/djiotua/tryhackme/assets/134016731/8d6732ca-be81-492e-aa8d-90d22cef17cb)

Since you're the Administrator, you see an option to _Add someone else to this PC_.

_Note: A Standard User will not see this option._

Click on the local user account. More options should appear: _Change account type_ and _Remove_.

![win-other-user2](https://github.com/djiotua/tryhackme/assets/134016731/023c27cd-d31a-4830-9f7f-98bc8214e969)

Click on Change account type. The value in the drop-down box (or the highlighted value if you click the drop-down) is the current account type. 

![win-other-user3](https://github.com/djiotua/tryhackme/assets/134016731/7f069ee5-2820-450f-b87a-0dd45e214784)

When a user account is created, a profile is created for the user. The location for each user profile folder will fall under is _C:\Users_.

For example, the user profile folder for the user account Max will be _C:\Users\Max_.

The creation of the user's profile is done upon initial login. When a new user account logs in to a local system for the first time, they'll see several messages on the login screen. One of the messages, User Profile Service, sits on the login screen for a while, which is at work creating the user profile. See below.

![win-profile-service](https://github.com/djiotua/tryhackme/assets/134016731/d4adefea-03a1-4624-a0b5-5bff0f5e733d)

Once logged in, the user will see a dialog box similar to the one below (again), indicating that the profile is in creation.

![win-profile-service2](https://github.com/djiotua/tryhackme/assets/134016731/1f8781b8-e94e-4a53-b76e-bd644e885ab2)

Each user profile will have the same folders; a few of them are:

- Desktop
- Documents
- Downloads
- Music
- Pictures

Another way to access this information, and then some, is using _Local User and Group Management_.

Right-click on the Start Menu and click _Run_. Type _lusrmgr.msc_. See below.

![win-lusrmgr](https://github.com/djiotua/tryhackme/assets/134016731/1c1d55d9-4b7e-44e5-933a-c37d99067b58)

_Note: The Run Dialog Box allows us to open items quickly._

Back to lusrmgr, you should see two folders: _Users_ and _Groups_.

If you click on Groups, you see all the names of the local groups along with a brief description for each group.

Each group has permissions set to it, and users are assigned/added to groups by the Administrator. When a user is assigned to a group, the user inherits the permissions of that group. A user can be assigned to multiple groups.

_Note: If you click on Add someone else to this PC from Other users, it will open Local Users and Management._

---

1. What is the name of the other user account?
   
  <details>
    <summary>Answer</summary>

    tryhackmebilly
  </details>

  <details>
    <summary>Explanation</summary>

    Once I ran lusrmgr.msc, there was a window that showed two folders. I clicked on Users, and there was another user account.

![Winfundpt1 2](https://github.com/djiotua/tryhackme/assets/134016731/f2e87dfc-a0ae-4cb7-a240-8a7aadb44fb8)
  </details>

_2. What groups is this user a member of?_

  <details>
    <summary>Answer</summary>

    Remote Desktop Users,Users
  </details>

  <details>
    <summary>Explanation</summary>

    By double-clicking on this user, it opened the "Properties" window, then I went to the "Member Of" tab to find the answer.

![Winfundpt1 3](https://github.com/djiotua/tryhackme/assets/134016731/2ffac858-a3db-4588-a7ee-3c51da23687e)
  </details>

_3. What built-in account is for guest access to the computer?_

  <details>
    <summary>Answer</summary>

    Guest
  </details>

_4. What is the account status?_

  <details>
    <summary>Answer</summary>

    Account is disabled
  </details>

  <details>
    <summary>Explanation</summary>

    From the "General" tab.
  </details>

---

# Task 7 - User Account Control

The large majority of home users are logged into their Windows systems as local administrators. Remember from the previous task that any user with administrator as the account type can make changes to the system.

A user doesn't need to run with high (elevated) privileges on the system to run tasks that don't require such privileges, such as surfing the Internet, working on a Word document, etc. This elevated privilege increases the risk of system compromise because it makes it easier for malware to infect the system. Consequently, since the user account can make changes to the system, the malware would run in the context of the logged-in user.

To protect the local user with such privileges, Microsoft introduced _User Account Control_ (UAC). This concept was first introduced with the short-lived [Windows Vista](https://en.wikipedia.org/wiki/Windows_Vista) and continued with versions of Windows that followed.

_Note: UAC (by default) doesn't apply for the built-in local administrator account._

How does UAC work? When a user with an account type of administrator logs into a system, the current session doesn't run with elevated permissions. When an operation requiring higher-level privileges needs to execute, the user will be prompted to confirm if they permit the operation to run.

Let's look at the program on the account you're currently logged into, the built-in administrator account—Right-click to view its Properties.

In the _Security_ tab, we can see the users/groups and their permissions to this file. Notice that the standard user is not listed.

![win-wireshark](https://github.com/djiotua/tryhackme/assets/134016731/bc45f4b7-633a-427c-ae7f-2ca22c37436a)

Log in as the standard user and try to install this program. To do this, you can remote desktop into the machine as the standard user account. 

_Note: You have the username and password for the standard user. It's visible in lusrmgr.msc._

Before installing the program, notice the icon. Do you see the difference? When you're logged in as the standard user, the shield icon is on the program's default icon. See below.

![win-wireshark](https://github.com/djiotua/tryhackme/assets/134016731/697f13dd-8dca-456e-96c6-a3ce1b514802)

This shield icon is an indicator that UAC will prompt to allow higher-level privileges to install the program.

![win-wireshark2](https://github.com/djiotua/tryhackme/assets/134016731/48a6ba4a-a918-4ace-b627-8fbd045818fd)

Double-click the program, and you'll see the UAC prompt. Notice that the built-in administrator account is already set as the user name and prompts the account's password. See below.

![win-uac](https://github.com/djiotua/tryhackme/assets/134016731/7b9004d5-7868-4c91-ae16-3a79134bfe18)

After some time, if a password is not entered, the UAC prompt disappears, and the program does not install. 

This feature reduces the likelihood of malware successfully compromising your system. You can read more about [UAC](https://learn.microsoft.com/en-us/windows/security/application-security/application-control/user-account-control/how-it-works) here.

---

_1. What does UAC mean?_

  <details>
    <summary>Answer</summary>

    User Account Control
  </details>

---

# Task 8 - Settings and the Control Panel

On a Windows system, the primary locations to make changes are the Settings menu and the Control Panel.

For a long time, the Control Panel has been the go-to location to make system changes, such as adding a printer, uninstall a program, etc. 

The Settings menu was introduced in Windows 8, the first Windows operating system catered to touch screen tablets, and is still available in Windows 10. As a matter of fact, the Settings menu is now the primary location a user goes to if they are looking to change the system. 

There are similarities and differences between the two menus. Below are screenshots of each.

Settings:

![win-settings](https://github.com/djiotua/tryhackme/assets/134016731/ce79361f-a7dc-4222-9e54-a0c2cabe64aa)

Control Panel:

![win-control-panel](https://github.com/djiotua/tryhackme/assets/134016731/ff9e7c68-6564-4bdd-9ad4-41566ccd7b4c)

_Note: The icons for Settings might be different in the version of Windows on your personal device._

Both can be accessed from the Start Menu. See below.

![win-settings-cp](https://github.com/djiotua/tryhackme/assets/134016731/dc5dc2dc-5943-4c89-9323-c3bccbd2db53)

Control Panel is the menu where you will access more complex settings and perform more complex actions. In some cases, you can start in Settings and end up in the Control Panel.

For example, in Settings, click on _Network & Internet_. From here, click on _Change adapter options_.

![win-change-adapter1](https://github.com/djiotua/tryhackme/assets/134016731/349425d5-afa4-40ef-b4fb-6efe2369ac78)

Notice that the next window that pops up is from the _Control Panel_.

![win-change-adapter2](https://github.com/djiotua/tryhackme/assets/134016731/0120eb23-044c-4179-b38b-89d5aebbc6e7)

If you're unclear which to open if you wish to change a setting, use the Start menu and search for it. 

In the example below, the search was 'wallpaper.' Notice that few results were returned.

![win-change-wallpaper](https://github.com/djiotua/tryhackme/assets/134016731/3609be6b-7293-473e-a65f-66bdd00bc546)

If we click on the Best match, a window to the Settings menu appears to make changes to the wallpaper.

![win-change-wallpaper2](https://github.com/djiotua/tryhackme/assets/134016731/8de43131-a3eb-4724-9df0-1872083e90fc)

---

_1. In the Control Panel, change the view to Small icons. What is the last setting in the Control Panel view?_

  <details>
    <summary>Answer</summary>

    Windows Defender Firewall
  </details>

  <details>
    <summary>Explanation</summary>

    Once Control Panel is opened, there is "View by:" on top of the categories. I changed to small icons, to find the answer.
  </details>

---

# Task 9 - Task Manager

The last subject that will be touched on in this module is the _Task Manager_.

The Task Manager provides information about the applications and processes currently running on the system. Other information is also available, such as how much CPU and RAM are being utilized, which falls under _Performance_.

You can access the Task Manager by right-clicking the taskbar.

![win-task-manager](https://github.com/djiotua/tryhackme/assets/134016731/5d6afe6b-15e2-48f1-94cb-511d2be5688b)

Task Manager will open in Simple View and won't show much information.

![win-task-manager2](https://github.com/djiotua/tryhackme/assets/134016731/54027d58-3bb3-4478-a7a0-7dc9d7d6c626)

Click on _More details_, and the view changes.

![win-task-manager3](https://github.com/djiotua/tryhackme/assets/134016731/379c8630-19c5-4293-b255-77d82c6b6b86)

You can refer to this [blog post](https://www.howtogeek.com/405806/windows-task-manager-the-complete-guide/) for more detailed information about the Task Manager.

If you wish to learn more about the core Windows processes and what each process is responsible for, visit the [Core Windows Processes room](https://tryhackme.com/room/btwindowsinternals).

---

_1. What is the keyboard shortcut to open Task Manager?_

  <details>
    <summary>Answer</summary>

    Ctrl+Shift+Esc
  </details>

---

# Task 10 - Conclusion

Again, this was a generic overview of the Windows OS.

There are intermediate and advanced topics for each topic (task) that was covered in this room.

Hence, Task 9 ended with a detailed blog post explaining the Task Manager in great detail.

In future modules, we'll cover topics like the Windows folder, the management console, security tools (Windows Defender, Windows Firewall, etc.), to name a few.

---

_1. Read above and terminate the Windows machine you deployed in this room._

No answer needed.

---

END OF ROOM
