# Burp Suite: Repeater

Learn how to use Repeater to duplicate requests in Burp Suite.

---

# Introduction

# Task 1 - Outline

Welcome to the Burp: Repeater room!

Having covered the basics of using Burp Suite, this room will dive into one of the more powerful aspects of the framework, namely: the Burp Suite Repeater module.

We will be covering how to use Repeater to manipulate and arbitrarily resend captured requests, as well as looking at some of the niftier options available in this awesome tool. Finally, we will encounter a series of examples, including a real-world, extra-mile exercise which we will use to consolidate the more theoretical aspects of the room.

If you have not used Burp Suite before and have not completed the [Burp Basics room](https://tryhackme.com/room/burpsuitebasics), you may wish to do so now before continuing, as this room builds on the foundations covered there.

---

_1. Deploy the machine (and the AttackBox if you are not using your own attack VM), and let's get started!_

_Note: If you are not using the AttackBox and want to connect to this machine without the VPN, you can do so using this link once the machine has fully loaded and an IP address is displayed: [https://LAB_WEB_URL.p.thmlabs.com](https://lab_web_url.p.thmlabs.com/)._

No answer needed.

---

# Repeater

# Task 2 - What is Repeater?

Before we start using Repeater, it will help to have a good idea of what it does.

In short: Burp Suite Repeater allows us to craft and/or relay intercepted requests to a target at will. In layman's terms, it means we can take a request captured in the Proxy, edit it, and send the same request repeatedly as many times as we wish. Alternatively, we could craft requests by hand, much as we would from the _CLI (Command Line Interface)_, using a tool such as cURL to build and send requests.

This ability to edit and resend the same request multiple times makes Repeater ideal for any kind of manual poking around at an endpoint, providing us with a nice _Graphical User Interface (GUI)_ for writing the request payload and numerous views (including a rendering engine for a graphical view) of the response so that we can see the results of our handiwork in action.

The Repeater interface can be split into six main sections -- an annotated diagram can be found below the following bullet points:

1. At the very top left of the tab, we have a list of Repeater requests. We can have many different requests going through Repeater: each time we send a new request to Repeater, it will appear up here.
2. Directly underneath the request list, we have the controls for the current request. These allow us to send a request, cancel a hanging request, and go forwards/backwards in the request history.
3. Still on the left-hand side of the tab, but taking up most of the window, we have the request and response view. We edit the request in the Request view then press send. The response will show up in the Response view.
4. Above the request/response section, on the right-hand side, is a set of options allowing us to change the layout for the request and response views. By default, this is usually side-by-side (horizontal layout, as in the screenshot); however, we can also choose to put them above/below each other (vertical layout) or in separate tabs (combined view).
5. At the right-hand side of the window, we have the Inspector, which allows us to break requests apart to analyse and edit them in a slightly more intuitive way than with the raw editor. We will cover this in a later task.
6. Finally, above the Inspector we have our target. Quite simply, this is the IP address or domain to which we are sending requests. When we send requests to Repeater from other parts of Burp Suite, this will be filled in automatically.

![631e09c2296fbc8d73ed38afa9705a50](https://github.com/djiotua/tryhackme/assets/134016731/d3158fea-eb4b-4a69-a43d-31dcbc88148d)

Don't worry if this doesn't make too much sense just now -- you will get plenty of chances to learn what it does first hand in the upcoming tasks!

---

_1. Familiarise yourself with the Repeater interface._

No answer needed.

---

# Task 3 - Basic Usage

We know what the interface looks like now, but how do we put it to use?

Whilst we _can_ craft requests by hand, it would be much more common to simply capture a request in the Proxy, then send that through to Repeater for editing/resending.

With a request captured in the proxy, we can send to repeater either by right-clicking on the request and choosing "_Send to Repeater_" or by pressing _Ctrl + R_.

Switching back to Repeater, we can see that our request is now available.

![ae762b56b7ecb30a0d861221d41502f5](https://github.com/djiotua/tryhackme/assets/134016731/c0d4c5e3-7595-4b94-abf1-1345000f88df)

The target and Inspector elements are now also showing information; however, we do not yet have a response. When we click the "_Send_" button, the Response section quickly populates.

![11da62185a73223355048c2fc04a1340](https://github.com/djiotua/tryhackme/assets/134016731/69806224-b3bd-4c28-875e-4f8b00807bc6)

If we want to change anything about the request, we can simply type in the Request window and press "Send" again; this will update the Response on the right. For example, changing the "_Connection_" header to _open_ rather than _close_ results in a response "Connection" header with a value of _keep-alive_:

![67d1462106edc86bd676315b3c0cba08](https://github.com/djiotua/tryhackme/assets/134016731/034fc47e-e4cb-4c44-bb1d-945104f7f1a7)

We could then also use the history buttons to the right of the Send button to go forwards and backwards in our modification history.

---

_1. Capture a request to http://MACHINE_IP in the Proxy and send it to Repeater. Practice modifying and re-sending the request numerous times._

No answer needed.

  <details>
    <summary>Explanation</summary>

    
  </details>
