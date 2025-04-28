---
title: Manage files from the terminal
description: A tutorial on basic terminal usage and file management
published: true
date: 2025-04-28T08:32:12.825Z
tags: coreutils terminal tutorial
editor: markdown
dateCreated: 2025-04-28T08:32:12.825Z
---


# Manage files from the terminal

While Ubuntu comes with a suite of graphical tools, learning how to use the terminal can
help you exercise more control over your system, gain a deeper understanding of the
underlying processes, and branch out to more complex and powerful applications.

While terminal usage has a very high skill ceiling, many tasks can be accomplished with
just a few fundamental commands. This tutorial will guide you through navigating your
machine’s file system, creating files and directories, and writing and running a shell
script--all from your system's terminal.


## Create a directory

In Linux, a [directory]() is a file that stores the names and metadata of other files.
Directories are typically represented by folders in graphical file managers.

Let's create a directory to work in. Open your system's [terminal
emulator](/general/terminal-emulators)--[`gnome-terminal`](/general/gnome-terminal) is
the default for Ubuntu Desktop--and type the following command before pressing the
'Enter' key:

```bash
mkdir project
```

We can now navigate to our newly created directory by running:

```bash
cd project
```


## Create a file

The [`touch`]() command is used to create empty files. In this case, we'll use it to
create a shell script, which contains commands to carry out when the script is run. In
your terminal, run:

```bash
touch helloworld.sh
```

While the `.sh` extension is not required, it is commonly added to communicate to users
that the file is a shell script.

To verify that our file was created, we can list the current directory's contents by
running:

```bash
ls
```

You should see `helloworld.sh` in the terminal's output. However, every directory also
contains two hidden entries that can be viewed by appending the `-a` option to the `ls`
command. Let's try this out:

```bash
ls -a
```

The output now reads:

```bash
.	..	helloworld.sh
```

The `.` entry references the current directory--`project` in this case--while the `..`
entry references the parent directory.


## Edit the file

When it comes to editing text files, there are many applications you can choose from,
each with varying capabilities and complexity. One of the most user-friendly options is
[nano](), which comes pre-installed on Ubuntu and many other popular Linux
distributions. To edit `helloworld.sh`, run:

```bash
nano helloworld.sh
```

We're now in nano's interactive editor. Let's add a basic command for our script to
carry out. At the top of the file, type:

```bash
echo "Hello, world!"
```

[`echo`]() is a simple command that prints the provided argument to the terminal.

Press `Ctrl+O` to save the file and `Ctrl+X` to close nano.


## Make the script executable

Before we can run our newly-created shell script, we need to let the system know that
it is executable.

First, let's check the current permissions of our shell script by running:

```bash
ls -l helloworld.sh
```

This should produce output similar to the following:

```bash
-rw-rw-r-- 1 <user> <user> 0 Apr 22 16:38 helloworld.sh
```

Pay special attention to the leftmost string of our `helloworld.sh` entry. These are the
file's permissions. The rightmost character of this string denotes whether the file is
executable. To make `helloworld.sh` executable, run:

```bash
chmod +x helloworld.sh
```

Run `ls -l helloworld.sh` again to check the permissions. It should now read:

```bash
-rw-rw-r-x 1 <user> <user> 0 Apr 22 16:39 helloworld.sh
```

Note that the rightmost character in the permissions string changed from a hyphen (`-`)
to an `x`. This means that we can now run our script.


## Run the shell script

We can run `helloworld.sh` by running:

```bash
./helloworld.sh
```

You should see our message echoed back to the terminal:

```bash
Hello, world!
```


## Update the shell script

Let's iterate on our shell script. Reopen `helloworld.sh` in a text editor and replace
its contents with:

```bash
echo "This script is located in:" && pwd
```

The `&&` operator allows you to run commands sequentially, while the [`pwd`]() command
prints the path of the current working directory.

Now that we've changed how our script functions, we should give it a more fitting name.
To do this, we'll use the [`mv`](/general/mv-command) command:

```bash
mv helloworld.sh print-directory.sh
```

The [`mv`]() command expects two arguments, those being the path to the file you want to
move, and the path to the desired destination. This is the standard method for moving
and renaming files from the terminal.

If you run `ls` again, you'll see that the current directory now contains:

```bash
print-directory.sh
```

Run the updated script with `./print-directory.sh` to see the new results:

```bash
This script is located in:
/home/<user>/project
```


## Clean up

Now that we've successfully gone over the most common file management commands, let's
clean up our work. Navigate back to the parent directory by running:

```bash
cd ../
```

To delete the `project` directory, run:

```bash
sudo rm -r project
```

The [`rm`]() command is used to delete files from the terminal, and the `-r` option
tells the system to perform this process recursively, meaning that it will delete any
files or directories referenced by the target directory.

Due to this command's destructive nature, you have to run this command with [`sudo`]
permissions, which grant regular users elevated [`root privileges`]().

Take care when deleting files from the terminal, as they cannot be recovered like in
graphical file managers.


## Conclusion and next steps

Now that you've performed some foundational file management from the terminal, consider
checking out the following resources:

* [Ubuntu CLI cheatsheet](/ubuntu/cli-cheatsheet)
* [Customize GNOME terminal]()
