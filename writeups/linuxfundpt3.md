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

_2. Now, use Python 3's "HTTPServer" module to start a web server in the home directory of the "tryhackme" user on the deployed instance._

  Hint: _python3 -m http.server_

_3. Download the file http://10.10.158.137:8000/.flag.txt onto the TryHackMe AttackBox. What are the contents?_

  Hint: Use wget! It's a hidden file so don't forget the period in .flag.txt when downloading and catting.
  
  <details>
    <summary>Answer</summary>

    THM{WGET_WEBSERVER}
  </details>

  <details>
    <summary>Explanation</summary>

    I used question 2, as well as the hint, to start the process.

  ```bash
  tryhackme@linux3:~$ python3 -m http.server
  Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
  ```

    I then opened another terminal using "tmux", which, in my case, created horizontally-split screen, then used "wget" on the new terminal to download the flag in question.

  ```bash
  tryhackme@linux3:~$ wget http://MACHINE_IP:8000/.flag.txt
  --2023-06-24 09:59:43--  http://MACHINE_IP:8000/.flag.txt
  Connecting to MACHINE_IP:8000... connected.
  HTTP request sent, awaiting response... 200 OK
  Length: 20 [text/plain]
  Saving to: '.flag.txt.1'

  .flag.txt.1         100%[===================>]      20  --.-KB/s    in 0s      

  2023-06-24 09:59:43 (260 KB/s) - '.flag.txt.1' saved [20/20]
  ```

    As I downloaded the flag, I immediately noticed this line from the first terminal screen (with python3):

  ```bash
  MACHINE_IP - - [24/Jun/2023 09:59:43] "GET /.flag.txt HTTP/1.1" 200 -
  ```

    From the "wget" terminal, I used "cat .flag.txt" to see the contents (and the flag!), since it was saved as ".flag.txt".

  ```bash
  tryhackme@linux3:~$ cat .flag.txt
  THM{WGET_WEBSERVER}
  ```
  </details>

_4. Create and download files to further apply your learning -- see how you can read the documentation on Python3's "HTTPServer" module. Use Ctrl + C to stop the Python3 HTTPServer module once you are finished._

  Hint: _https://docs.python.org/3/library/http.server.html_

No answer needed.

  <details>
    <summary>Explanation</summary>

    Once I used "Ctrl + C" to stop the Python3 module, the terminal showed as:

  ```bash
  MACHINE_IP - - [24/Jun/2023 09:59:43] "GET /.flag.txt HTTP/1.1" 200 -
  ^C
  Keyboard interrupt received, exiting.
  tryhackme@linux3:~$
  ```
  </details>

  ---

# Task 5 - Processes 101

Processes are the programs that are running on your machine. They are managed by the kernel, where each process will have an ID associated with it, also known as its PID. The PID increments for the order in which the process starts. I.e. the 60th process will have a PID of 60.

## Viewing Processes

We can use the friendly _ps_ command to provide a list of the running processes as our user's session and some additional information such as its status code, the session that is running it, how much usage time of the CPU it is using, and the name of the actual program or command that is being executed:

