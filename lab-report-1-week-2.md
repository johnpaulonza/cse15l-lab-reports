# **Getting Started in CSE15L**
## Overview
---
Hello student! This is a guide on how to prepare your computer for this course. You will be installing VScode, logging in with your unique ieng6 id for remote access, and practicing transferring files. The following is the list of instructions you will be going through. You got this!
- Installing VScode
- Remotely Connecting
- Trying Some Commands
- Moving Files with scp
- Setting an SSH Key
- Optimizing Remote Running 

<br>

--- 
## **Installing VScode**
---

<br>

### __1.__  Go to [code.visualstudio.com](code.visualstudio.com) and follow the instructions to download and install VScode to your system
![vscode-download](Screenshot_1.png)

### __2.__ This is what it should somewhat look like once you launch it(color & layout will differ depending on how you set it up):
![vscode-screenshot](Screenshot_2.png)

<br>
<br>

---
## **Remotely Connecting**
---
<br>

### __1.__ Before moving on, you must install OpenSSH in order to connect to the remote computer to do your work on there. Follow the instructions to install OpenSSH through this [microsoft link](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse) depending on your operating system.

### __2.__ Next, you need to find your course-specific account through the [account lookup on UCSD](https://sdacs.ucsd.edu/~icc/index.php)
* Input your student **username**(the portion before your @ucsd.edu email) and your Student ID and press submit
* This is what you should see when you press submit, look for the circled area, that is your __*ieng6*__ username
![account-lookup](Screenshot_3.png)

     ***Keep in mind it is a lowercase 'L' after the 15, and you might have different letters and numbers following that 'L'.** (sp22 for spring 22, and you will have your own unique combination at the end
 
 ### __3.__ You are now ready to connect to the remote server
*(I will be referencing [this](https://code.visualstudio.com/docs/remote/ssh#_connect-to-a-remote-host) for these next few steps)*
 
 * On VScode, you can open the terminal by pressing *Ctrl + `* or from the top bar *Terminal ??? New Terminal*
 ![terminal](Screenshot_4.png)
 * Once the terminal is open, you can begin by typing:

        ssh cs15lsp22zzz@ieng6.ucsd.edu
    *Remember to replace the 'sp22zzz' with your specific account(see previous step)*
* You will probably see this for your first time connecting:

        ssh cs15lsp22zz@ieng6.ucsd.edu
        The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.
        RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
        Are you sure you want to continue connecting (yes/no/[fingerprint])?
* Just type yes and continue along, then enter your password, it should look like this once you're in:

![ssh-login](Screenshot_5.png)

<br>

You are now logged in and connected to the remote server, **Congrats!** Any commands you run from this terminal will run on the computer you're connected to.

<br>
<br>

---
## **Trying Some Commands**
---

<br>

Now that you're connected, you can start testing commands. Some you can try are:

    cd ~
    cd
    ls -a
    ls -lat
    cp /home/linux/ieng6/cs15lsp22/public/test.txt ~/
    cat /home/linux/ieng6/cs15lsp22/public/test.txt

This is what running some commands looks like:
![commands](Screenshot_6.png)

You can also open a new terminal and test some of these commands on your local computer  to see the difference.

If you wanted to logout of the server you can always press ***Ctrl + D*** or run the command ***exit*** in the ssh terminal

<br>
<br>

---
## **Moving files over with scp**
---

<br>

Now we're going to learn how to move files remotely from the terminal. As coders, moving files between computers is important and being able to do work remotely helps a lot. You might be familiar with transferring files through e-mail, Google Drive, or Dropbox, then accessing those on the receiving end to download the files.

You won't need to do any of those with what I am about to teach you in the following steps. We will be utilizing the *scp* command from your client(local computer) in order to transfer files to the remote server.

1. Create a new file MyInfo.java and write this sample code:

        class MyInfo {
            public static void main(String[] args) {
            System.out.println(System.getProperty("os.name"));
            System.out.println(System.getProperty("user.name"));
            System.out.println(System.getProperty("user.home"));
            System.out.println(System.getProperty("user.dir"));
            }
        }
     (If you have java installed on your computer, try to run *javac* then *java* and see what it does)

2. Once you've created the file, run this command from your client terminal(**not** the logged in ssh one):

        scp MyInfo.java cs15lsp22zzz@ieng6.ucsd.edu:~/
    *Don't forget to replace the 'sp22zzz' with your unique account name :)*

    * You'll be prompted to put your password; type it out press *Enter*:
    ![scp-command](Screenshot_7.png)

    * Now in the ssh terminal, run the *ls* command and you should see MyInfo.java show up:
    ![ls-after-scp](Screenshot_8.png)
    * Next, run these two commands in the same terminal:
            
            javac MyInfo.java
            java MyInfo
        This is my output, yours should look very similar:
        ![ssh-output](Screenshot_9.png)

<br>
<br>

---
## **Setting an SSH key**
---

<br>

You now have the basics of file transfer. But wasn't it annoying having to type out/copy&paste your long password in a bunch of steps throughout? 

Do not worry, there is a solution! ssh keys. A program called ssh-keygen creates a *public key* and a *private key*. The idea is that the public key can be copied to a particular location in the remote server, while the private key is stored somewhere in the client. The *ssh* command is able to read both files and connect you without having to input your password.

* On the **client** terminal, run the following commands

    For **Windows**, you need to run this line first:

        ssh-keygen -t ed25519
    
    For everyone else, run this command(*For windows, this is the next command you run*)

        ssh-keygen
        
    ### **DO NOT ENTER A PASSPHRASE! I also used the default save path(see screenshot below)**

    <br>

    ![ssh-keygen](Screenshot_10.png)

    You now have two new files, ***id_rsa***(private key) and ***id_rsa.pub***(public key).

    <br>
    
* The next step is to copy the public key into the remote server. To do this, first log into your remote server:

        ssh cs15lsp22zz@ieng6.ucsd.edu
    
    *Don't forget to replace the 'sp22zzz' with your unique account name :)*

* Run the command:

        mkdir.ssh

* Now, go back to your client terminal(***not*** the ssh logged in one) and run this command, replacing necessary info to match yours:

        scp /Users/<user-name>/.ssh/id_rsa.pub cs15lsp22zzz@ieng6.ucsd.edu:~/.ssh/authorized_keys

    *You can find the path from when you generated the keygen and also replace the 'sp22zzz' in the ieng6 :)*

Try to log back into your ssh, you should automatically be logged in as soon as you press Enter. If not, don't be afraid to ask a neighbor or a TA!

<br>
<br>

Congrats! you have fully setup your local computer to be able to work remotely. With more practice, you will work even faster!

---
## **Optimizing Remote Running**  
---

<br>

All that's left is to try and improve what we've setup so far! 

I will list some of the many things you could do to make your work flow even more efficient:

* Writing a command in quotes at the end of the ssh command allows you to log in remotely, run the command, then immediately exit

        ssh cs15lsp22zzz@ieng6.ucsd.edu "ls -lat"

* Adding semicolons allows you to run multiple lines of commands

        cp MyInfo.java MyInfoCopy.java; javac MyInfoCopy.java; java MyInfoCopy

* The up arrow allows you to recall the last command you ran

* Type a few letters of a file or directory and press Tab. The terminal will try to autocomplete the rest of whatever you're looking for


There are obviously many more shortcuts and tips that I have yet to learn, so try to find new ones on your own and share them with others :D
