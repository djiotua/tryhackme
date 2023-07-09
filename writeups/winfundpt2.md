# Windows Fundamentals 2

In part 2 of the Windows Fundamentals module, discover more about System Configuration, UAC Settings, Resource Monitoring, the Windows Registry and more...

---

We will continue our journey exploring the Windows operating system. 

In [Windows Fundamentals 1](https://tryhackme.com/room/windowsfundamentals1xbx), we covered the desktop, the file system, user account control, the control panel, settings, and the task manager. 

This module will attempt to provide an overview of some other utilities available within the Windows operating system and different methods to access these utilities.

Launch the attached virtual machine. If you wish to access the virtual machine via Remote Desktop, use the credentials below. 

Machine IP: _MACHINE_IP_

User: _administrator_

Password: _letmein123!_

![remmina](https://github.com/djiotua/tryhackme/assets/134016731/3c491c4c-ae9e-48db-922b-ea9cafb97493)

Accept the Certificate when prompted, and you should be logged into the remote system now.

_Note: The virtual machine may take up to 3 minutes to load._

---

_1. Read above and start the virtual machine._

No answer needed.

---

# Task 2 - System Configuration

The _System Configuration_ utility (_MSConfig_) is for advanced troubleshooting, and its main purpose is to help diagnose startup issues. 

Reference the following document [here](https://learn.microsoft.com/en-us/troubleshoot/windows-client/performance/system-configuration-utility-troubleshoot-configuration-errors) for more information on the System Configuration utility. 

There are several methods to launch System Configuration. One method is from the Start Menu.

![msconfig-start](https://github.com/djiotua/tryhackme/assets/134016731/466c4f67-6727-49ad-82b9-ceba40f6255b)

_Note: You need local administrator rights to open this utility._

The utility has five tabs across the top. Below are the names for each tab. We will briefly cover each tab in this task. 

1. General
2. Boot
3. Services
4. Startup
5. Tools

In the _General_ tab, we can select what devices and services for Windows to load upon boot. The options are: _Normal_, _Diagnostic_, or _Selective_.

In the _Boot_ tab, we can define various boot options for the Operating System.

![msconfig2](https://github.com/djiotua/tryhackme/assets/134016731/66c8f209-7fc0-479c-b42c-51efd43e623a)

The _Services_ tab lists all services configured for the system regardless of their state (running or stopped). A service is a special type of application that runs in the background.

![msconfig3](https://github.com/djiotua/tryhackme/assets/134016731/e2746187-0b7c-4087-a4e0-74920c2f43c1)

In the _Startup_ tab, you won't see anything interesting in the attached VM.  Below is a screenshot of the Startup tab for _MSConfig_ from my local machine.

![msconfig4](https://github.com/djiotua/tryhackme/assets/134016731/455694ab-4435-4252-8489-376897153e17)

As you can see, Microsoft advises using _Task Manager_ (_taskmgr_) to manage (enable/disable) startup items. The System Configuration utility is _NOT_ a startup management program.

_Note: If you open Task Manager for the attached VM, you will notice that Task Manager doesn't show a Startup tab._

There is a list of various utilities (tools) in the Tools tab that we can run to configure the operating system further. There is a brief description of each tool to provide some insight into what the tool is for.

![msconfig5](https://github.com/djiotua/tryhackme/assets/134016731/3a6195eb-b13b-42cb-9cd9-00b6b80a6f8e)

Notice the _Selected command_ section. The information in this textbox will change per tool.

To run a tool, we can use the command to launch the tool via the run prompt, command prompt, or by clicking the _Launch_ button.

---

_1. What is the name of the service that lists Systems Internals as the manufacturer?_

  <details>
    <summary>Answer</summary>

    PsShutdown
  </details>

  <details>
    <summary>Explanation</summary>

    I found the answer on the "Services" tab.
  </details>

_2. Whom is the Windows license registered to?_

  <details>
    <summary>Answer</summary>

    Windows User
  </details>

  <details>
    <summary>Explanation</summary>

    In the "Tools" tab, I double-clicked "About Windows", where I found the answer.
  </details>

_3. What is the command for Windows Troubleshooting?_

  <details>
    <summary>Answer</summary>

    C:\Windows\System32\control.exe /name Microsoft.Troubleshooting
  </details>

  <details>
    <summary>Explanation</summary>

    Also in "Tools". You may have to type the answer instead of copying and pasting.
  </details>

_4. What command will open the Control Panel? (The answer is the name of .exe, not the full path)_

  <details>
    <summary>Answer</summary>

    control.exe
  </details>

---

# Task 3 - Change UAC Settings

We're continuing with Tools that are available through the _System Configuration_ panel.

_User Account Control_ (UAC) was covered in great detail in [Windows Fundamentals 1](https://tryhackme.com/room/windowsfundamentals1xbx).

The UAC settings can be changed or even turned off entirely (_not recommended_).

You can move the slider to see how the setting will change the UAC settings and Microsoft's stance on the setting.

![uac](https://github.com/djiotua/tryhackme/assets/134016731/7f5885f9-7451-4a44-bb9f-54cfae842b55)

---

_1. What is the command to open User Account Control Settings? (The answer is the name of the .exe file, not the full path)_

  <details>
    <summary>Answer</summary>

    UserAccountControlSettings.exe
  </details>

---

# Task 4 - Computer Management

We're continuing with Tools that are available through the _System Configuration_ panel.

The _Computer Management_ (_compmgmt_) utility has three primary sections: _System Tools_, _Storage_, and _Services and Applications_.

![compmgmt1](https://github.com/djiotua/tryhackme/assets/134016731/04e80236-589e-44a0-a42c-ca7183aba906)

### System Tools

Let's start with _Task Scheduler_. Per Microsoft, with Task Scheduler, we can create and manage common tasks that our computer will carry out automatically at the times we specify.

A task can run an application, a script, etc., and tasks can be configured to run at any point. A task can run at log in or at log off. Tasks can also be configured to run on a specific schedule, for example, every five mins.

To create a basic task, click on _Create Basic Task_ under _Actions_ (right pane).

![create-task](https://github.com/djiotua/tryhackme/assets/134016731/00d1fdf5-abd4-4b1e-8adb-70231e13ed44)

Next is _Event Viewer_.

Event Viewer allows us to view events that have occurred on the computer. These records of events can be seen as an audit trail that can be used to understand the activity of the computer system. This information is often used to diagnose problems and investigate actions executed on the system.

![event-viewer](https://github.com/djiotua/tryhackme/assets/134016731/e46a9297-8498-4956-b126-c11fd55b169e)

Event Viewer has three panes.

1. The pane on the left provides a hierarchical tree listing of the event log providers. (as shown in the image above)
2. The pane in the middle will display a general overview and summary of the events specific to a selected provider.
3. The pane on the right is the actions pane.
   
There are five types of events that can be logged. Below is a table from [docs.microsoft.com](https://learn.microsoft.com/en-us/windows/win32/eventlog/event-types) providing a brief description for each.

![five-event-types](https://github.com/djiotua/tryhackme/assets/134016731/5b3c413c-6e0c-4cf9-a691-4b90021c1228)

The standard logs are visible under _Windows Logs_. Below is a table from [docs.microsoft.com](https://learn.microsoft.com/en-us/windows/win32/eventlog/eventlog-key) providing a brief description for each.

![standard-event-logs](https://github.com/djiotua/tryhackme/assets/134016731/b2e54d05-99f5-4491-b8d4-17affe602bed)

For more information about Event Viewer and Event Logs, please refer to the Windows Event Log [room](https://tryhackme.com/room/windowseventlogs).

_Shared Folders_ is where you will see a complete list of shares and folders shared that others can connect to.

![shared-folders](https://github.com/djiotua/tryhackme/assets/134016731/18772395-b647-40f7-a29e-a6db37fe53b1)

In the above image, under Shares, are the default share of Windows, C$, and default remote administration shares created by Windows, such as ADMIN$. 

As with any object in Windows, you can right-click on a folder to view its properties, such as Permissions (who can access the shared resource). 

Under _Sessions_, you will see a list of users who are currently connected to the shares. In this VM, you won't see anybody connected to the shares.

All the folders and/or files that the connected users access will list under _Open Files_.

The _Local Users and Groups_ section you should be familiar with from Windows Fundamentals 1 because it's _lusrmgr.msc_.

In _Performance_, you'll see a utility called _Performance Monitor_ (perfmon).

Perfmon is used to view performance data either in real-time or from a log file. This utility is useful for troubleshooting performance issues on a computer system, whether local or remote. 

![perfmon](https://github.com/djiotua/tryhackme/assets/134016731/3a542352-e5d6-4a16-b99f-401241a8ba8c)

_Device Manager_ allows us to view and configure the hardware, such as disabling any hardware attached to the computer.

![device-mgr](https://github.com/djiotua/tryhackme/assets/134016731/d8269c1f-0584-4fe6-aec2-9b7a6cf7f272)

### Storage

Under Storage is _Windows Server Backup_ and _Disk Management_. We'll only look at Disk Management in this room.

_Note: Since the virtual machine is a Windows Server operating system, there are utilities available that you will typically not see in Windows 10._

![disk-mgmt](https://github.com/djiotua/tryhackme/assets/134016731/a2301fd3-ea63-4d91-b7ab-104121f87eb2)

Disk Management is a system utility in Windows that enables you to perform advanced storage tasks.  Some tasks are:

- Set up a new drive
- Extend a partition
- Shrink a partition
- Assign or change a drive letter (ex. E:)

### Services and Applications

![services-apps](https://github.com/djiotua/tryhackme/assets/134016731/8cc72faf-b6e2-4cec-97ce-4ff96f6a02e6)

Recall from the previous task; a service is a special type of application that runs in the background. Here you can do more than enable and disable a service, such as view the Properties for the service.

![service](https://github.com/djiotua/tryhackme/assets/134016731/cb7bc788-15d8-4cdd-a195-2c7b9a75a0eb)

WMI Control configures and controls the _Windows Management Instrumentation_ (WMI) service.

Per Wikipedia, "_WMI allows scripting languages (such as VBScript or Windows PowerShell) to manage Microsoft Windows personal computers and servers, both locally and remotely. Microsoft also provides a command-line interface to WMI called Windows Management Instrumentation Command-line (WMIC)._"

_Note: The WMIC tool is deprecated in Windows 10, version 21H1. Windows PowerShell supersedes this tool for WMI._

---

_1. What is the command to open Computer Management? (The answer is the name of the .msc file, not the full path)_

  <details>
    <summary>Answer</summary>

    compmgmt.msc
  </details>

_2. At what time every day is the GoogleUpdateTaskMachineUA task configured to run?_

  <details>
    <summary>Answer</summary>

    6:15 AM
  </details>

  <details>
    <summary>Explanation</summary>

    In "Task Scheduler", I viewed the "Active Tasks".
  </details>

_3. What is the name of the hidden folder that is shared?_

  <details>
    <summary>Answer</summary>

    sh4r3dF0Ld3r
  </details>

  <details>
    <summary>Explanation</summary>

    I went to "Shared Folders", then "Shares".
  </details>

---

# Task 5 - System Information

We're continuing with Tools that are available through the _System Configuration_ panel.

What is the _System Information_ (_msinfo32_) tool?

Per Microsoft, "_Windows includes a tool called Microsoft System Information (Msinfo32.exe).  This tool gathers information about your computer and displays a comprehensive view of your hardware, system components, and software environment, which you can use to diagnose computer issues._"

The information in _System Summary_ is divided into three sections:

- Hardware Resources
- Components
- Software Environment
  
System Summary will display general technical specifications for the computer, such as processor brand and model.

![system-summary](https://github.com/djiotua/tryhackme/assets/134016731/d2753908-563b-44d7-9b6f-09f42322fba5)

The information displayed in _Hardware Resources_ is not for the average computer user. If you want to learn more about this section, refer to the official Microsoft [page](https://learn.microsoft.com/en-us/windows-hardware/drivers/kernel/hardware-resources).

![hardware-resources](https://github.com/djiotua/tryhackme/assets/134016731/58b38720-7b45-4aaf-b1cb-fff3e6b5eedb)

Under _Components_, you can see specific information about the hardware devices installed on the computer. Some sections don't show any information, but some sections do, such as _Display_ and _Input_.

![components](https://github.com/djiotua/tryhackme/assets/134016731/61dcbc96-69b6-4d84-84a7-738e1572f220)

In the _Software Environment_ section, you can see information about software baked into the operating system and software you have installed. Other details are visible in this section as well, such as the _Environment Variables_ and _Network Connections_.

![software-env](https://github.com/djiotua/tryhackme/assets/134016731/10e80347-0118-4e6c-95b2-c366b78ae008)

Recall from the [Windows Fundamentals 1 room](https://tryhackme.com/room/windowsfundamentals1xbx) (The _Windows\System32_ Folder task) where _Environment Variables_ was briefly touched on.

Per [Microsoft](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-7.3&viewFallbackFrom=powershell-7.1), "_Environment variables store information about the operating system environment. This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders_.

_The environment variables store data that is used by the operating system and other programs. For example, the WINDIR environment variable contains the location of the Windows installation directory. Programs can query the value of this variable to determine where Windows operating system files are located_".

Click on _Environment Variables_ to see the assigned values for the virtual machine.

![env-variables](https://github.com/djiotua/tryhackme/assets/134016731/6318b2a2-7c52-489b-a3e8-d8b48c971900)

Another method to view environment variables is:
- Control Panel > System and Security > System > Advanced system settings > Environment Variables, OR
- Settings > System > About > system info > Advanced system settings > Environment Variables.

![env-variables2](https://github.com/djiotua/tryhackme/assets/134016731/51ccdb6c-b1e5-4d35-9145-645504024e25)

The detour is over. Let's redirect our attention back to _msinfo32_ and pick up where we left off.

Towards the very bottom of this utility, there is a search bar. Please give it a go. Select Components and search for _IP address_.

![msinfo32-search](https://github.com/djiotua/tryhackme/assets/134016731/274e0253-0e73-404c-8d81-a2af987ec47b)

---

_1. What is the command to open System Information? (The answer is the name of the .exe file, not the full path)_

  <details>
    <summary>Answer</summary>

    msinfo32.exe
  </details>

_2. What is listed under System Name?_

  <details>
    <summary>Answer</summary>

    THM-WINFUN2
  </details>

_3. Under Environment Variables, what is the value for ComSpec?_

  <details>
    <summary>Answer</summary>

    %SystemRoot%\system32\cmd.exe
  </details>

  <details>
    <summary>Explanation</summary>

    I went to "Software Environment", then "Environment Variables".
  </details>

---

# Task 6 - Resource Monitor

We're continuing with Tools that are available through the _System Configuration_ panel.

What is _Resource Monitor_ (_resmon_)?

Per Microsoft, "_Resource Monitor displays per-process and aggregate CPU, memory, disk, and network usage information, in addition to providing details about which processes are using individual file handles and modules. Advanced filtering allows users to isolate the data related to one or more processes (either applications or services), start, stop, pause, and resume services, and close unresponsive applications from the user interface. It also includes a process analysis feature that can help identify deadlocked processes and file locking conflicts so that the user can attempt to resolve the conflict instead of closing an application and potentially losing data._"

As some of the other tools mentioned in this room, this utility is geared primarily to advanced users who need to perform advanced troubleshooting on the computer system.

In the Overview tab, Resmon has four sections:

- CPU
- Disk
- Network
- Memory

![resmon1](https://github.com/djiotua/tryhackme/assets/134016731/3865312f-6d79-49fc-9089-725daf6ed24c)

The same four sections have corresponding tabs across the top. See below.

![resmon2](https://github.com/djiotua/tryhackme/assets/134016731/4130f78b-08cf-4c35-98a5-11f658b19691)

Note that each tab has additional information for each. An image is shown below for each tab.

### CPU

![resmon-cpu](https://github.com/djiotua/tryhackme/assets/134016731/556131e7-dc8d-473d-b6dd-97635bceb7ce)

### Memory

![resmon-mem](https://github.com/djiotua/tryhackme/assets/134016731/ac79684c-9e7f-46d0-b7cb-90bb140e3cd5)

### Disk

![resmon-disk](https://github.com/djiotua/tryhackme/assets/134016731/72608dfc-4cb4-450d-befb-a7a7628f6abd)

### Network

![resmon-network](https://github.com/djiotua/tryhackme/assets/134016731/c9fcbe48-e572-435f-86ea-6ab99376c439)

Although not captured in any of the images above, Resource Monitor has a pane at the far right. This pane shows a graphical view in real-time for each section.

_Note: The information displayed in Resource Monitor will be different for you compared to the images above._

---

_1. What is the command to open Resource Monitor? (The answer is the name of the .exe file, not the full path)_

  <details>
    <summary>Answer</summary>

    resmon.exe
  </details>

---

# Task 7 - Command Prompt

We're continuing with Tools that are available through the _System Configuration_ panel.

The command prompt (_cmd_) can seem daunting at first, but it's really not that bad once you understand how to interact with it.

In early operating systems, the command line was the sole way to interact with the operating system.

When the GUI (graphical user interface) was introduced, it allowed users to perform complex tasks with a few clicks of a button instead of entering commands in the command prompt.

Even though the GUI is the primary way to interact with the operating system, a computer user can still interact via the command prompt.

In this task, we'll only cover a few commands that a computer user can run in the command prompt to obtain information about the computer system.

Let's start with a few simple commands, such as _hostname_ and _whoami_.

The command _hostname_ will output the computer name.

![hostname](https://github.com/djiotua/tryhackme/assets/134016731/51dfc4d8-df7f-41f9-b14a-a974b5e421cf)

The command _whoami_ will output the name of the logged-in user.

![whoami](https://github.com/djiotua/tryhackme/assets/134016731/2a1dca0b-6049-480e-a0ad-43bc0a8c21ca)

Next, let's look at some commands that are useful when troubleshooting.

A command used often is _ipconfig_. This command will show the network address settings for the computer.

![ipconfig](https://github.com/djiotua/tryhackme/assets/134016731/b4bab8cc-1de5-44a3-86e1-8bf1d21f990f)

Each command will have a help manual to explain the expected syntax to execute the command properly, along with any additional parameters that can be added to the command to expand its execution.

A  command to retrieve the help manual for a command is _/?_.

For example, to see the help manual for _ipconfig_, you can use the following command: _ipconfig /?_

![ipconfig-help](https://github.com/djiotua/tryhackme/assets/134016731/6044d45f-436f-4e10-b358-af368cd72fa8)

_Note: To clear the command prompt screen, the command is "cls"._

The next command is _netstat_. Per the help manual, this command will display protocol statistics and current TCP/IP network connections.

![netstat](https://github.com/djiotua/tryhackme/assets/134016731/dfb0dfe8-511d-4804-ad0f-f87e0cdbce18)

In the above image, the line within the red box shows us an example syntax for the command. 

The structure tells us the _netstat_ command can be run alone or with parameters, such as _-a_,  _-b_,  _-e_, etc. 

When any of the parameters are appended to the root command, _netstat_ in this case, the output changes. Play with a few to see for yourself. 

The _net_ command is primarily used to manage network resources. This command supports sub-commands.

If you type _net_ without a sub-command, the output will show the syntax for the root command showing a few of the sub-commands you can use.

![net](https://github.com/djiotua/tryhackme/assets/134016731/00cf610c-30f5-44bc-a0ef-76643438cccf)

For the net command, to display the help manual _/?_ will not work. In this case, you need to use different syntax, which is _net help_.

![net-help](https://github.com/djiotua/tryhackme/assets/134016731/46e14f5b-c55d-42d9-a6ab-7852ffb8dd87)

So, if you wish to see the help information for _net user_, the command is _net help user_.

![net-help-user2](https://github.com/djiotua/tryhackme/assets/134016731/bb4ba52b-cf8c-4645-9171-cdf99ef32adc)

You can use the same command to view the help information for other useful _net_ sub-commands, such as _localgroup_, _use_, _share_, and _session_.

Refer to the following link to see a comprehensive list of commands you can execute in the command prompt [here](https://ss64.com/nt/).

---

_1. In System Configuration, what is the full command for Internet Protocol Configuration?_

  <details>
    <summary>Answer</summary>

    C:\Windows\System32\cmd.exe /k %windir%\system32\ipconfig.exe
  </details>

_2. For the "ipconfig" command, how do you show detailed information?_

  <details>
    <summary>Answer</summary>

    ipconfig /all
  </details>

  <details>
    <summary>Explanation</summary>

    If you are not familiar with this command, type "ipconfig /?".
  </details>

---

# Task 8 - Registry Editor

We're continuing with Tools that are available through the _System Configuration_ panel.

The _Windows Registry_ (per Microsoft) is a central hierarchical database used to store information necessary to configure the system for one or more users, applications, and hardware devices.

The registry contains information that Windows continually references during operation, such as:

- Profiles for each user
- Applications installed on the computer and the types of documents that each can create
 -Property sheet settings for folders and application icons
- What hardware exists on the system
- The ports that are being used.
  
_Warning: The registry is for advanced computer users. Making changes to the registry can affect normal computer operations._ 

There are various ways to view/edit the registry. One way is to use the _Registry Editor_ (_regedit_).

![regedit](https://github.com/djiotua/tryhackme/assets/134016731/88ca329d-dfe0-4030-8e48-1b1e8b352583)

Refer to the following Microsoft documentation [here](https://learn.microsoft.com/en-us/troubleshoot/windows-server/performance/windows-registry-advanced-users) to learn more about the Windows Registry.

---

_1. What is the command to open the Registry Editor? (The answer is the name of  the .exe file, not the full path)_

  Hint: Refer to the command in MSConfig.
  
  <details>
    <summary>Answer</summary>

    regedt32.exe
  </details>

---

# Task 9 - Conclusion

Recall that the tasks covered in this room were some of the tools that can launch from _MSConfig_.

Throughout the room, commands and shortcuts were shared for the utilities. This means you don't have to launch _MSConfig_ to run these utilities.

You can also run some of these utilities directly from the Start Menu. See below where some of these utilities can be found.

![start-menu](https://github.com/djiotua/tryhackme/assets/134016731/4421db64-29fc-47da-a811-084b4b036128)

Some of the tools listed in _MSConfig_ that weren't mentioned in this room were either covered in Windows Fundamentals 1 or were left for you to explore on your own.

---

_1. Read above._

No answer needed.

---

END OF ROOM
