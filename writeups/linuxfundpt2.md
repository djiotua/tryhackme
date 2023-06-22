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
