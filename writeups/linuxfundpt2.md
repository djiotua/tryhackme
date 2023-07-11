# Linux Fundamentals Part 2

Continue your learning Linux journey with part two. You will be learning how to log in to a Linux machine using SSH, how to advance your commands, file system interaction.

---

# Task 1 - Introduction

Welcome to the second part of the reworked "Linux Fundamentals" series. We'll be applying our knowledge from the first installment in this series, so I highly recommend you [completing that room](https://tryhackme.com/room/linuxfundamentalspart1) _before_ proceeding further.

In part 2, we'll be ditching the in-browser functionality and help you get started in what is a fundamental skill in being able to login to and control the terminals of remote machines. Not only this, but the room will also have you:

- Unlocking the potential of your first few commands by introducing you to using flags and arguments
- Advancing your knowledge of the filesystem to perform some more useful commands such as copying and moving files
- Introducing you to the access mechanisms in place to keep files and folders secure and how to identify the things that our current user has access too
- Running your first few scripts and executables!

---

_1. Let's proceed!_

No answer needed.

---

# Task 2 - Accessing Your Linux Machine Using SSH (Deploy)

The in-browser functionality was used in Linux Fundamentals Part 1 to get you directly connected to your first ever Linux machine without any hassle.

In fact, the in-browser functionality uses the exact same protocol that we are going to be using today. This protocol is called Secure Shell or _SSH_ for short and is the common means of connecting to and interacting with the command line of a remote Linux machine.

We will be deploying two machines in this room:

- Your Linux machine
- The TryHackMe AttackBox

### What is SSH & how Does it Work?

Secure Shell or SSH simply is a protocol between devices in an encrypted form. Using cryptography, any input we send in a human-readable format is encrypted for travelling over a network -- where it is then unencrypted once it reaches the remote machine, such as in the diagram below.

