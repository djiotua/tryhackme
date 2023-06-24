# Linux Fundamentals Part 3

Power-up your Linux skills and get hands-on with some common utilities that you are likely to use day-to-day!

---

# Task 1 - Introduction

Welcome to part three (and the finale) of the Linux Fundamentals module. So far, throughout the series, you have got hands-on with some fundamental concepts and used some important commands. This room is going to showcase some useful utilities and applications that you are likely to use day-to-day. You're also going to advance your Linux-fu skills by learning about automation, package management, and service/application logging.

---

_1. Let's proceed!_

No answer needed.

---

# Task 2 - Deploy Your Linux Machine

### Deploying Your Linux Machine

Press the green "Start Machine" button on the top-right of this task and then scroll to the top of the page to see the deployment information like so.

![deploy1](https://github.com/djiotua/tryhackme/assets/134016731/d6ba1a39-4fbb-48f6-9455-02a9f2b4fa6e)

The IP address displayed is the address of your Linux machine that you will be logging into using SSH. Take note of this for now.

### Deploying the TryHackMe AttackBox

Looking at the top of the page, press the "_Start AttackBox_" button to deploy the TryHackMe AttackBox that we will be interacting with. The TryHackMe AttackBox is a Ubuntu Linux machine that is hosted online in the cloud and can be interacted with via your browser. You will be using this to interact with the machine that you deploy in this task.

![deploy2](https://github.com/djiotua/tryhackme/assets/134016731/8b881447-d462-4677-8dba-6b11cdac0c6d)

### Use The Following Credentials:

IP Address: MACHINE_IP
Username: tryhackme
Password: tryhackme

---

_1. I've logged into the Linux Fundamentals Part 3 machine using SSH and have deployed the AttackBox successfully!_

No answer needed.

---

# Task 3 - Terminal Text Editors

Throughout the series so far, we have only stored text in files using a combination of the _echo_ command and the pipe operators (_>_ and _>>_). This isn't an efficient way to handle data when you're working with files with multiple lines and the sorts!

### Introducing terminal text editors

There are a few options that you can use, all with a variety of friendliness and utility. This task is going to introduce you to _nano_ but also show you an alternative named _VIM_ (which TryHackMe has a room dedicated to!).

## Nano

It is easy to get started with Nano! To create or edit a file using nano, we simply use _nano filename_ -- replacing "filename" with the name of the file you wish to edit.

  ```bash
  tryhackme@linux3:/tmp# nano myfile
  GNU nano 4.8                                             myfile                                                       

  ^G Get Help    ^O Write Out   ^W Where Is    ^K Cut Text    ^J Justify     ^C Cur Pos     M-U Undo       M-A Mark Text
  ^X Exit        ^R Read File   ^\ Replace     ^U Paste Text  ^T To Spell    ^_ Go To Line  M-E Redo       M-6 Copy Text
  ```

Once we press enter to execute the command, _nano_ will launch! Where we can just begin to start entering or modifying our text. You can navigate each line using the "up" and "down" arrow keys or start a new line using the "Enter" key on your keyboard.

  ```bash
  tryhackme@linux3:/tmp# nano myfile
  GNU nano 4.8                                             myfile                                             Modified  

  Hello TryHackMe
  I can write things into "myfile"


  ^G Get Help    ^O Write Out   ^W Where Is    ^K Cut Text    ^J Justify     ^C Cur Pos     M-U Undo       M-A Mark Text
  ^X Exit        ^R Read File   ^\ Replace     ^U Paste Text  ^T To Spell    ^_ Go To Line  M-E Redo       M-6 Copy Text
  ```

Nano has a few features that are easy to remember & covers the most general things you would want out of a text editor, including:

- Searching for text
- Copying and Pasting
- Jumping to a line number
- Finding out what line number you are on
  
You can use these features of nano by pressing the "_Ctrl_" key (which is represented as an _^_ on Linux)  and a corresponding letter. For example, to exit, we would want to press "Ctrl" and "X" to exit Nano.

## VIM

VIM is a much more advanced text editor. Whilst you're not expected to know all advanced features, it's helpful to mention it for powering up your Linux skills.

![vim1](https://github.com/djiotua/tryhackme/assets/134016731/87af0b43-351d-4847-9f28-167a8923ff07)

Some of VIM's benefits, albeit taking a much longer time to become familiar with, includes:

- Customisable - you can modify the keyboard shortcuts to be of your choosing
- Syntax Highlighting - this is useful if you are writing or maintaining code, making it a popular choice for software developers
- VIM works on all terminals where nano may not be installed
- There are a lot of resources such as [cheatsheets](https://vim.rtorr.com/), tutorials, and the sorts available to you use.

TryHackMe has a [room showcasing VIM](https://tryhackme.com/room/toolboxvim) if you wish to learn more about this editor!

---

_1. Create a file using Nano._

No answer needed.

_2. Edit "task3" located in "tryhackme"'s home directory using Nano. What is the flag?_

  <details>
    <summary>Answer</summary>

    THM{TEXT_EDITORS}
  </details>

  <details>
    <summary>Explanation</summary>

    I used "ls" to check where "task3" is, then used "nano" on task3.

  ```bash
  tryhackme@linux3:~$ ls
  task3
  tryhackme@linux3:~$ nano task3
  ```

    Once you run the "nano" command, it takes you to the Nano text editor, where you will find what this question asks for.
  
  ```bash
    GNU nano 4.8                         task3                                    
  THM{TEXT_EDITORS}
  ```

    When ready, press Ctrl + X to exit Nano.
  </details>

---

# Task 4 - General/Useful Utilities

## Downloading Files

A pretty fundamental feature of computing is the ability to transfer files. For example, you may want to download a program, a script, or even a picture. Thankfully for us, there are multiple ways in which we can retrieve these files.

We're going to cover the use of _wget_.  This command allows us to download files from the web via HTTP -- as if you were accessing the file in your browser. We simply need to provide the address of the resource that we wish to download. For example, if I wanted to download a file named "myfile.txt" onto my machine, assuming I knew the web address it -- it would look something like this:

  ```bash
  wget https://assets.tryhackme.com/additional/linux-fundamentals/part3/myfile.txt
  ```

## Transferring Files From Your Host - SCP (SSH)

Secure copy, or SCP, is just that -- a means of securely copying files. Unlike the regular cp command, this command allows you to transfer files between two computers using the SSH protocol to provide both authentication and encryption.

Working on a model of SOURCE and DESTINATION, SCP allows you to:

- Copy files & directories from your current system to a remote system
- Copy files & directories from a remote system to your current system

Provided that we know usernames and passwords for a user on your current system and a user on the remote system. For example, let's copy an example file from our machine to a remote machine, which I have neatly laid out in the table below.

| Variable | Value |
| --- | --- |
| The IP address of the remote system | 192.168.1.30 |
| User on the remote system | ubuntu |
| Name of the file on the local system | important.txt |
| Name that we wish to store the file as on the remote system | transferred.txt |

With this information, let's craft our _scp_ command (remembering that the format of SCP is just SOURCE and DESTINATION).

  ```bash
  scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt
  ```

And now let's reverse this and layout the syntax for using scpto copy a file from a remote computer that we're not logged into.

| Variable | Value |
| --- | --- |
| IP address of the remote system | 192.168.1.30 |
| User on the remote system | ubuntu |
| Name of the file on the remote system | documents.txt |
| Name that we wish to store the file as on our system | notes.txt |

The command will now look like the following:

  ```bash
  scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt
  ```

## Serving Files From Your Host - WEB

Ubuntu machines come pre-packaged with python3. Python helpfully provides a lightweight and easy-to-use module called "HTTPServer". This module turns your computer into a quick and easy web server that you can use to serve your own files, where they can then be downloaded by another computing using commands such as _curl_ and _wget_. 

Python3's "HTTPServer" will serve the files in the directory that you run the command, but this can be changed by providing options that can be found in the manual pages. Simply, all we need to do is run _python3 -m http.server_ to start the module! In the screenshot below, we are serving from a directory called "webserver", which has a single named "file".

  ```bash
  tryhackme@linux3:/tmp# python3 -m http.server
  Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
  ```

Now, let's use _wget_ to download the file using the computer's IP address and the name of the file. One flaw with this module is that you have no way of indexing, so you must know the exact name and location of the file that you wish to use. This is why I prefer to use Updog. [What's Updog?](https://github.com/sc0tfree/updog) A more advanced yet lightweight webserver. But for now, let's stick to using Python's "HTTP Server".

  ```bash
  tryhackme@linux3:/tmp# wget http://127.0.0.1:8000/file

  2021-05-04 14:26:16  http://127.0.0.1:8000/file
  Connecting to http://127.0.0.1:8000... connected.
  HTTP request sent, awaiting response... 200 OK
  Length: 51095 (50K) [text]
  Saving to: ‘file’

  file                    100%[=================================================>]  49.90K  --.-KB/s    in 0.04s

  2021-05-04 14:26:16 (1.31 MB/s) - ‘file’ saved [51095/51095]
  ```

In the screenshot above, we can see that _wget_ has successfully downloaded the file named "file" to our machine. This request is logged by SimpleHTTPServer much as any web server would, which I have captured in the screenshot below.

  ```bash
  tryhackme@linux3:/tmp# python3 -m http.server
  Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
  127.0.0.1 - - [04/May/2021/14:26:09] "GET /file HTTP/1.1" 200 -
  ```

---

_1. Ensure you are connected to the deployed instance (10.10.158.137)._

No answer needed.

2. 
