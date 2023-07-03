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

There are various different editions of Burp Suite available. We will be working with the Burp Suite Community edition, as this is free to use for any (legal) non-commercial use. The Burp Suite Professional and Enterprise editions both require expensive licenses but come with powerful extra features:

- Burp Suite Professional is an unrestricted version of Burp Suite Community. It comes with features such as:
An automated vulnerability scanner
A fuzzer/bruteforcer that isn't rate limited
Saving projects for future use; report generation
A built-in API to allow integration with other tools
Unrestricted access to add new extensions for greater functionality
Access to the Burp Suite Collaborator (effectively providing a unique request catcher self-hosted or running on a Portswigger owned server)
In short, Burp Pro is an extremely powerful tool -- which is why it comes with a £319/$399 price tag per user for a one-year subscription. For this reason, Burp Pro is usually only used by professionals (with licenses often being provided by employers).
Burp Suite Enterprise is slightly different. Unlike the community and professional editions, Burp Enterprise is used for continuous scanning. It provides an automated scanner that can periodically scan webapps for vulnerabilities in much the same way as software like Nessus performs  automated infrastructure scanning. Unlike the other editions of Burp Suite which allow you to perform manual attacks from your own computer, Enterprise sits on a server and constantly scans target web apps for vulnerabilities.
Due to the prohibitive costs involved with either of these editions of Burp Suite, we will stick to the core feature-set provided by Burp Suite Community.

Note: Burp Suite for Windows is featured in the screenshots for many demonstrations; however, there are no differences between this and the copy of Burp Suite installed on the AttackBox.
