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

![Burpsbasics 2](https://github.com/djiotua/tryhackme/assets/134016731/ab12c013-d7f6-4428-b3e9-f62ff7b062f5)
  </details>

_2. In which category can you find reference to a "Cookie jar"?_

  <details>
    <summary>Answer</summary>

    Sessions
  </details>

  <details>
    <summary>Explanation</summary>

    I found where "Cookie Jar" was, in "Project options" then "Sessions".

![Burpsbasics 3](https://github.com/djiotua/tryhackme/assets/134016731/4f8f2493-6395-4cb2-8a7a-5d5c6a8f7900)
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

![Burpsbasics 6](https://github.com/djiotua/tryhackme/assets/134016731/806f3454-ad94-464c-95b7-ec0b22287d59)
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

![Burpsbasics 7](https://github.com/djiotua/tryhackme/assets/134016731/bd552c21-74fc-472e-bac3-a4028cd51250)
  </details>

_6. There are many more configuration options available. Take the time to read through them._

_In the next section, we will cover the Burp Proxy -- a much more hands-on aspect of the room._

No answer needed.

---

# Proxy

# Task 8 - Introduction to the Burp Proxy

The Burp Proxy is the most fundamental (and most important!) of the tools available in Burp Suite. It allows us to capture requests and responses between ourselves and our target. These can then be manipulated or sent to other tools for further processing before being allowed to continue to their destination.

For example, if we make a request to _https://tryhackme.com_ through the Burp Proxy, our request will be captured and won't be allowed to continue to the TryHackMe servers until we explicitly allow it through. We can choose to do the same with the response from the server, although this isn't active by default. This ability to intercept requests ultimately means that we can take complete control over our web traffic -- an invaluable ability when it comes to testing web applications.

There are a few configurations we need to make before we can use the proxy, but let's start by looking at the interface.

_Note: You do not need to follow along with this task -- just read the information and understand what the Proxy is used for._

When we first open the Proxy tab, Burp gives us a bunch of useful information and background reading. This information is well worth reading through; however, the real magic happens after we capture a request.

![73989984d0985412a3405ea1d6f8d171](https://github.com/djiotua/tryhackme/assets/134016731/7477f5cb-82db-4071-b730-9bfdf9164394)

With the proxy active, a request was made to the TryHackMe website. At this point, the browser making the request will hang, and the request will appear in the Proxy tab giving us the view shown in the screenshot above. We can then choose to forward or drop the request (potentially after editing it). We can also do various other things here, such as sending the request to one of the other Burp modules, copying it as a cURL command, saving it to a file, and many others.

When we have finished working with the Proxy, we can click the "Intercept is on" button to disable the Intercept, which will allow requests to pass through the proxy without being stopped.

Burp Suite will still (by default) be logging requests made through the proxy when the intercept is off. This can be very useful for going back and analysing prior requests, even if we didn't specifically capture them when they were made.

Burp will also capture and log WebSocket communication, which, again, can be exceedingly helpful when analysing a web app.

The logs can be viewed by going to the "HTTP history" and "WebSockets history" sub-tabs.

![8d5388b41dc847d2af38acf7ef4b116c](https://github.com/djiotua/tryhackme/assets/134016731/43383904-c74a-4e80-9d35-ea4258c04c4f)

It is worth noting that any requests captured here can be sent to other tools in the framework by right-clicking them and choosing "Send to...". For example, we could take a previous HTTP request that has already been proxied to the target and send it to Repeater.

Finally, there are also Proxy specific options, which in the Proxy Settings, accessible by clicking on the "_Proxy Settings_" button.

These options give us a lot of control over how the proxy operates, so it is an excellent idea to familiarise yourself with these.

For example, the proxy will not intercept server responses by default unless we explicitly ask it to on a per-request basis. We can override the default setting by selecting the "Intercept responses based on the following rules" checkbox and picking one or more rules. The "_Or_ _Request_ _Was Intercepted_" rule is good for catching responses to all requests that were intercepted by the proxy.

![e24fd91064186b78014d6afd773d60f3](https://github.com/djiotua/tryhackme/assets/134016731/9a932773-b029-4a27-944b-885fdbf15d79)

The "_And_ _URL_ _Is in target scope_" is another very good default rule; we will look at scoping later in this room.

You can make your own rules for most of the Proxy options, so this is one section where looking around and experimenting will serve you very well indeed!

Another particularly useful section of this sub-tab is the "Match and Replace" section; this allows you to perform regexes on incoming and outgoing requests. For example, you can automatically change your user agent to emulate a different web browser in outgoing requests or remove all cookies being set in incoming requests. Again, you are free to make your own rules here.

---

_1. Which button would we choose to send an intercepted request to the target in Burp Proxy?_

  <details>
    <summary>Answer</summary>

    Forward
  </details>

  <details>
    <summary>Explanation</summary>

    Forward is to send a request that has been intercepted, to the target. The button is in "Intercept", in "Proxy".

![Burpsbasics 8](https://github.com/djiotua/tryhackme/assets/134016731/e828fa0e-1d6a-4cc8-9c31-e5ee6bb7b61d)
  </details>

_2. Research: What is the default keybind for this?_

_Note: Assume you are using Windows or Linux (i.e. swap Cmd for Ctrl)._

  Hint: Use what you learnt in a previous task to look up the keybindings used in Burp Suite, then find a keybinding related to forwarding intercepted proxy messages.

  <details>
    <summary>Answer</summary>

    Ctrl+F
  </details>

  <details>
    <summary>Explanation</summary>

    I used a cheat sheet which shows all the possible keybinds.

  [Link to the cheat sheet](https://github.com/rinetd/BurpSuite-1/blob/master/CheatSheet.md)

![Burpsbasics 9](https://github.com/djiotua/tryhackme/assets/134016731/6fff7551-7136-42b4-9485-031e4ad9b02d)
  </details>

---

# Task 9 - Connecting through the Proxy (FoxyProxy)

You've seen the theory; now it's time to start using the proxy for yourself.

There are two ways to proxy our traffic through Burp Suite.

1. We could use the embedded browser (_we will cover this in a later task_).
2. We can configure our local web browser to proxy our traffic through Burp; this is more common and so will be the focus of this task.

The Burp Proxy works by opening a web interface on _127.0.0.1:8080_ (by default). As implied by the fact that this is a "proxy", we need to redirect all of our browser traffic through this port before we can start intercepting it with Burp. We can do this by altering our browser settings or, more commonly, by using a Firefox browser extension called [FoxyProxy](https://getfoxyproxy.org/). FoxyProxy allows us to save proxy profiles, meaning we can quickly and easily switch to our "Burp Suite" profile in a matter of clicks, then disable the proxy just as easily.

_Note: All instructions will be given with Firefox in mind, as this is the default browser for both Kali Linux and the TryHackMe AttackBox. If you are using another browser locally then you are advised to use the AttackBox, or you may otherwise need to find alternative methods to those presented in this task. If you can't get the proxy working in your local browser and do not want to use the AttackBox, then you may wish to skip ahead to the Burp Suite Browser task._

There are two versions of FoxyProxy: Basic and Standard. Both versions allow you to change your proxy settings on the fly; however, FoxyProxy Standard gives you a lot more control over what traffic gets sent through the proxy. For example, it will allow you to set pattern matching rules to determine whether a request should be proxied or not: this is more complicated than the simple proxy offered by FoxyProxy basic.

The basic edition is more than adequate for our usage. It is pre-installed and configured in the Firefox browser of the AttackBox, so if you are using the AttackBox, please feel free to skip ahead to the last section of this task.

If you are using your own machine, you can download FoxyProxy Basic [here](https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-basic/).

Once installed, a button should appear at the top right of the screen which allows you to access your proxy configurations.

![fee3f150ebb4d9301023188fddc0458a](https://github.com/djiotua/tryhackme/assets/134016731/a9d5b6ab-0b29-4c94-ab5a-1873fae1eafb)

There are no default configurations, so let's click on the "_Options_" button to create our Burp Proxy config.

This will open a new browser tab with the FoxyProxy options page.

![5a73425b5de3395c5db2962b9d613506](https://github.com/djiotua/tryhackme/assets/134016731/22f6e865-001d-49bb-b988-043725a324f9)

Click on the "_Add_" button and fill in the following values:

- Title: _Burp_ (or anything else you prefer)
- Proxy IP: _127.0.0.1_
- Port: _8080_

![b2d6f2b724f123070ca434bf2759df91](https://github.com/djiotua/tryhackme/assets/134016731/349f7ce4-40d8-415f-a270-c314c98bdd73)

Now click "_Save_".

When you click on the FoxyProxy icon at the top of the screen, you will see that that there is a configuration available for Burp.

![20f5e9db304d164b57c7f7d89fabc63a](https://github.com/djiotua/tryhackme/assets/134016731/ed3a9e6e-557e-4718-bc3f-b7f4daa6122b)

If we click on the "Burp" config, our browser will start directing all of our traffic through _127.0.0.1:8080_. _Be warned_: if Burp Suite is not running, your browser will not be able to make any requests when this config is activated!

Activate this config now -- the icon in the menu should change to indicate that we have a proxy running.

![6a468cdba89180fad2cfb429db0ddf10](https://github.com/djiotua/tryhackme/assets/134016731/d320117b-2144-4fc3-8156-528ba987d0d1)

Next, switch over to Burp Suite and make sure the Intercept is On.

![32b3bdd3afad87b916212f078e0f1795](https://github.com/djiotua/tryhackme/assets/134016731/0970937a-44fb-4bd3-b7eb-b55e1fcba5d3)

Now, try accessing the homepage for _http://10.10.218.45/_ in Firefox. Your browser should hang, and your proxy will populate with the request headers.

Congratulations, you just intercepted your first request!

From here, you can choose to forward or drop the request. Alternatively, you could send it to another tool or perform any number of other actions by right-clicking on the request and selecting an option from the right-click menu.

_Remember: Whilst you are connected to the proxy and have the Proxy Intercept switched on, your browser will hang whenever you make a request. A very common mistake when you are learning to use Burp Suite (and indeed, later on!) is to accidentally leave the intercept switched on and ergo be unable to make any web requests through your browser. If your browser is hanging and you don't know why: check your proxy!_

---

_1. Read through the options in the right-click menu. There is one particularly useful option that allows you to intercept and modify the response to your request. What is this option?_

  <details>
    <summary>Answer</summary>
    
    Response to this request
  </details>

  <details>
    <summary>Explanation</summary>

    I followed the walkthrough. In simple terms, I used FoxyProxy. In the case there was already a configuration, I deleted it, otherwise, follow the steps up until the green Burp icon running.

    After FoxyProxy, I switched to Burp Suite. I made sure that "Intercept is off" so as to not constantly be notified (red flash) from the Burp Suite icon every time I click whilst in Firefox.

    Once I typed the given machine IP address in Firefox, the browser "should hang", then check Burp Suite to see the page contents. This gives you the option to forward or drop.

    The screen should look similar to this:

![Burpsbasics 10](https://github.com/djiotua/tryhackme/assets/134016731/6c46bfe5-a69d-4e63-9423-449ae9d293a8)
  </details>