![ps1](https://github.com/djiotua/tryhackme/assets/134016731/6c0ad6e0-8c0b-4526-9f2f-d21534a23c1e)

Note how in the screenshot above, the second process ps has a PID of 204, and then in the command below it, this is then incremented to 205.

To see the processes run by other users and those that don't run from a session (i.e. system processes), we need to provide aux to the ps command like so: _ps aux_.

![ps2](https://github.com/djiotua/tryhackme/assets/134016731/73f9cf1b-b0d4-43d4-bc4a-1d49092437e5)

Note we can see a total of 5 processes -- note how we now have "_root_" and "_cmnatic_".

Another very useful command is the top command; top gives you real-time statistics about the processes running on your system instead of a one-time view. These statistics will refresh every 10 seconds, but will also refresh when you use the arrow keys to browse the various rows. Another great command to gain insight into your system is via the _top_ command.

![top1](https://github.com/djiotua/tryhackme/assets/134016731/770c16eb-9643-477d-a894-89fe3b3b2290)

## Managing Processes

You can send signals that terminate processes; there are a variety of types of signals that correlate to exactly how "cleanly" the process is dealt with by the kernel. To kill a command, we can use the appropriately named _kill_ command and the associated PID that we wish to kill. i.e., to kill PID 1337, we'd use _kill 1337_.

Below are some of the signals that we can send to a process when it is killed:

- SIGTERM - Kill the process, but allow it to do some cleanup tasks beforehand
- SIGKILL - Kill the process - doesn't do any cleanup after the fact
- SIGSTOP - Stop/suspend a process

## How do Processes Start?

Let's start off by talking about namespaces. The Operating System (OS) uses namespaces to ultimately split up the resources available on the computer to (such as CPU, RAM and priority) processes. Think of it as splitting your computer up into slices -- similar to a cake. Processes within that slice will have access to a certain amount of computing power, however, it will be a small portion of what is actually available to every process overall.

Namespaces are great for security as it is a way of isolating processes from another -- only those that are in the same namespace will be able to see each other.

We previously talked about how PID works, and this is where it comes into play. The process with an ID of 0 is a process that is started when the system boots. This process is the system's init on Ubuntu, such as _systemd_, which is used to provide a way of managing a user's processes and sits in between the operating system and the user. 

For example, once a system boots and it initialises, systemd is one of the first processes that are started. Any program or piece of software that we want to start will start as what's known as a child process of systemd. This means that it is controlled by systemd, but will run as its own process (although sharing the resources from systemd) to make it easier for us to identify and the likes.

![process1](https://github.com/djiotua/tryhackme/assets/134016731/46e1ce8b-15c6-4232-8b5b-0da8fd8a3e72)

## Getting Processes/Services to Start on Boot

Some applications can be started on the boot of the system that we own. For example, web servers, database servers or file transfer servers. This software is often critical and is often told to start during the boot-up of the system by administrators.

In this example, we're going to be telling the apache web server to be starting apache manually and then telling the system to launch apache2 on boot.

Enter the use of _systemctl_ -- this command allows us to interact with the systemd process/daemon. Continuing on with our example, systemctl is an easy to use command that takes the following formatting: _systemctl [option] [service]_

For example, to tell apache to start up, we'll use _systemctl start apache2_. Seems simple enough, right? Same with if we wanted to stop apache, we'd just replace the _[option]_ with stop (instead of start like we provided)

We can do four options with _systemctl_:

- Start
- Stop
- Enable
- Disable

## An Introduction to Backgrounding and Foregrounding in Linux

Processes can run in two states: In the background and in the foreground. For example, commands that you run in your terminal such as "echo" or things of that sort will run in the foreground of your terminal as it is the only command provided that hasn't been told to run in the background. "Echo" is a great example as the output of echo will return to you in the foreground, but wouldn't in the background - take the screenshot below, for example.

![bg1](https://github.com/djiotua/tryhackme/assets/134016731/f09e5258-d7e4-4fc4-8253-5d552bdc8a88)

Here we're running _echo "Hi THM"_, where we expect the output to be returned to us like it is at the start. But after adding the _&_ operator to the command, we're instead just given the ID of the echo process rather than the actual output -- as it is running in the background.

This is great for commands such as copying files because it means that we can run the command in the background and continue on with whatever further commands we wish to execute (without having to wait for the file copy to finish first)

We can do the exact same when executing things like scripts -- rather than relying on the & operator, we can use _Ctrl + Z_ on our keyboard to background a process. It is also an effective way of "pausing" the execution of a script or command like in the example below.

![bg2](https://github.com/djiotua/tryhackme/assets/134016731/e7f87dab-5b00-4f28-94ef-c190e20c96eb)

This script will keep on repeating "This will keep on looping until I stop!" until I stop or suspend the process. By using _Ctrl + Z_ (as indicated by T^Z). Now our terminal is no longer filled up with messages -- until we foreground it, which we will discuss below.

### Foregrounding a process

Now that we have a process running in the background, for example, our script "background.sh" which can be confirmed by using the _ps aux_ command, we can back-pedal and bring this process back to the foreground to interact with.

![bg3](https://github.com/djiotua/tryhackme/assets/134016731/6b45c4f0-ac2b-45a2-873a-de62dc86aa14)

With our process backgrounded using either _Ctrl + Z_ or the _&_ operator, we can use _fg_ to bring this back to focus like below, where we can see the _fg_ command is being used to bring the background process back into use on the terminal, where the output of the script is now returned to us.

![bg4](https://github.com/djiotua/tryhackme/assets/134016731/b7f34ebc-6a24-456d-a899-d7769dde498a)

![bg5](https://github.com/djiotua/tryhackme/assets/134016731/4974876a-a364-4340-a0c9-6f5cd87c5b17)

---

_1. Read me!_

No answer needed.

_2. If we were to launch a process where the previous ID was "300", what would the ID of this new process be?_

  <details>
    <summary>Answer</summary>

    301
  </details>

  <details>
    <summary>Explanation</summary>

    Since process IDs go by sequence, if the process ID was 300 and there are no new processes launched since 300, then the next available ID is 301. But depending on other processes, the process ID may be higher than 301.
  </details>

_3. If we wanted to cleanly kill a process, what signal would we send it?_

  <details>
    <summary>Answer</summary>

    SIGTERM
  </details>

  <details>
    <summary>Explanation</summary>

    SIGTERM includes cleanup beforehand, SIGKILL does not, and SIGSTOP stops or suspends a process.
  </details>

_4. Locate the process that is running on the deployed instance (10.10.60.198). What flag is given?_

  Hint: Use ps aux to list all running processes. We're looking for a process that seems "out of the ordinary".

  <details>
    <summary>Answer</summary>

    THM{PROCESSES}
  </details>

  <details>
    <summary>Explanation</summary>

    I used the hint, and had to scroll to find the flag, under the COMMAND section.

  ```bash
  tryhackme@linux3:~$ ps aux
  USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
  root           1  0.5  0.5 102508 11244 ?        Ss   11:24   0:04 /sbin/init
  root           2  0.0  0.0      0     0 ?        S    11:24   0:00 [kthreadd]
  ...
  root         482  0.0  0.0   2364   576 ?        S    11:24   0:00 THM{PROCESSES}
  ...
  ```
  </details>

_5. What command would we use to stop the service "myservice"?_

  Hint: _systemctl [option] [service]_

  <details>
    <summary>Answer</summary>

    systemctl stop myservice
  </details>

_6. What command would we use to start the same service on the boot-up of the system?_

  Hint: Same as question 5.

  <details>
    <summary>Answer</summary>

    systemctl enable myservice
  </details>

  <details>
    <summary>Explanation</summary>

    To "enable" is to enable a service to start automatically during the system's boot-up.
  </details>

_7. What command would we use to bring a previously backgrounded process back to the foreground?_

  <details>
    <summary>Answer</summary>

    fg
  </details>

  <details>
    <summary>Explanation</summary>

    "fg" means foreground.
  </details>

---

# Task 6 - Maintaining Your System: Automation

Users may want to schedule a certain action or task to take place after the system has booted. Take, for example, running commands, backing up files, or launching your favourite programs on, such as Spotify or Google Chrome.

We're going to be talking about the _cron_ process, but more specifically, how we can interact with it via the use of _crontabs_. Crontab is one of the processes that is started during boot, which is responsible for facilitating and managing cron jobs.

![cron1](https://github.com/djiotua/tryhackme/assets/134016731/df0afa99-fe87-434e-bda2-af38b255622c)

A crontab is simply a special file with formatting that is recognised by the _cron_ process to execute each line step-by-step. Crontabs require 6 specific values:

| Value	| Description |
| --- | --- |
| MIN | What minute to execute at |
| HOUR | What hour to execute at |
| DOM | What day of the month to execute at |
| MON | What month of the year to execute at |

Let's use the example of backing up files. You may wish to backup "cmnatic"'s  "Documents" every 12 hours. We would use the following formatting:

  ```bash
  0 *12 * * * cp -R /home/cmnatic/Documents /var/backups/
  ```

An interesting feature of crontabs is that these also support the wildcard or asterisk (*). If we do not wish to provide a value for that specific field, i.e. we don't care what month, day, or year it is executed -- only that it is executed every 12 hours, we simply just place an asterisk.

This can be confusing to begin with, which is why there are some great resources such as the online "[Crontab Generator](https://crontab-generator.org/)" that allows you to use a friendly application to generate your formatting for you! As well as the site "[Cron Guru](https://crontab.guru/)"!

Crontabs can be edited by using _crontab -e_, where you can select an editor (such as _Nano_) to edit your crontab.

![cron2](https://github.com/djiotua/tryhackme/assets/134016731/69a34ceb-ff07-4720-8066-033440ffd429)

![cron3](https://github.com/djiotua/tryhackme/assets/134016731/46991118-db7e-4bf4-86ce-91a4ec402fa3)

---

_1. Ensure you are connected to the deployed instance and look at the running crontabs._

  Hint: Remember that we can use _crontab -e_ to edit the user's crontab file.

No answer needed.

  <details>
    <summary>Explanation</summary>

    By using the "crontab -e" command, we should be able to see the output below:

  ```bash
  tryhackme@linux3:~$ crontab -e
  ```

    Only "crontab" is accepted. Ohter spellings would cause errors, assuming you have not installed the program. Once run, you are taken to the Nano text editor program.
    
  ```bash
      GNU nano 4.8              /tmp/crontab.dN4JLi/crontab                         
  
  # To define the time you can provide concrete values for
  # minute (m), hour (h), day of month (dom), month (mon),
  # and day of week (dow) or use '*' in these fields (for 'any').
   
  # Notice that tasks will be started based on the cron's system
  # daemon's notion of time and timezones.
  ```
  </details>

_2. When will the crontab on the deployed instance (MACHINE_IP) run?_

  Hint: Take a look at the position and the value within the appropriate column.

  <details>
    <summary>Answer</summary>

    @reboot
  </details>

  <details>
    <summary>Explanation</summary>

    At the end of the Nano text, there is a line in white that shows when crontab jobs occur.

  ```bash
  # 
  # m h  dom mon dow   command
  @reboot /var/opt/processes.sh
  ```
  </details>

---

# Task 7 - Maintaining Your System: Package Management

## Introducing Packages & Software Repos

When developers wish to submit software to the community, they will submit it to an "apt" repository. If approved, their programs and tools will be released into the wild. Two of the most redeeming features of Linux shine to light here: User accessibility and the merit of open source tools.

When using the _ls_ command on a Ubuntu 20.04 Linux machine, these files serve as the gateway/registry.

![apt1](https://github.com/djiotua/tryhackme/assets/134016731/949c403d-d412-4994-97e5-5be4adcd720d)

![apt2](https://github.com/djiotua/tryhackme/assets/134016731/b20c9e8f-86af-4ffb-80e1-8823ba176d5d)

Whilst Operating System vendors will maintain their own repositories, you can also add community repositories to your list! This allows you to extend the capabilities of your OS. Additional repositories can be added by using the _add-apt-repository_ command or by listing another provider! For example, some vendors will have a repository that is closer to their geographical location.

## Managing Your Repositories (Adding and Removing)

Normally we use the apt command to install software onto our Ubuntu system. The _apt_ command is a part of the package management software also named apt. Apt contains a whole suite of tools that allows us to manage the packages and sources of our software, and to install or remove software at the same time.

One method of adding repositories is to use the _add-apt-repository_ command we illustrated above, but we're going to walk through adding and removing a repository manually. Whilst you can install software through the use of package installers such as _dpkg_, the benefits of apt means that whenever we update our system -- the repository that contains the pieces of software that we add also gets checked for updates. 

In this example, we're going to add the text editor Sublime Text to our Ubuntu machine as a repository as it is not a part of the default Ubuntu repositories. When adding software, the integrity of what we download is guaranteed by the use of what is called GPG (Gnu Privacy Guard) keys. These keys are essentially a safety check from the developers saying, "here's our software". If the keys do not match up to what your system trusts and what the developers used, then the software will not be downloaded.

So, to start, we need to add the GPG key for the developers of Sublime Text 3. (Note that TryHackMe instances do not have internet access and so we're not expecting you to add this to the machine that you deploy, as it would fail.)

1. Let's download the GPG key and use apt-key to trust it.

  ```bash
  wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
  ```

2. Now that we have added this key to our trusted list, we can now add Sublime Text 3's repository to our apt sources list. A good practice is to have a separate file for every different community/3rd party repository that we add.
  
2.1. Let's create a file named _sublime-text.list_ in _/etc/apt/sources.list.d_ and enter the repository information like so.

![sources1](https://github.com/djiotua/tryhackme/assets/134016731/5274d5c8-0a34-455c-b737-b0832bd6fb80)

2.2. And now use Nano or a text editor of your choice to add & save the Sublime Text 3 repository into this newly created file.

![sources2](https://github.com/djiotua/tryhackme/assets/134016731/2a182793-60fb-4f56-a9d5-df4e346d440c)

2.3. After we have added this entry, we need to update apt to recognise this new entry -- this is done using the _apt update_ command.

2.4. Once successfully updated, we can now proceed to install the software that we have trusted and added to apt using _apt install sublime-text_.

Removing packages is as easy as reversing. This process is done by using the _add-apt-repository --remove ppa:PPA_Name/ppa_ command or by manually deleting the file that we previously added to. Once removed, we can just use _apt remove [software-name-here]_ i.e. _apt remove sublime-text_.

---

_1. Since TryHackMe instances do not have an internet connection...this task only requires you to read through the material._

No answer needed.

---

# Task 8 - Maintaining Your System: Logs

We briefly touched upon log files and where they can be found in Linux Fundamentals Part 1. However, let's quickly recap. Located in the _/var/log_ directory, these files and folders contain logging information for applications and services running on your system. The Operating System (OS) has become pretty good at automatically managing these logs in a process that is known as "rotating".

I have highlighted some logs from three services running on a Ubuntu machine:

- An Apache2 web server
- Logs for the fail2ban service, which is used to monitor attempted brute forces, for example
- The UFW service which is used as a firewall

![log1](https://github.com/djiotua/tryhackme/assets/134016731/74718d78-95a7-43e4-9d89-e0d60ab72f37)

These services and logs are a great way in monitoring the health of your system and protecting it. Not only that, but the logs for services such as a web server contain information about every single request - allowing developers or administrators to diagnose performance issues or investigate an intruder's activity. For example, the two types of log files below that are of interest:

- Access log
- Error log

![log2](https://github.com/djiotua/tryhackme/assets/134016731/3ace01e5-e3ab-4427-b643-b3238f240445)

There are, of course, logs that store information about how the OS is running itself and actions that are performed by users, such as authentication attempts.

----

_1. Look for the apache2 logs on the deployable Linux machine._

  Hint: Located in _/var/log/apache2_.

No answer needed.

_2. What is the IP address of the user who visited the site?_

  <details>
    <summary>Answer</summary>

    10.9.232.111
  </details>

  <details>
    <summary>Explanation</summary>

    I "cd"ed to /var/log/apache2, then used "ls" to see the contents. I then used "cat" on access.log.1 (in green). The contents in white require admin privileges.

  ```bash
  tryhackme@linux3:~$ cd /var/log/apache2
  tryhackme@linux3:/var/log/apache2$ ls
  access.log    error.log    error.log.2.gz
  access.log.1  error.log.1  other_vhosts_access.log
  tryhackme@linux3:/var/log/apache2$ cat access.log.1
  10.9.232.111 - - [04/May/2021:18:18:16 +0000] "GET /catsanddogs.jpg HTTP/1.1" 200 51395 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/90.0.4430.93 Safari/537.36"
  ```
  </details>

_3. What file did they access?_

  <details>
    <summary>Answer</summary>

    catsanddogs.jpg
  </details>

---

# Task 9 - Conclusions & Summaries

Welcome to the end of the Linux Fundamentals module. Your familiarity with Linux will improve as you get to interact with it over time. Linux has the potential to do very powerful things with relative ease (as you have hopefully discovered throughout this module).

To recap, this room introduced you to the following topics:

- Using terminal text editors
- General utilities such as downloading and serving contents using a python webserver
- A look into processes
- Maintaining & automating your system by the use of crontabs, package management, and reviewing logs
  
Continue your learning in some other TryHackMe rooms that are dedicated to Linux tools or utilities:

- Bash Scripting - [https://tryhackme.com/room/bashscripting](https://tryhackme.com/room/bashscripting)
- Regular Expressions - [https://tryhackme.com/room/catregex](https://tryhackme.com/room/catregex)
  
---

_1. Terminate the machine deployed in this room from task 2._

No answer needed.

_2. Continue your learning in other Linux-dedicated rooms._

No answer needed.

---

END OF ROOM
