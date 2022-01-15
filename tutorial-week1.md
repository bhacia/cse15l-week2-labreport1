# Software Tools & Techniques Lab (UCSD CSE15L)
This will be a tutorial to show you how to set up your work environment for this course.

## Installing VSCode
Go to the Visual Studio Code website [here](https://code.visualstudio.com/), to download and install
VSCode! There should be different versions you could download depending on your operating system, for
example OSX for Apple Macbooks and Windows for PCs.

When you're finished, open a window! It should look similar to this:

![Image](https://bhacia.github.io/cse15l-week2-labreport1/vscode-new-window.png)

It may look different depending on your system and settings. For instance, the color theme shown is
called "Tomorrow Night Blue". If you want to change your theme, follow these steps!
1. Go to settings by clicking the gear on the bottom left corner.
2. Click on "Color Theme".
3. Then choose whatever theme you like!

## Remotely Connecting
Here you'll use VSCode to connect to a remote computer at UCSD.

**For those on Windows**, you *must* have some features installed.
1. Open your device's settings.
2. Select "Apps", then "Apps & Features", then "Optional Features".
3. Check the list for both "OpenSSH Client" AND "OpenSSH Server".
4. If you *don't* have them, scroll to the top and select "Add a feature".
5. Find the OpenSSH features that you don't have, then click "Install".

Now look up your course-specific account for CSE15L [here](https://sdacs.ucsd.edu/~icc/index.php).
Then, in VSCode, open a new terminal, then type in your command, which will look like this, except
**wi22** is replaced by the time you're taking this class, and **apl** is replaced by the letters
in your course-specific account.

![Image](https://bhacia.github.io/cse15l-week2-labreport1/vscode-ssh-remote-connect.png)

Your terminal is now connected to a computer in the CSE basement, meaning that any commands you run
will run on that computer! In other terms, your computer is called the client and the UCSD computer
is called the server.

## Trying Some Commands
Try running a few commands! Here are some useful commands to get you started:
- cd ~
- cd
- ls -lat
- ls -a
- ls <directory> where <directory> is /home/linux/ieng6/cs15lwi22/cs15lwi22abc
(where again **wi22** is replaced by the time you're taking this class, and **apl** is replaced by
the letters in your course-specific account.)
- cp /home/linux/ieng6/cs15lwi22/public/hello.txt ~/
- cat /home/linux/ieng6/cs15lwi22/public/hello.txt

Here's an example:
  
![Image](https://bhacia.github.io/cse15l-week2-labreport1/vscode-running-a-command.png)

## Moving Files with scp
In this section, you'll learn how to copy files back and forth between the your comuter (client) and
the UCSD computer (server). To do this, you'll use the **scp** command. Note that you'll always run
this command from the *client*, and remember you shouldn't be logged into ieng6, so log out by
running **exit** in your terminal.

1. First make a random file, for instance HelloWorld.java, and run it using **javac** to compile and
**java** to run.

![Image](https://bhacia.github.io/cse15l-week2-labreport1/vscode-create-and-run-file.png)

2. Then run this command (using your own information as usual).

![Image](https://bhacia.github.io/cse15l-week2-labreport1/vscode-using-scp.png)

3. Log into the server again through ssh, and run the **ls** command in the terminal. Now you should
see the file in your home directory!

![Image](https://bhacia.github.io/cse15l-week2-labreport1/vscode-running-ls-on-server.png)

4. Now run it again using **javac** and **java**.

![Image](https://bhacia.github.io/cse15l-week2-labreport1/vscode-running-file-on-server.png)

## Setting an SSH Key
Notice how when you log into the server, you always have to type in your password, which can be time
consuming. To avoid this, you can use **ssh** keys! First and foremost, log off of the server again.

Now run this:

![Image](https://bhacia.github.io/cse15l-week2-labreport1/vscode-rsa-key-pair.png)

Now you have two new files on your system: the private key (id_rsa) and the public key (id_rsa.pub),
which are stored in the .ssh directory on your computer.

Now you're going to copy the **public** key to the .ssh directory of your user account on the server by
running this:

$ ssh cs15lwi22apl@ieng6.ucsd.edu
$ <Enter Password>
$ (now on server)
$ mkdir .ssh
$ exit
$ (back on client)
$ scp C:\Users\15624/.ssh/id_rsa.pub cs15lwi22apl@ieng6.ucsd.edu:~/.ssh/authorized_keys
$ (use the public key you copied)

Now you should be able to log into the server without having to input your password!

## Optimizing Remote Running
In this section, you're going to make a small local edit to the random file you made earlier. Then you're
going to copy it over to the remote server and run it!

![Image](https://bhacia.github.io/cse15l-week2-labreport1/vscode-remote-running.png)

Extra **useful** notes:
- You can write a command in quotes at the end of an ssh command to directly run it on the remote server!
- You can use semicolons to run multiple commands on the same line in most terminals!
- You can use the up-arrow on your keyboard to recall the last command that was run!
