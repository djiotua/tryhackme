# Burp Suite: The Basics

An introduction to using Burp Suite for web application pentesting.

---

# Task 1 - Introduction

Welcome to Burp Suite Basics!
This particular room aims to understand the basics of the Burp Suite web application security testing framework. Our focus will revolve around the following key aspects:

1. A thorough introduction to Burp Suite.
2. A comprehensive overview of the various tools available within the framework.
3. Detailed guidance on the process of installing Burp Suite on your system.
4. Navigating and configuring Burp Suite.

We will also introduce the core of the Burp Suite framework, which is the Burp Proxy. It is important to note that this room primarily serves as a foundational resource for acquiring knowledge about Burp Suite. Subsequent rooms in the Burp module will adopt a more practical approach. Thus, this room will contain a greater emphasis on theoretical content. If you have not yet utilised Burp Suite, it is recommended to carefully read the provided information and actively engage with the tool. Experimentation is essential for grasping the fundamentals of this framework. Combining the information presented here with hands-on exploration will establish a strong foundation for utilising the framework. This will significantly assist you in future rooms.

---

_1. Let us start!_

No answer needed.

---

# Task 2 - What is Burp Suite

In essence, Burp Suite is a Java-based framework designed to serve as a comprehensive solution for conducting web application penetration testing. It has become the industry standard tool for hands-on security assessments of web and mobile applications, including those that rely on _application programming interfaces (APIs)_.

Simply put, Burp Suite captures and enables manipulation of all the HTTP/HTTPS traffic between a browser and a web server. This fundamental capability forms the backbone of the framework. By intercepting requests, users have the flexibility to route them to various components within the Burp Suite framework, which we will explore in upcoming sections. The ability to intercept, view, and modify web requests before they reach the target server or even manipulate responses before they are received by our browser makes Burp Suite an invaluable tool for manual web application testing.

Burp Suite is available in different editions. For our purposes, we will focus on the _Burp Suite Community Edition_, which is freely accessible for non-commercial use within legal boundaries. However, it's worth noting that Burp Suite also offers Professional and Enterprise editions, which come with advanced features and require licensing:

1. _Burp Suite Professional_ is an unrestricted version of Burp Suite Community. It comes with features such as:

- An automated vulnerability scanner.
- A fuzzer/brute-forcer that isn't rate limited.
- Saving projects for future use and report generation.
- A built-in API to allow integration with other tools.
- Unrestricted access to add new extensions for greater functionality.
- Access to the Burp Suite Collaborator (effectively providing a unique request catcher self-hosted or running on a Portswigger-owned server).

In short, Burp Suite Professional is a highly potent tool, making it a preferred choice for professionals in the field.

2. _Burp Suite Enterprise_, in contrast to the community and professional editions, is primarily utilized for continuous scanning. It features an automated scanner that periodically scans web applications for vulnerabilities, similar to how tools like Nessus perform automated infrastructure scanning. Unlike the other editions, which allow manual attacks from a local machine, Burp Suite Enterprise resides on a server and constantly scans the target web applications for potential vulnerabilities.

