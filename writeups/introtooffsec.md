# Intro to Offensive Security

Hack your first website (legally in a safe environment) and experience an ethical hacker's job.

---

# Task 1 - What is Offensive Security?

In short, offensive security is the process of breaking into computer systems, exploiting software bugs, and finding loopholes in applications to gain unauthorized access to them.

To beat a hacker, you need to behave like a hacker, finding vulnerabilities and recommending patches before a cybercriminal does, as you'll do in this room!

On the flip side, there is also defensive security, which is the process of protecting an organization's network and computer systems by analyzing and securing any potential digital threats; learn more in the digital forensics room.

In a defensive cyber role, you could be investigating infected computers or devices to understand how it was hacked, tracking down cybercriminals, or monitoring infrastructure for malicious activity.

---

_1. Which of the following options better represents the process where you simulate a hacker's actions to find vulnerabilities in a system?_

  - Offensive Security
  - Defensive Security

  <details>
    <summary>Answer</summary>

    Offensive Security
  </details>

---

# Task 2 - Hacking your first machine

﻿﻿﻿Before going into cyber security careers and what offensive security is, let's get you hacking (and yes, its legal, all exercises are fake simulations).

## Your first hack

Click the "_Start Machine_" button. Once loaded in _Split View_ in your browser, you will have access to a machine you'll use to hack a fake bank application called _FakeBank_. If you don't see the machine appear, use the blue _Show Split View_ button on the top-right of this page.

We will use a command-line application called "_GoBuster_" to brute-force FakeBank's website to find hidden directories and pages. GoBuster will take a list of potential page or directory names and tries accessing a website with each of them; if the page exists, it tells you.

### Step 1: Open a terminal

A terminal, also known as the command-line, allows us to interact with a computer without using a graphical user interface. On the machine, open the terminal using the _Terminal_ icon.

### Step 2: Find hidden website pages

Most companies will have an admin portal page, giving their staff access to basic admin controls for day-to-day operations. For a bank, an employee might need to transfer money to and from client accounts. Often these pages are not made private, allowing attackers to find hidden pages that show, or give access to, admin controls or sensitive data.

Type the following command into the terminal to find potentially hidden pages on FakeBank's website using GoBuster (a command-line security application).

  ```bash
  gobuster -u http://fakebank.com -w wordlist.txt dir
  ```

The command will run and show you an output similar to this:

  ```bash
  ubuntu@tryhackme:~/Desktop$ gobuster -u http://fakebank.com -w wordlist.txt dir
  =====================================================
  Gobuster v2.0.1
  =====================================================
  [+] Mode         : dir
  [+] Url/Domain   : http://fakebank.com/
  [+] Threads      : 10
  [+] Wordlist     : wordlist.txt
  [+] Status codes : 200,204,301,302,307,403
  [+] Timeout      : 10s
  =====================================================
  2022/04/11 18:23:28 Starting gobuster
  =====================================================
  /images (Status: 301)
  /DIRECTORY_NAME_OUTPUT (Status: 200)
  =====================================================
  2022/04/11 18:23:38 Finished
  =====================================================
  ```

_Don't worry if you have not used a terminal before - TryHackMe walks you through everything!_

In the command above, _-u_ is used to state the website we're scanning, _-w_ takes a list of words to iterate through to find hidden pages.

You will see that GoBuster scans the website with each word in the list, finding pages that exist on the site. GoBuster will have told you the pages it found in the list of page/directory names (indicated by Status: 200).

### Step 3: Hack the bank

You should have found a secret bank transfer page that allows you to transfer money between accounts at the bank (_/bank-transfer_). Type the hidden page into the FakeBank website on the machine.

This page allows an attacker to steal money from any bank account, which is a critical risk for the bank. As an ethical hacker, you would (with permission) find vulnerabilities in their application and report them to the bank to fix before a hacker exploits them.

Transfer $2000 from the bank account 2276, to your account (account number 8881).

---

If your transfer was successful, you should now be able to see your new balance reflected on your account page. Go there now and confirm you got the money! (You may need to hit _Refresh_ for the changes to appear)

_1. Above your account balance, you should now see a message indicating the answer to this question. Can you find the answer you need?_

  Hint: Make sure your new balance is a positive number. If your balance still shows a negative value (even after refreshing the page), you may need to transfer more money.

  <details>
    <summary>Answer</summary>

    BANK-HACKED
  </details>

_2. If you were a penetration tester or security consultant, this is an exercise you’d perform for companies to test for vulnerabilities in their web applications; find hidden pages to investigate for vulnerabilities._

No answer needed.

_3. Terminate the machine by clicking the red "Terminate" button at the top of the page._

No answer needed.

---

# Task 3 - Careers in cyber security

## How can I start learning?

People often wonder how others become hackers (security consultants) or defenders (security analysts fighting cybercrime), and the answer is simple. Break it down, learn an area of cyber security you're interested in, and regularly practice using hands-on exercises. Build a habit of learning a little bit each day on TryHackMe, and you'll acquire the knowledge to get your first job in the industry.

Trust us; you can do it! Just take a look at some people who have used TryHackMe to get their first security job:

- [Paul](https://tryhackme.com/resources/blog/construction-worker-to-security-engineer-how-paul-used-tryhackme-to-land-his-first-job-in-security) went from a construction worker to a security engineer.
- [Kassandra](https://tryhackme.com/resources/blog/the-teacher-becomes-the-student) went from a music teacher to a security professional.
- [Brandon](https://tryhackme.com/resources/blog/brandons-success-story) used TryHackMe while at school to get his first job in cyber.
 
## What careers are there?

The cyber careers room goes into more depth about the different careers in cyber. However, here is a short description of a few offensive security roles:

- Penetration Tester - Responsible for testing technology products for finding exploitable security vulnerabilities.
- Red Teamer - Plays the role of an adversary, attacking an organization and providing feedback from an enemy's perspective.
- Security Engineer - Design, monitor, and maintain security controls, networks, and systems to help prevent cyberattacks.

---

_1. Read the above, and continue with the next room!_

No answer needed.

---

END OF ROOM
