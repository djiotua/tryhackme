# Burp Suite: The Basics

An introduction to using Burp Suite for Web Application pentesting

---

# Introduction

# Task 1 - Outline

Welcome to Burp Suite Basics!

This room will cover the foundations of using the Burp Suite web application framework.
Specifically, we will be looking at:

- What Burp Suite is
- An overview of the available tools in the framework
- Installing Burp Suite for yourself
- Navigating and configuring Burp Suite.
  
We will also be introducing the core of the Burp Suite framework: the Burp Proxy. This room is primarily designed to provide a foundational knowledge of Burp Suite which can then be built upon further in the other rooms of the Burp module; as such, it will be a lot heavier in theory than subsequent rooms, which take more of a practical approach. You are advised to read the information here and follow along yourself with a copy of the tool if you haven't used Burp Suite before. Experimentation is key: use this information in tandem with playing around with the app for yourself to build a foundation for using the framework, which can then be built upon in later rooms.

Let's begin!

---

_1. Deploy the machine attached to the task by pressing the green "Start Machine" button, as well as the AttackBox (using the "Start AttackBox" button at the top of the page) if you are not using your own machine._

_Note: If you are not using the AttackBox and want to connect to this machine without the VPN, you can do so using this link once the machine has fully loaded and an IP address is displayed: [https://LAB_WEB_URL.p.thmlabs.com](https://LAB_WEB_URL.p.thmlabs.com)._

No answer needed.

---

# Getting Started

# Task 2 - What is Burp Suite?

Put simply: Burp Suite is a framework written in Java that aims to provide a one-stop-shop for web application penetration testing. In many ways, this goal is achieved as Burp is very much the industry standard tool for hands-on web app security assessments. Burp Suite is also very commonly used when assessing mobile applications, as the same features which make it so attractive for web app testing translate almost perfectly into testing the _APIs_ (_Application Programming Interfaces_) powering most mobile apps.

At the simplest level, Burp can capture and manipulate all of the traffic between an attacker and a webserver: this is the core of the framework. After capturing requests, we can choose to send them to various other parts of the Burp Suite framework -- we will be covering some of these tools in upcoming rooms. This ability to intercept, view, and modify web requests prior to them being sent to the target server (or, in some cases, the responses before they are received by our browser), makes Burp Suite perfect for any kind of manual web app testing.

There are various different editions of Burp Suite available. We will be working with the _Burp Suite Community_ edition, as this is free to use for any (legal) non-commercial use. The Burp Suite Professional and Enterprise editions both require expensive licenses but come with powerful extra features:

- _Burp Suite Professional_ is an unrestricted version of Burp Suite Community. It comes with features such as:
  - An automated vulnerability scanner
  - A fuzzer/bruteforcer that isn't rate limited
  - Saving projects for future use; report generation
  - A built-in API to allow integration with other tools
  - Unrestricted access to add new extensions for greater functionality
  - Access to the Burp Suite Collaborator (effectively providing a unique request catcher self-hosted or running on a Portswigger owned server)
    
In short, Burp Pro is an extremely powerful tool -- which is why it comes with a £319/$399 price tag per user for a one-year subscription. For this reason, Burp Pro is usually only used by professionals (with licenses often being provided by employers).

- _Burp Suite Enterprise_ is slightly different. Unlike the community and professional editions, Burp Enterprise is used for continuous scanning. It provides an automated scanner that can periodically scan webapps for vulnerabilities in much the same way as software like [Nessus](https://tryhackme.com/room/rpnessusredux) performs automated infrastructure scanning. Unlike the other editions of Burp Suite which allow you to perform manual attacks from your own computer, Enterprise sits on a server and constantly scans target web apps for vulnerabilities.
  
Due to the prohibitive costs involved with either of these editions of Burp Suite, we will stick to the core feature-set provided by Burp Suite Community.

_Note: Burp Suite for Windows is featured in the screenshots for many demonstrations; however, there are no differences between this and the copy of Burp Suite installed on the AttackBox._

---

_1. Which edition of Burp Suite will we be using in this module?_

  Hint: The task above contains the answer in bold text. Paragraph Three.

  <details>
    <summary>Answer</summary>

    Burp Suite Community
  </details>

_2. Which edition of Burp Suite runs on a server and provides constant scanning for target web apps?_

  <details>
    <summary>Answer</summary>

    Burp Suite Enterprise
  </details>

_3. Burp Suite is frequently used when attacking web applications and ______ applications._

  Hint: Fill in the blank.

  <details>
    <summary>Answer</summary>

    Mobile
  </details>

---

# Task 3 - Features of Burp Community

Whilst Burp Community has a relatively limited feature-set compared to the Professional edition, it still has many superb tools available. These include:

- _Proxy_: The most well-known aspect of Burp Suite, the Burp Proxy allows us to intercept and modify requests/responses when interacting with web applications.
- _Repeater_: The second most well-known Burp feature -- [Repeater](https://tryhackme.com/room/burpsuiterepeater) -- allows us to capture, modify, then resend the same request numerous times. This feature can be absolutely invaluable, especially when we need to craft a payload through trial and error (e.g. in an _SQLi_ -- _Structured Query Language Injection_) or when testing the functionality of an endpoint for flaws.
- _Intruder_: Although harshly rate-limited in Burp Community, [Intruder](https://tryhackme.com/room/burpsuiteintruder) allows us to spray an endpoint with requests. This is often used for bruteforce attacks or to fuzz endpoints.
- _Decoder_: Though less-used than the previously mentioned features, [Decoder](https://tryhackme.com/room/burpsuiteom) still provides a valuable service when transforming data -- either in terms of decoding captured information, or encoding a payload prior to sending it to the target. Whilst there are other services available to do the same job, doing this directly within Burp Suite can be very efficient.
- _Comparer_: As the name suggests, [Comparer](https://tryhackme.com/room/burpsuiteom) allows us to compare two pieces of data at either word or byte level. Again, this is not something that is unique to Burp Suite, but being able to send (potentially very large) pieces of data directly into a comparison tool with a single keyboard shortcut can speed things up considerably.
- _Sequencer_: We usually use [Sequencer](https://tryhackme.com/room/burpsuiteom) when assessing the randomness of tokens such as session cookie values or other supposedly random generated data. If the algorithm is not generating secure random values, then this could open up some devastating avenues for attack.

In addition to the myriad of in-built features, the Java codebase also makes it very easy to write extensions to add to the functionality of the Burp framework. These can be written in Java, Python (using the Java [Jython](https://www.jython.org/) interpreter), or Ruby (using the Java [JRuby](https://www.jruby.org/) interpreter). The Burp Suite [Extender](https://tryhackme.com/room/burpsuiteextender) module can quickly and easily load extensions into the framework, as well as providing a marketplace to download third-party modules (referred to as the "BApp Store"). Whilst many of these extensions require a professional license to download and add in, there are still a fair number that can be integrated with Burp Community. For example, we may wish to extend the inbuilt logging functionality of Burp Suite with the [Logger++](https://github.com/portswigger/logger-plus-plus) module.

---

_1. Which Burp Suite feature allows us to intercept requests between ourselves and the target?_

  <details>
    <summary>Answer</summary>

    Proxy
  </details>

_2. Which Burp tool would we use if we wanted to bruteforce a login form?_

  <details>
    <summary>Answer</summary>

    Intruder
  </details>

---

# Task 4 - Installation

_Note: The AttackBox already has Burp Suite installed, so please feel free to skip this task if you do not intend to use Burp Suite locally._

Burp Suite is one of those tools that is very useful to have around, whether you're explicitly assessing a web or mobile application for a pentest/bug bounty, or are simply wanting to debug a new feature in a web app you are developing. For this reason, it is important to know how to install Burp Suite on a variety of platforms, rather than just using it inside a pentesting OS such as Kali or Parrot. You never know when you might need it!

Fortunately, [PortSwigger](https://portswigger.net/) have made installing Burp Suite extremely easy on Linux, macOS, and Windows, providing dedicated installers for all three. As a Java application, Burp can also be downloaded as a JAR archive and run on effectively anything that will support a Java runtime environment.

Burp Suite comes pre-packaged with Kali Linux, so you should not need to install it there. If, for some reason, Burp is missing from your Kali installation, you can easily install it from the Kali _apt_ repositories.

For other systems, we can download installers from the [Burp Suite Downloads page](https://portswigger.net/burp/releases/professional-community-2023-6-2?requestededition=community&requestedplatform=).

From the dropdown menus, we can select our operating system, as well as whether we want Burp Suite Community or Burp Suite Professional.

![2fb250ca476cf53cbb0a0e10691c53db](https://github.com/djiotua/tryhackme/assets/134016731/c6439d26-8532-49d4-a2d4-3b7441b2905b)

We can then click the "Download" button to start downloading the Burp Suite installer. No matter which operating system you are using, _make sure to use Burp Suite Community Edition_.

Once we have verified the integrity of our download, we can install it in the normal way for our operating system (e.g. Running the executable in Windows or executing the script from the terminal with _sudo_ in Linux).

_Note: If installing in Linux, you can choose to install either with or without super-user permissions. If you decide_ not _to use sudo when executing the script, Burp Suite will be installed in your home directory at ~/BurpSuiteCommunity/BurpSuiteCommunity and will not be added to your PATH_.

The installation wizard is very intuitive. It is generally safe to accept the suggested defaults, regardless of your operating system; however, it is still sensible to read through the installer carefully.

With Burp Suite installed, we can now start up the application. The first time we use it, Burp Suite will ask us to read and accept its terms and conditions; make sure you do so before accepting or declining them!

With the terms and conditions accepted, we are presented with another menu. We will go through this in the next task.

---

_1. If you have chosen not to use the AttackBox, make sure that you have a copy of Burp Suite installed before proceeding._

No answer needed.

---

# Task 5 - The Dashboard

When we open Burp Suite and have accepted the terms and conditions, we are met with a window asking us to select the project type.

This window doesn't give us many options in Burp Community. Burp Pro would allow us to save our work to the disk or load a previously saved project at this point. All we can do here is click "Next", however.

The next window allows us to choose a configuration for Burp Suite. Leaving this at the default is perfect for most situations:

Click "_Start Burp_", and the main Burp Suite interface will open!

The first time you open Burp Suite, you may be presented with a screen of training options. These are well worth reading through if you get the time.

If not (and in any subsequent sessions regardless), you will be presented with the slightly daunting Burp Dashboard.

![4ed11212a3b11c9bf0eaab1e699e9d51](https://github.com/djiotua/tryhackme/assets/134016731/1d2f69e3-5f0c-4f75-836d-15d7d4e057f8)

Don't be alarmed if this doesn't make too much sense just yet -- it soon will!

In short, the Dashboard interface is split into four quadrants.

![11202e4c73faa30a757f1439b63b85c6](https://github.com/djiotua/tryhackme/assets/134016731/37a81c59-8424-4bdb-8be1-d57a7b27a818)

1. The Tasks menu allows us to define background tasks that Burp Suite will run whilst we use the application. The Pro version would also allow us to create on-demand scans. The default "Live Passive Crawl" (which automatically logs the pages we visit) will be more than suitable for our uses in this module.
2. The Event log tells us what Burp Suite is doing (e.g. starting the Proxy), as well as information about any connections that we are making through Burp.
3. The Issue Activity section is exclusive to Burp Pro. It won't give us anything using Burp Community, but in Burp Professional it would list all of the vulnerabilities found by the automated scanner. These would be ranked by severity and filterable by how sure Burp is that the component is vulnerable.
4. The Advisory section gives more information about the vulnerabilities found, as well as references and suggested remediations. These could then be exported into a report.
Clicking on one of the example vulnerabilities in the Issue Activity section gives us an idea of what this looks like:

![a1e27d91bd58a0038fd0a5902a66f5b9](https://github.com/djiotua/tryhackme/assets/134016731/776d0e49-8bcf-474c-8e2a-9a924857d211)

Throughout the various tabs and windows of Burp Suite, you will find little help icons: a question mark within a circle.

![93d5f88c31c7e99d65fda7425a572406](https://github.com/djiotua/tryhackme/assets/134016731/6e7c2353-f81f-4006-9ddc-8fd27e70ffd9)

Clicking on these will open a new window containing help for the section, for example.

![0266982309d2d272aa6495aedf81a584](https://github.com/djiotua/tryhackme/assets/134016731/f8ee729c-ca52-477f-9a29-4c57b411c523)

These are extremely useful if you're ever stuck and don't know what a feature does, so make good use of them!

---

_1. Open Burp Suite and have a look around the dashboard. Make sure that you are comfortable with it before moving on._

No answer needed.

---

# Task 6 - Navigation

Navigating around the Burp Suite GUI by default is done entirely using the top menu bars:

![cb50d9d010fd277b7ce2c9acf2481125](https://github.com/djiotua/tryhackme/assets/134016731/4dd8caba-ac0b-4648-9d34-aca7ef2e94a1)

These allow you to switch between modules (along the top row of the attached image). If the selected module has more than one sub-tab, then these can be selected using a second menu bar which appears directly below the original bar (the bottom row of the image above). It is common for module-specific settings to be provided in these sub-tabs (as is the case with the Proxy Options above).

Tabs can also be popped out into separate windows should you prefer to view multiple tabs separately. This can be done by clicking "_Window_" in the application menu at the top of the screen, then choosing to "_Detach_" tabs.

![87c7b704d11abbed8e059a0d33672613](https://github.com/djiotua/tryhackme/assets/134016731/0d220917-9816-4f6b-95f1-c8065c65be73)

These can be reattached in the same way.

In addition to the menu bar, Burp Suite also has keyboard shortcuts that allow quick navigation to key tabs. By default, these are:

| Shortcut | Does |
| --- | --- |
| Ctrl + Shift + D | Switch to the Dashboard |
| Ctrl + Shift + T | Switch to the Target tab |
| Ctrl + Shift + P | Switch to the Proxy tab |
| Ctrl + Shift + I | Switch to the Intruder tab |
| Ctrl + Shift + R | Switch to the Repeater tab |

We will look at how we can view and change these in the next task.

---

_1. Get comfortable navigating around the top menu bars._

No answer needed.

---

# Task 7 - Options

Before we start learning about the Burp Proxy, let's take a look at the options available for configuring Burp Suite.

There are two types of settings: _Global Settings_ (also called User Settings), and _Project Settings_.

User settings affect the Burp Suite installation as a whole and will be applied every time we start the application. By contrast, Project Settings only apply to the current project. Given that we can't save projects in Burp Suite Community Edition, this effectively means that any project options we set will be lost every time we close Burp.

Many options are provided as both global settings (which are used to set a baseline) and project settings (which can be used to override the equivalent global setting).

The Settings window can be accessed by clicking on the "_Settings_" button in the top navigation bar:

![8a6df0ac968a5c33e91903b350253b6b](https://github.com/djiotua/tryhackme/assets/134016731/ca430cb3-3780-4884-ab00-1a5dc39aaae2)

On the left hand side we have a menu containing options to change the scope between all settings, user settings, and project settings, as well as search for specific settings, or select them by category.

It should be noted that many of the tools in Burp Suite offer shortcuts to specific categories of settings. For example, the Proxy tool includes a "_Proxy settings_" button which will open the Settings window directly to the section relevant to the proxy.

![09211709d4034aa42ce403780ca12ba0](https://github.com/djiotua/tryhackme/assets/134016731/9743b556-84f7-47dd-bc2f-043af7fd0534)

The Search feature of the settings page is a relatively new addition; however, it is absolutely invaluable, allowing us to search for settings using keywords.

Familiarise yourself with the range of configurable options in Burp Suite, then complete the following exercises.

---

_1. Change the Burp Suite theme to dark mode._

No answer needed.

  <details>
    <summary>Explanation</summary>

    Note: This is from AttackBox.

    Burp Suite's interface may differ from the walkthrough screenshots. So once I started the program, we are greeted with the "Dashboard". There is no "Settings" feature, so I clicked "User options" on the top right.

![Burpsbasics](https://github.com/djiotua/tryhackme/assets/134016731/1206a4c2-9177-4378-9eab-1b60c491e8c7)

    I then went to "Display" on the bar below, then changed from "Light" to "Dark" theme on "User Interface".

![Burpsbasics 2](https://github.com/djiotua/tryhackme/assets/134016731/199f58e4-b6cf-47f7-b6ae-0adf4c972571)
  </details>

_2. In which category can you find reference to a "Cookie jar"?_

  <details>
    <summary>Answer</summary>

    Sessions
  </details>

  <details>
    <summary>Explanation</summary>

    I found where "Cookie Jar" was, in "Project options" then "Sessions".

![Burpsbasics 3](https://github.com/djiotua/tryhackme/assets/134016731/96520728-9215-48e0-89df-0d948558ca6d)
  </details>

_3. In which base category can you find the "Updates" sub-category, which controls the Burp Suite update behaviour?_

  Hint: If your answer to this question is "_Misc_" then you are using an _outdated_ version of Burp Suite. Update to the _latest_ version then search for the answer in the Settings window.
  
  <details>
    <summary>Answer</summary>

    Suite
  </details>

  <details>
    <summary>Explanation</summary>

    The AttackBox has the older version of Burp Suite, in which "Misc" would be incorrect. So I used a virtual machine to open Burp Suite. There, I went into "Settings".

    Note: This is from my virtual machine.

![Burpsbasics 4](https://github.com/djiotua/tryhackme/assets/134016731/0b803e52-f593-4bfe-9dc5-c9209a729f94)

    After this, I went into "Suite" on the left hand side, and there I found "Updates".

![Burpsbasics 5](https://github.com/djiotua/tryhackme/assets/134016731/c3e36793-fb68-4bfe-b687-aae4cfc33313)
  </details>

_4. What is the name of the sub-category which allows you to change the keybindings for shortcuts in Burp Suite?_

  <details>
    <summary>Answer</summary>

    Hotkeys
  </details>

  <details>
    <summary>Explanation</summary>

    I located "Hotkeys" as the first sub-category on "Misc".

    Note: This is now from AttackBox.

![Burpsbasics 6](https://github.com/djiotua/tryhackme/assets/134016731/b68a01ce-221a-4fb7-9c13-f302c023ddb9)
  </details>

_5. If we have uploaded Client-Side TLS certificates, can we override these on a per-project basis (Aye/Nay)?_

  Hint: Search for "_Client TLS Certificates_" then look at the scopes provided to the right of the section heading.

  <details>
    <summary>Answer</summary>

    Aye
  </details>

  <details>
    <summary>Explanation</summary>

    Whilst in "User options", I switched to "TLS", where I found "Client TLS Certificates". The note below the description confirms what the question is talking about.

![Burpsbasics 7](https://github.com/djiotua/tryhackme/assets/134016731/ff37b44a-3888-4476-a316-fd5c3c65133d)
  </details>

_6. There are many more configuration options available. Take the time to read through them._

_In the next section, we will cover the Burp Proxy -- a much more hands-on aspect of the room._

No answer needed.

---

# Proxy

# Task 8 - Introduction to the Burp Proxy

