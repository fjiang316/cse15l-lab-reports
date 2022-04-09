# CSE 15L Lab Report 1 (Week 2 Remote Access)
## Introduction (About this Report)
In this lab report, the purpose is to demonstrate the step by step process in which one could gain remote access through the ieng6 server from one’s local computer using the terminal in visual studio code. The report will also contain steps for basic operation that can be done on the remote server, and ways to optimize the remote access and operating experience.

## Step 1 - Installing VS Code
In this step, we are going to set up the environment for accessing the remote server. For this purpose, we are going to download the Visual Studio Code, which is an easy platform that allows us to implement codes and manage the terminals. The VS Code can be downloaded from the following [link](https://code.visualstudio.com/). After it’s downloaded, according to the way you set it up, you should see something similar to this upon opening the application.

![screenshot](https://raw.githubusercontent.com/fjiang316/cse15l-lab-reports/6c5ce83e4049d177572934ffb74b2f07b14a537a/2022-04-01.png)

## Step 2 - Remote Connecting
For this step, we are going to gain remote access to the ieng6 server by clicking on the `terminal` - `new terminal`. To gain remote access, it is required to type in the following ssh command with account name and host server name in the terminal: `ssh cs15lsp22zz@ieng6.ucsd.edu`, where `zz` should be replace by your peronalized account suffix. After that, if there’s no key being generated, it will prompt the user to enter the password for the account, upon hitting enter, you should see something similar to the following image.

![image 2](https://github.com/fjiang316/cse15l-lab-reports/blob/main/2022-04-01%20(1).png?raw=true)

## Step 3 - Trying Some Commands
Now that we are logged in to the remote server, we can make operations on the remote computer with commands through the terminal. Some basic commands are: `ls` for showing the visible files in the current directory, `ls -a` for showing both visible and hidden files, `ls -lat` for showing all files with date, size, type, etc., `cd` for changing directory, `pwd` for showing the current directory, `cat` for showing the content of a file, and `cp` for making a copy of a file. The following are some examples for executing some of those commands, for your reference.

![image3](https://github.com/fjiang316/cse15l-lab-reports/blob/main/2022-04-01%20(2).png?raw=true)

## Step 4 - Moving Files With `scp`
To securely make a copy of a file from your local computer to the remote computer, we use the `scp` command on your local computer’s terminal, which stands for “secure copy”. The way it should be typed in a terminal is `scp <your_file_name> cs15lsp22zz@ieng6.ucsd.edu:~/` where the file name can be of any file and the zz should be replaced with your personal account suffix. After that, if no keys have been generated, the user will be prompted to type in the passwords, and upon hitting enter, the file will be copied into the remote computer’s home directory. The process is shown below with an example file.

![image4](https://github.com/fjiang316/cse15l-lab-reports/blob/main/2022-04-01%20(5).png?raw=true)

## Step 5 - Setting an SSH Key
In this step, we are going to set up an SSH key and store the public key in the server and the private key in the local computer, so that afterwards whenever we want to access the remote computer, we will not be prompted to enter passwords again. On the local computer’s terminal, the process is as following: 
* Enter `ssh -keygen`, the computer will reply 
```
Generating public/private rsa key pair. Enter file in which to save the key (/Users/<user-name>/.ssh/id_rsa):
```
* Then enter in format `/Users/<user-name>/.ssh/id_rsa`
* After that, hit enter when prompted 
```
Enter passphrase (empty for no passphrase): 
Enter same passphrase again:
```
* The computer will show the following:
```
Your identification has been saved in /Users/<user-name>/.ssh/id_rsa.
Your public key has been saved in /Users/<user-name>/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:jZaZH6fI8E2I1D35hnvGeBePQ4ELOf2Ge+G0XknoXp0 <user-name>@<system>.local
The key's randomart image is:
+---[RSA 3072]----+
|                 |
|       . . + .   |
|      . . B o .  |
|     . . B * +.. |
|      o S = *.B. |
|       = = O.*.*+|
```

 