![6b7cdf06b365b6908c41525e8efb86e0](https://github.com/djiotua/tryhackme/assets/134016731/f6f3e4b8-fe29-46f8-8537-defd9696322c)

Due to requiring a license for the Professional and Enterprise editions, we will focus on the core feature set provided by the Burp Suite Community Edition.

_Note: The provided demonstrations utilize Burp Suite for Windows. However, the functionality remains consistent with the version installed on the AttackBox._

---

_1. Which edition of Burp Suite runs on a server and provides constant scanning for target web apps?_

  <details>
    <summary>Answer</summary>

    Burp Suite Enterprise
  </details>

_2. Burp Suite is frequently used when attacking web applications and ______ applications._

  Hint: Fill in the blank.

  <details>
    <summary>Answer</summary>

    Mobile
  </details>

---

# Task 3 - Features of Burp Community

Although Burp Suite Community offers a more limited feature set compared to the Professional edition, it still provides an impressive array of tools that are highly valuable for web application testing. Let's explore some of the key features:

- _Proxy_: The Burp Proxy is the most renowned aspect of Burp Suite. It enables interception and modification of requests and responses while interacting with web applications.
- _Repeater_: Another well-known feature. [Repeater](https://tryhackme.com/room/burpsuiterepeater) allows for capturing, modifying, and resending the same request multiple times. This functionality is particularly useful when crafting payloads through trial and error (e.g., in SQLi - Structured Query Language Injection) or testing the functionality of an endpoint for vulnerabilities.
- _Intruder_: Despite rate limitations in Burp Suite Community, [Intruder](https://tryhackme.com/room/burpsuiteintruder) allows for spraying endpoints with requests. It is commonly utilized for brute-force attacks or fuzzing endpoints.
- _Decoder_: [Decoder](https://tryhackme.com/room/burpsuiteom) offers a valuable service for data transformation. It can decode captured information or encode payloads before sending them to the target. While alternative services exist for this purpose, leveraging Decoder within Burp Suite can be highly efficient.
- _Comparer_: As the name suggests, [Comparer](https://tryhackme.com/room/burpsuiteom) enables the comparison of two pieces of data at either the word or byte level. While not exclusive to Burp Suite, the ability to send potentially large data segments directly to a comparison tool with a single keyboard shortcut significantly accelerates the process.
- _Sequencer_: [Sequencer](https://tryhackme.com/room/burpsuiteom) is typically employed when assessing the randomness of tokens, such as session cookie values or other supposedly randomly generated data. If the algorithm used for generating these values lacks secure randomness, it can expose avenues for devastating attacks.

Beyond the built-in features, the Java codebase of Burp Suite facilitates the development of extensions to enhance the framework's functionality. These extensions can be written in Java, Python (using the Java Jython interpreter), or Ruby (using the Java JRuby interpreter). The _Burp Suite Extender_ module allows for quick and easy loading of extensions into the framework, while the marketplace, known as the _BApp Store_, enables downloading of third-party modules. While certain extensions may require a professional license for integration, there are still a considerable number of extensions available for Burp Community. For instance, the _Logger++_ module can extend the built-in logging functionality of Burp Suite.

---

_1. Which Burp Suite feature allows us to intercept requests between ourselves and the target?_

  <details>
    <summary>Answer</summary>

    Proxy
  </details>

_2. Which Burp tool would we use to brute-force a login form?_

  <details>
    <summary>Answer</summary>

    Intruder
  </details>

---

# Task 4 - Installation

Burp Suite is one of those tools that is very useful to have around, whether for web or mobile application assessments, pentesting, bug bounty hunting, or even debugging features in web app development. Here's a guide on installing Burp Suite on different platforms:

_Note: If you use the AttackBox, Burp Suite is already installed, so you can skip this step._

## Downloads

To download the latest version of Burp Suite for other systems, you may click this [button](https://portswigger.net/burp/releases/) to go to their download page.

_Kali Linux_: Burp Suite comes pre-installed with Kali Linux. In case it is missing on your Kali installation, you can easily install it from the Kali apt repositories.

_Linux, macOS, and Windows_: For other operating systems, PortSwigger provides dedicated installers for Burp Suite Community and Burp Suite Professional on the Burp Suite downloads page. Choose your operating system from the dropdown menu and select _Burp Suite Community Edition_. Then, click the _Download_ button to initiate the download.

![cf27fb99c50eb3c2784212d4f56a7b82](https://github.com/djiotua/tryhackme/assets/134016731/d8fef291-32ae-4817-b4b2-e98c8e3d8c4a)

## Installation

Install Burp Suite using the appropriate method for your operating system. On Windows, run the executable file, while on Linux, execute the script from the terminal (with or without sudo). If you choose not to use _sudo_ during installation on Linux, Burp Suite will be installed in your home directory at _~/BurpSuiteCommunity/BurpSuiteCommunity_ and will not be added to your _PATH_.

The installation wizard provides clear instructions, and it is generally safe to accept the default settings. However, it is always recommended to review the installer carefully.

With Burp Suite successfully installed, you can now launch the application. In the next task, we will explore the initial setup and configuration.

---

_1. If you have chosen not to use the AttackBox, ensure that you have a copy of Burp Suite installed before proceeding._

No answer needed.

---

# Task 5 - The Dashboard

You may use the pre-installed Burp Suite Community Edition in our AttackBox. To launch the AttackBox, click the _Start AttackBox_ button at the top of this page.

Once you launch Burp Suite and accept the terms and conditions, you will be prompted to select a project type. In Burp Suite Community, the options are limited, and you can simply click _Next_ to proceed.

The next window allows you to choose the configuration for Burp Suite. It is generally recommended to keep the default settings, which are suitable for most situations. Click _Start Burp_ to open the main Burp Suite interface.

Upon opening Burp Suite for the first time, you might encounter a screen with training options. It is highly recommended to go through these training materials when you have the time.

If you don't see the training screen (or in subsequent sessions), you will be presented with the Burp Dashboard, which may seem overwhelming at first. However, it will soon become familiar.

The Burp Dashboard is divided into four quadrants, as labelled in counter-clockwise order starting from the top left.

![11202e4c73faa30a757f1439b63b85c6](https://github.com/djiotua/tryhackme/assets/134016731/b4ce5a38-8743-4b4c-90b5-728b67977159)

1. _Tasks_: The Tasks menu allows you to define background tasks that Burp Suite will perform while you use the application. In Burp Suite Community, the default “Live Passive Crawl” task, which automatically logs the pages visited, is sufficient for our purposes in this module. Burp Suite Professional offers additional features like on-demand scans.

2. _Event log_: The Event log provides information about the actions performed by Burp Suite, such as starting the proxy, as well as details about connections made through Burp.

3. _Issue Activity_: This section is specific to Burp Suite Professional. It displays the vulnerabilities identified by the automated scanner, ranked by severity and filterable based on the certainty of the vulnerability.

4. _Advisory_: The Advisory section provides more detailed information about the identified vulnerabilities, including references and suggested remediations. This information can be exported into a report. In Burp Suite Community, this section may not show any vulnerabilities.

Throughout the various tabs and windows of Burp Suite, you will notice question mark icons (![93d5f88c31c7e99d65fda7425a572406](https://github.com/djiotua/tryhackme/assets/134016731/f572b776-16c5-402b-861a-a5d976f4d263)).

Clicking on these icons opens a new window with helpful information specific to that section. These help icons are invaluable when you need assistance or clarification on a particular feature, so make sure to utilise them effectively.

![a68c56aa12934f1fa68758f086a0df3a](https://github.com/djiotua/tryhackme/assets/134016731/667a863e-569e-4eee-aba0-659e4949ba85)

By exploring the different tabs and functionalities of Burp Suite, you will gradually become familiar with its capabilities.

---

_1. What menu provides information about the actions performed by Burp Suite, such as starting the proxy, and details about connections made through Burp?_

  <details>
    <summary>Answer</summary>

    Event log
  </details>

---

# Task 6 - Navigation

In Burp Suite, the default navigation is primarily done through the top menu bars, which allow you to switch between modules and access various sub-tabs within each module. The sub-tabs appear in a second menu bar directly below the main menu bar.

Here's how the navigation works:

1. _Module Selection_: The top row of the menu bar displays the available modules in Burp Suite. You can click on each module to switch between them. For example, the Burp Proxy module is selected in the image below.

![cb50d9d010fd277b7ce2c9acf2481125](https://github.com/djiotua/tryhackme/assets/134016731/8efb73fd-1ac1-413a-a9e0-4145df541932)

2. _Sub-Tabs_: If a selected module has multiple sub-tabs, they can be accessed through the second menu bar that appears directly below the main menu bar. These sub-tabs often contain module-specific settings and options. For example, in the image above, the Proxy Intercept sub-tab is selected within the Burp Proxy module.

3. _Detaching Tabs_: If you prefer to view multiple tabs separately, you can detach them into separate windows. To do this, go to the _Window_ option in the application menu above the _Module Selection_ bar. From there, choose the "Detach" option, and the selected tab will open in a separate window. The detached tabs can be reattached using the same method.

![87c7b704d11abbed8e059a0d33672613](https://github.com/djiotua/tryhackme/assets/134016731/475e4998-04f0-40fd-a488-f3dd0136cf38)

Burp Suite also provides keyboard shortcuts for quick navigation to key tabs. By default, the following shortcuts are available.

| Shortcut | Tab |
| --- | --- |
| Ctrl + Shift + D | Dashboard |
| Ctrl + Shift + T | Target tab |
| Ctrl + Shift + P | Proxy tab |
| Ctrl + Shift + I | Intruder tab |
| Ctrl + Shift + R | Repeater tab |

---

_1. Which tab Ctrl + Shift + P will switch us to?_

  <details>
    <summary>Answer</summary>

    Proxy tab
  </details>

---

# Task 7 - Options

Before diving into the Burp Proxy, let's explore the available options for configuring Burp Suite. There are two types of settings: Global settings (also known as User settings) and Project settings.

- _Global Settings_: These settings affect the entire Burp Suite installation and are applied every time you start the application. They provide a baseline configuration for your Burp Suite environment.

- _Project Settings_: These settings are specific to the current project and apply only during the session. However, please note that Burp Suite Community Edition does not support saving projects, so any project-specific options will be lost when you close Burp.

To access the settings, click on the _Settings_ button in the top navigation bar. This will open a separate settings window.

![40a3ea01d6eadc91d98499c3f921c90f](https://github.com/djiotua/tryhackme/assets/134016731/aad3347b-a449-401f-a71d-ed8b908a3691)

Below is the image showing the separate settings window.

![8a6df0ac968a5c33e91903b350253b6b](https://github.com/djiotua/tryhackme/assets/134016731/f24a90ec-11fe-4787-9fff-0631f2de7fe0)

In the Settings window, you will find a menu on the left-hand side. This menu allows you to switch between different types of settings, including:

1. _Search_: Enables searching for specific settings using keywords.
2. _Type filter_: Filters the settings for _User_ and _Project_ options.
  - _User settings_: Shows settings that affect the entire Burp Suite installation.
  - _Project settings_: Displays settings specific to the current project.
3. _Categories_: Allows selecting settings by category.

![04cf1a4164616772d9495a3ee2bfd10a](https://github.com/djiotua/tryhackme/assets/134016731/52f3c4ed-7dbb-4b50-8c54-3b06fe8869c0)

It's worth noting that many tools within Burp Suite provide shortcuts to specific categories of settings. For example, the _Proxy_ module includes a _Proxy settings_ button that opens the settings window directly to the relevant proxy section.

![09211709d4034aa42ce403780ca12ba0](https://github.com/djiotua/tryhackme/assets/134016731/3e58be53-3eb9-4495-948c-1ffb73badbde)

The search feature on the settings page is a valuable addition, allowing you to quickly search for settings using keywords.

Take some time to familiarise yourself with the range of configurable options in Burp Suite. Once you are comfortable, you can proceed with the exercises related to configuring Burp Suite settings.

---

_1. In which category can you find a reference to a "Cookie jar"?_

  <details>
    <summary>Answer</summary>

    Sessions
  </details>

_2. In which base category can you find the "Updates" sub-category, which controls the Burp Suite update behaviour?_

  Hint: If your answer to this question is "Misc", then you are using an outdated version of Burp Suite. Update to the latest version, then search for the answer in the settings window.

  <details>
    <summary>Answer</summary>

    Suite
  </details>

_3. What is the name of the sub-category which allows you to change the keybindings for shortcuts in Burp Suite?_

  <details>
    <summary>Answer</summary>

    Hotkeys
  </details>

  <details>
    <summary>Explanation</summary>

    Under the "User interface" category
  </details>

_4. If we have uploaded Client-Side TLS certificates, can we override these on a per-project basis (yea/nay)?_

  Hint: Search for "Client TLS Certificates", then look at the scopes provided to the right of the section heading.

  <details>
    <summary>Answer</summary>

    yea
  </details>

---

# Task 8 - Introduction to the Burp Proxy

The Burp Proxy is a fundamental and crucial tool within Burp Suite. It enables the capture of requests and responses between the user and the target web server. This intercepted traffic can be manipulated, sent to other tools for further processing, or explicitly allowed to continue to its destination.

## Key Points to Understand About the Burp Proxy

- _Intercepting Requests_: When requests are made through the Burp Proxy, they are intercepted and held back from reaching the target server. The requests appear in the Proxy tab, allowing for further actions such as forwarding, dropping, editing, or sending them to other Burp modules. To disable the intercept and allow requests to pass through the proxy without interruption, click the _Intercept is on_ button.

![73989984d0985412a3405ea1d6f8d171](https://github.com/djiotua/tryhackme/assets/134016731/f9b8ce1e-7af2-4808-b4dc-25683edda3b9)

- _Taking Control_: The ability to intercept requests empowers testers to gain complete control over web traffic, making it invaluable for testing web applications.

- _Capture and Logging_: Burp Suite captures and logs requests made through the proxy by default, even when the interception is turned off. This logging functionality can be helpful for later analysis and review of prior requests.

- _WebSocket Support_: Burp Suite also captures and logs WebSocket communication, providing additional assistance when analysing web applications.

- _Logs and History_: The captured requests can be viewed in the _HTTP history_ and _WebSockets history_ sub-tabs, allowing for retrospective analysis and sending the requests to other Burp modules as needed.

![8d5388b41dc847d2af38acf7ef4b116c](https://github.com/djiotua/tryhackme/assets/134016731/f00361dc-4abe-47e6-8696-5f00e0313cc0)

Proxy-specific options can be accessed by clicking the _Proxy settings_ button. These options provide extensive control over the Proxy’s behaviour and functionality. Familiarise yourself with these options to optimize your Burp Proxy usage.

## Some Notable Features in the Proxy Settings

- _Response Interception_: By default, the proxy does not intercept server responses unless explicitly requested on a per-request basis. The "Intercept responses based on the following rules" checkbox, along with the defined rules, allows for a more flexible response interception.

![e24fd91064186b78014d6afd773d60f3](https://github.com/djiotua/tryhackme/assets/134016731/7e877753-ed79-4914-9f01-2cac0af818c9)

- _Match and Replace_: The "Match and Replace" section in the _Proxy settings_ enables the use of regular expressions (regex) to modify incoming and outgoing requests. This feature allows for dynamic changes, such as modifying the user agent or manipulating cookies.

Take the time to explore and experiment with the Proxy options, as this will enhance your understanding and proficiency with the tool.

---

_1. Click me to proceed to the next task._

No answer needed.

---

# Task 9 - Connecting through the Proxy (FoxyProxy)