![ssh1](https://github.com/djiotua/tryhackme/assets/134016731/b3c4d657-d066-4ab8-985f-f01064dca42b)

You can learn about the various types of encryption on a TryHackMe room. But for now, we only need to understand that:

- SSH allows us to remotely execute commands on another device remotely.
- Any data sent between the devices is encrypted when it is sent over a network such as the Internet.

### Deploying Your Linux Machine

Press the green "_Start Machine_" button on the top-right of this task and then scroll to the top of the page to see the deployment information like so.

![deploy1](https://github.com/djiotua/tryhackme/assets/134016731/8a499792-49f7-4bfe-8119-aba0b17f047f)

The IP address displayed is the address of your Linux machine that you will be logging into using SSH. Take note of this for now.

### Deploying the TryHackMe AttackBox

Looking at the top of the page, press the "Start AttackBox" button to deploy the TryHackMe AttackBox that we will be interacting with. The TryHackMe AttackBox is a Ubuntu Linux machine that is hosted online in the cloud and can be interacted with via your browser. You will be using this to interact with the machine that you deploy in this task.

![ab1](https://github.com/djiotua/tryhackme/assets/134016731/c39cfbee-af09-43f6-8644-df597e53e413)

### Using SSH to Login to Your Linux Machine

The syntax to use SSH is very simple. We only need to provide two things:

1. The IP address of the remote machine
2. Correct credentials to a valid account to login with on the remote machine

For this room, we will be logging in as "tryhackme", whose password is "tryhackme" without the quotation ("") marks. Let's use the IP address of the machine displayed in the card at the top of the room as the IP address and this user, to construct a command to log in to the remote machine using SSH. The command to do so is _ssh_ and then the username of the account, _@_ the IP address of the machine.

But first, we need to open a terminal on the TryHackMe AttackBox. There is an icon placed on the desktop named "Terminal". And now, we can proceed to input commands.

For example: _ssh tryhackme@MACHINE_IP_. Replacing the IP address with the IP address for your Linux target machine. Once executed, we will then be asked to trust the host and then provide a password for the "tryhackme" account, which is also "tryhackme".

![ab2](https://github.com/djiotua/tryhackme/assets/134016731/47e2afdd-beeb-4bd0-bdd5-ae903e9f43ca)

Now that we are connected, any commands that we execute will now execute on the remote machine -- not our own.

_Note: When you type a password into an ssh login prompt there is no visible feedback -- you will not be able to see any text or symbols appear as you type the password. It is still working, however, so just type the password and press enter to login._

---

_1. I've logged into the Linux Fundamentals Part 2 machine using SSH!_

No answer needed.

---

# Task 3 - Introduction to Flags and Switches

A majority of commands allow for arguments to be provided. These arguments are identified by a hyphen and a certain keyword known as flags or switches.

We'll later discuss how we can identify what commands allow for arguments to be provided and understanding what these do exactly.

When using a command, unless otherwise specified, it will perform its default behaviour. For example, _ls_ lists the contents of the working directory. However, hidden files are not shown. We can use flags and switches to extend the behaviour of commands.

Using our _ls_ example, _ls_ informs us that there is only one folder named "_folder1_" as highlighted in the screenshot below. Note that the contents in the screenshots below are only examples.

  ```bash
  tryhackme@linux2:~$ ls
  folder1
  tryhackme@linux2:~$
  ```

However, after using the _-a_ argument (short for _--all_), we now suddenly have an output with a few more files and folders such as ".hiddenfolder". Files and folders with "." are hidden files.

  ```bash
  tryhackme@linux2:~$ ls -a 
  .hiddenfolder folder1
  tryhackme@linux2:~$
  ```

Commands that accept these will also have a _--help_ option. This option will list the possible options that the command accepts, provide a brief description and example of how to use it.

  ```bash
  tryhackme@linux2:~$ ls --help
  Usage: ls [OPTION]... [FILE]...
  List information about the FILEs (the current directory by default).
  Sort entries alphabetically if none of -cftuvSUX nor --sort is specified.

  Mandatory arguments to long options are mandatory for short options too.
    -a, --all                  do not ignore entries starting with .
    -A, --almost-all           do not list implied . and ..
  ...
  ```

This option is, in fact, a formatted output of what is called the man page (short for manual), which contains documentation for Linux commands and applications.

## The Man(ual) Page

The manual pages are a great source of information for both system commands and applications available on both a Linux machine, which is accessible on the machine itself and online.

To access this documentation, we can use the mancommand and then provide the command we want to read the documentation for. Using our _ls_ example, we would use _man ls_ to view the manual pages for _ls_ like so.

  ```bash
  tryhackme@linux2:~$ man ls
  LS(1)                                               User Commands                                               LS(1)

  NAME
         ls - list directory contents

  SYNOPSIS
         ls [OPTION]... [FILE]...

  DESCRIPTION
         List  information  about the FILEs (the current directory by default).  Sort entries alphabetically if none of
         -cftuvSUX nor --sort is specified.

         Mandatory arguments to long options are mandatory for short options too.

         -a, --all
                do not ignore entries starting with .
  ...
  ```

---

_1. Explore the manual page of the ls command._

No answer needed.

_2. What directional arrow key would we use to navigate down the manual page?_

  <details>
    <summary>Answer</summary>

    down
  </details>

_3. What flag would we use to display the output in a "human-readable" way?_

  <details>
    <summary>Answer</summary>

    -h
  </details>

  <details>
    <summary>Explanation</summary>

    Use the "man ls" command, and navigate to -h.

  ```bash
  tryhackme@linux2:~$ man ls
  ...

       -h, --human-readable
              with -l and/or -s, print human readable sizes (e.g., 1K 234M 2G)
  ...
  ```
  </details>

---

# Task 4 - Filesystem Interaction Continued

We covered some of the most fundamental commands when interacting with the filesystem on the Linux machine. For example, we covered how to list and find the contents of folders using _ls_ and _find_ and navigating the filesystem using cd. 

In this task, we're going to learn some more commands for interacting with the filesystem to allow us to:

- create files and folders
- move files and folders
- delete files and folders
  
More specifically, the following commands:

| Command	| Full Name |	Purpose |
| --- | --- | --- |
| touch | touch | Create file |
| mkdir | make directory | Create a folder |
| cp | copy | Copy a file or folder |
| mv | move | Move a file or folder |
| rm | remove | Remove a file or folder |
| file | file | Determine the type of a file |

_Protip: Similarly to using cat, we can provide full file paths, i.e. directory1/directory2/note for all of these commands._

---

## Creating Files and Folders (touch, mkdir)

Creating files and folders on Linux is a simple process. First, we'll cover creating a file. The touch command takes exactly one argument -- the name we want to give the file we create. For example, we can create the file "note" by using _touch note_. It's worth noting that touch simply creates a blank file. You would need to use commands like _echo_ or text editors such as _nano_ to add content to the blank file.

  ```bash
  tryhackme@linux2:~$ touch note
  tryhackme@linux2:~$ ls           
  folder1 note
  ```

This is a similar process for making a folder, which just involves using the _mkdir_ command and again providing the name that we want to assign to the directory. For example, creating the directory "mydirectory" using _mkdir mydirectory_.

  ```bash
  tryhackme@linux2:~$ mkdir mydirectory
  tryhackme@linux2:~$ ls           
  folder1 mydirectory note
  ```

## Removing Files and Folders (rm)

_rm_ is extraordinary out of the commands that we've covered so far. You can simply remove files by using rm. However, you need to provide the _-R_ switch alongside the name of the directory you wish to remove.

  ```bash
  tryhackme@linux2:~$ rm note
  tryhackme@linux2:~$ ls           
  folder1 mydirectory
  ```

  ```bash
  tryhackme@linux2:~$ rm -R mydirectory
  tryhackme@linux2:~$ ls           
  folder1
  ```

## Copying and Moving Files and Folders (cp, mv)

Copying and moving files is an important functionality on a Linux machine. Starting with _cp_, this command takes two arguments:

1. the name of the existing file
2. the name we wish to assign to the new file when copying

_cp_ copies the entire contents of the existing file into the new file. In the screenshot below, we are copying "note" to "note2".

  ```bash
  tryhackme@linux2:~$ cp note note2
  tryhackme@linux2:~$ ls           
  folder1 note note2
  ```

Moving a file takes two arguments, just like the _cp_ command. However, rather than copying and/or creating a new file, _mv_ will merge or modify the second file that we provide as an argument. Not only can you use _mv_ to move a file to a new folder, but you can also use _mv_ to rename a file or folder. For example, in the screenshot below, we are renaming the file "note2" to be named "note3". "note3" will now have the contents of "note2".

  ```bash
  tryhackme@linux2:~$ mv note2 note3
  tryhackme@linux2:~$ ls           
  folder1 note note3
  ```

## Determining File Type

What is often misleading and often catches people out is making presumptions from files as to what their purpose or contents may be. Files usually have what's known as an extension to make this easier. For example, text files usually have an extension of ".txt". But this is not necessary.

So far, the files we have used in our examples haven't had an extension. Without knowing the context of why the file is there -- we don't really know its purpose. Enter the _file_ command. This command takes one argument. For example, we'll use _file_ to confirm whether or not the "note" file in our examples is indeed a text file, like so _file note_.

  ```bash
  tryhackme@linux2:~$ file note
  note: ASCII text
  ```

---

_1. How would you create the file named "newnote"?_

  Hint: Look at the answer formatting - we're not expecting quotation marks for this.

  <details>
    <summary>Answer</summary>

    touch newnote
  </details>

  <details>
    <summary>Explanation</summary>

    To create a new note, I used the "touch" command, followed by a new note aptly named "newnote".

  ```bash
  tryhackme@linux2:~$ touch newnote
  tryhackme@linux2:~$ ls
  important  myfile  myfolder  newnote  unknown1
  ```
  </details>
  
_2. On the deployable machine, what is the file type of "unknown1" in "tryhackme's" home directory?_

  <details>
    <summary>Answer</summary>

    ASCII text
  </details>

  <details>
    <summary>Explanation</summary>

    I used the "file" command to find out the type file, on "unknown1" in this case. I also used the "ls" command to verify if there is "unknown1" in the current directory.

  ```bash
  tryhackme@linux2:~$ ls
  important  myfile  myfolder  newnote  unknown1
  tryhackme@linux2:~$ file unknown1
  unknown1: ASCII text
  ```
  </details>

_3. How would we move the file "myfile" to the directory "myfolder"?_

  <details>
    <summary>Answer</summary>

    mv myfile myfolder
  </details>

  <details>
    <summary>Explanation</summary>

    I used "mv" to simply move a file into a folder in this instance.

  ```bash
  tryhackme@linux2:~$ mv myfile myfolder
  tryhackme@linux2:~$ ls myfolder
  myfile
  ```
  </details>

_4. What are the contents of this file?_

  <details>
    <summary>Answer</summary>

    THM{FILESYSTEM}
  </details>

  <details>
    <summary>Explanation</summary>

    Since I have done question 3, I had to move to the "myfolder" directory, then use "cat" to open "myfile".

  ```bash
  tryhackme@linux2:~$ cd myfolder
  tryhackme@linux2:~$ cat myfile
  THM{FILESYSTEM}
  ```
  </details>

_5. Continue to apply your knowledge and practice the commands from this task._

No answer needed.

---

# Task 5 - Permissions 101

As you would have already found out by now, certain users cannot access certain files or folders. We've previously explored some commands that can be used to determine what access we have and where it leads us. 

In our previous tasks, we learned how to extend the use of commands through flags and switches. Take, for example, the _ls_ command, which lists the contents of the current directory. When using the _-l_ switch, we can see ten columns such as in the screenshot below. However, we're only interested in the first three columns:

  ```bash
  tryhackme@linux2:~$ ls -lh
  -rw-r--r-- 1 cmnatic cmnatic 0 Feb 19 10:37 file1
  -rw-r--r-- 8 cmnatic cmnatic 0 Feb 19 10:37 file2
  ```

Although intimidating, these three columns are very important in determining certain characteristics of a file or folder and whether or not we have access to it. A file or folder can have a couple of characteristics that determine both what actions are allowed and what user or group has the ability to perform the given action -- such as the following:

- Read
- Write
- Execute
  
_Using su to switch to user2_

  ```bash
  tryhackme@linux2:~$ su user2
  Password:
  user2@linux2:/home/tryhackme$
  ```

Let's use the "_cmnatic.pem_" file in our initial screenshot at the top of this task. It has the "-" indicator highlighting that it is a file and then "rw" followed after. This means that only the owner of the file can read and write to this "cmnatic.pem" file but cannot execute it.

## Briefly: The Differences Between Users & Groups

We briefly explored this in Linux fundamentals part 1 (namely, the differences between a regular user and a system user). The great thing about Linux is that permissions can be so granular, that whilst a user technically owns a file, if the permissions have been set, then a group of users can also have either the same or a different set of permissions to the exact same file without affecting the file owner itself.

Let's put this into a real-world context; the system user that runs a web server must have permissions to read and write files for an effective web application. However, companies such as web hosting companies will have to want to allow their customers to upload their own files for their website without being the webserver system user -- compromising the security of every other customer. 

We'll learn the commands necessary to switch between users below.

## Switching Between Users

Switching between users on a Linux install is easy work thanks to the _su_ command. Unless you are the root user (or using root permissions through sudo), then you are required to know two things to facilitate this transition of user accounts:

- The user we wish to switch to
- The user's password
  
The _su_ command takes a couple of switches that may be of relevance to you. For example, executing a command once you log in or specifying a specific shell to use. I encourage you to read the man page for _su_ to find out more. However, I will cover the _-l_ or _--login_ switch.

Simply, by providing the _-l_ switch to _su_, we start a shell that is much more similar to the actual user logging into the system - we inherit a lot more properties of the new user, i.e., environment variables and the likes.

  ```bash
  tryhackme@linux2:~$ su user2
  Password:
  user2@linux2:/home/tryhackme$
  ```

For example, when using _su_ to switch to "user2", our new session drops us into our previous user's home directory. 

  ```bash
  tryhackme@linux2:~$ su -l user2
  Password:
  user2@linux2:~$ pwd
  user2@:/home/user2$
  ```

Where now, after using _-l_, our new session has dropped us into the home directory of "user" automatically. 

---

_1. On the deployable machine, who is the owner of "important"?_

  <details>
    <summary>Answer</summary>

    user2
  </details>

  <details>
    <summary>Explanation</summary>

    The most suitable option would be to use the "ls" command, but adding the "-l" flag, so as to better understand who has permissions to which and who owns certain files or folders. You can also add the "-h" flag if you want to have a slightly better understanding (human readable, remember?).

  ```bash
  tryhackme@linux2:~$ ls -l
  total 12
  -rw-r--r-- 1 user2     user2       14 May  5  2021 important
  drwxr-xr-x 2 tryhackme tryhackme 4096 Jun 23 09:54 myfolder
  -rw-r--r-- 1 tryhackme tryhackme   17 May  4  2021 unknown1
  ```
  </details>

_2. What would the command be to switch to the user "user2"?_

  <details>
    <summary>Answer</summary>

    su user2
  </details>

  <details>
    <summary>Explanation</summary>

    I used the "su" command, to switch between users of course. Unfortunately for now, you cannot apply this command into the AttackBox, as there is no password provided.
  </details>

_3. Now switch to this user "user2" using the password "user2"._

No answer needed.

  <details>
    <summary>Explanation</summary>

    Now that the password has been provided, we can be able to switch to user2.

  ```bash
  tryhackme@linux2:~$ su user2
  Password: 
  user2@linux2:/home/tryhackme$
  ```
  </details>

_4. Output the contents of "important", what is the flag?_

  <details>
    <summary>Answer</summary>

    THM{SU_USER2}
  </details>

  <details>
    <summary>Explanation</summary>

    Assuming you are under "user2", use "ls" to find "important", then "cat" the file.

  ```bash
  user2@linux2:/home/tryhackme$ ls
  important  myfolder  unknown1
  user2@linux2:/home/tryhackme$ cat important
  THM{SU_USER2}
  ```
  </details>

# Task 6 - Common Directories

### /etc

This root directory is one of the most important root directories on your system. The etc folder (short for etcetera) is a commonplace location to store system files that are used by your operating system. 

For example, the sudoers file highlighted in the screenshot below contains a list of the users & groups that have permission to run sudo or a set of commands as the root user.

Also highlighted below are the "_passwd_" and "_shadow_" files. These two files are special for Linux as they show how your system stores the passwords for each user in encrypted formatting called _sha512_.

  ```bash
  tryhackme@linux2:/etc$ ls
  shadow passwd sudoers sudoers.d
  ```

### /var

The "/var" directory, with "var" being short for variable data,  is one of the main root folders found on a Linux install. This folder stores data that is frequently accessed or written by services or applications running on the system. For example, log files from running services and applications are written here (_/var/log_), or other data that is not necessarily associated with a specific user (i.e., databases and the like).

  ```bash
  tryhackme@linux2:/var$ ls
  backups log opt tmp
  ```

### /root

Unlike the /home directory, the _/root_ folder is actually the home for the "root" system user. There isn't anything more to this folder other than just understanding that this is the home directory for the "root" user. But, it is worth a mention as the logical presumption is that this user would have their data in a directory such as _"/home/root"_ by default. 

  ```bash
  root@linux2:~# ls
  myfile myfolder passwords.xlsx
  ```

### /tmp

This is a unique root directory found on a Linux install. Short for "_temporary_", the /tmp directory is volatile and is used to store data that is only needed to be accessed once or twice. Similar to the memory on your computer, once the computer is restarted, the contents of this folder are cleared out.

What's useful for us in pentesting is that any user can write to this folder by default. Meaning once we have access to a machine, it serves as a good place to store things like our enumeration scripts.

  ```bash
  root@linux2:/tmp# ls
  todelete trash.txt rubbish.bin
  ```

---

_1. Read me!_

No answer needed.

_2. What is the directory path that would we expect logs to be stored in?_

  <details>
    <summary>Answer</summary>

    /var/log
  </details>

  <details>
    <summary>Explanation</summary>

    "/var" holds the "log" directory. For the demonstration, I used "cd .." to navigate to the "/var/log" directory, and "ls" to look for contents, and verify if I am the right location.
    
  ```bash
  tryhackme@linux2:~$ cd ..
  tryhackme@linux2:/home$ ls
  tryhackme  ubuntu  user2
  tryhackme@linux2:/home$ cd ..
  tryhackme@linux2:/$ ls
  bin  ...  var
  tryhackme@linux2:/$ cd var/log
  tryhackme@linux2:/var/log$
  ```
  </details>

_3. What root directory is similar to how RAM on a computer works?_

  Hint: The contents of this root directory do not persist after reboot.

  <details>
    <summary>Answer</summary>

    /tmp
  </details>

  <details>
    <summary>Explanation</summary>

    "/tmp" simply holds temporary files, which disappear once the machine is restarted. You can be able to switch between root directories, wherever you are.

  ```bash
  tryhackme@linux2:/var/log$ cd /tmp
  tryhackme@linux2:/tmp$
  ```
  </details>

_4. Name the home directory of the root user._

  <details>
    <summary>Answer</summary>

    /root
  </details>

_5. Now apply your learning and navigate through these directories on the deployed Linux machine._

No answer needed.

---

# Task 7 - Conclusions and Summaries

Nice work! This room was quite theory-heavy and covered quite a range of the fundamentals in getting you familiar with Linux. To quickly recap, this room taught you:

- How to connect to a Linux machine remotely using SSH
- Advancing your use of commands by providing flags, switches and where you can go to learn about these for each command (man pages)
- Some more commands that you'll frequently be using to interact with the filesystem and its contents
- A brief introduction to file permissions & switching users
- A summary paragraph of the important root directories on a Ubuntu Linux install and how we may be able to use the data stored within these.
  
I encourage you to go through this room again once or twice to gain some familiarity with the concepts. After all, practice makes perfect!

---

_1. Proceed to the next task to continue your learning._

No answer needed.

---

# Task 8 - Linux Fundamentals Part 3

Visit part three of the Linux fundamentals series here! [https://tryhackme.com/room/linuxfundamentalspart3](https://tryhackme.com/room/linuxfundamentalspart3)

---

_1. Terminate the machine from task 2!_

No answer needed.

_2. Join Linux Fundamentals Part 3!_

No answer needed.

---

END OF ROOM
