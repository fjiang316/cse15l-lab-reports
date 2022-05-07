# CSE 15L Lab Report 3 (Week 6 Git on Remote Server)
## Introduction
The purpose of the lab report is to demostrate ways to build easier connections between github and the remote server. This includes to connect to ieng6 remote server more easily from the local computer, being able to push changes to github directly from the terminal, and to securely copy directories to remote server.

## Streamlining `ssh` Configuration
### My .ssh/config File
![config_file](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport3%20part1%20file.png?raw=true)
### Logging in with Alias `ieng6`
![login](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport3%20part1%20ssh.png?raw=true)
### Copying one File with `scp` and Alias `ieng6`
![copying](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport%203%20part%201%20scp.png?raw=true)

## Setup Github Access from ieng6 Server
### Public Key Stored in Github User Account
![public key](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport3%20part2%20key%20update.png?raw=true)
### Private Key Stored in Remote User Account
![private key](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport3%20part2%20private%20user%20account.png?raw=true)
### Commit and Push Changes from ieng6 Server to Github Using Git Commands
![push origin](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport3%20part2%20push.png?raw=true)
### The Resulting Commit on Github Webpage
> Link to the commit: [click here](https://github.com/fjiang316/markdown-parser-fork/commit/b2d072d55c353d767aed03bd11cf2edbd5fbae9c)

It displays as following:
![disply commit](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport3%20part2%20commit.png?raw=true)

## Copy Whole Directories with `scp -r`
### Copying Whole markdown-parse Directory to ieng6 server
The full command line used to copy the directory is `PS C:\Users\fiona\Documents\GitHub\markdown-parser-fork> scp -r *.java *.md lib cs15lsp22acs@ieng6.ucsd.edu:~/markdown-parser`.
The result in the remote server is shown as in the following screenshot:
![copy](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport3%20part3%20copy%20updataed.png?raw=true)

### Compile and Run Junit Test While Inside Remote Server
![compile](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport3%20part3%20run%20test.png?raw=true)

### Combine `scp` and `ssh` and Running the Tests in Remote ieng6 Server All in One step
![run and copy](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport3%20part3%20run%20and%20copy.png?raw=true)