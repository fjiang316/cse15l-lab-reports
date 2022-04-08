# CSE 15L Lab Report 1 (Week 2 Remote Access)
## Introduction (About this Report)
In this lab report, the purpose is to demonstrate the step by step process in which one could gain remote access through the ieng6 server from one’s local computer using the terminal in visual studio code. The report will also contain steps for basic operation that can be done on the remote server, and ways to optimize the remote access and operating experience.

## Step 1 - Installing VS Code
In this step, we are going to set up the environment for accessing the remote server. For this purpose, we are going to download the Visual Studio Code, which is an easy platform that allows us to implement codes and manage the terminals. The VS Code can be downloaded from the following [link](https://code.visualstudio.com/). After it’s downloaded, according to the way you set it up, you should see something similar to this upon opening the application.

![screenshot](https://raw.githubusercontent.com/fjiang316/cse15l-lab-reports/6c5ce83e4049d177572934ffb74b2f07b14a537a/2022-04-01.png)

## Step 2 - Remote Connecting
For this step, we are going to gain remote access to the ieng6 server by clicking on the `terminal` - `new terminal`. To gain remote access, it is required to type in the following ssh command with account name and host server name in the terminal: `ssh cs15lsp22zz@ieng6.ucsd.edu`, where `zz` should be replace by your peronalized account suffix. After that, if there’s no key being generated, it will prompt the user to enter the password for the account, upon hitting enter, you should see something similar to the following image.