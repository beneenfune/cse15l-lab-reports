# How to log into a course-specific account on ieng6
//needs at least 6 screenshots

## 1. Installing VScode

![Image](https://code.visualstudio.com/assets/docs/languages/javascript/overview.png)

1. go to [Visual Studio Code](https://code.visualstudio.com/) and follow instructions to install the application based on which system you have, including OSX for Mac and Windows for PC

You now have VScode downloaded to your computer.


## 2. Remotely Connecting

1. look up your course-specific account for CSE15L [here](https://sdacs.ucsd.edu/~icc/index.php)
* if you're using **Windows**, you must install OpenSSH [here](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse)
2. under 'Additional Accounts', click the button that starts with "cs15l"
(Image)[fakjdfhaskfhjvjsadskljvav]
3. note your username-it should have the form **cs15lsp22zzz** where the zzz are personalized to your account.
your **user@hostname** is your *username*@ieng6.ucsd.edu : 
**cs15lsp22zzz@ieng6.ucsd.edu**
4. open VScode
5. open Terminal using either Ctrl+' or the Terminal -> New Terminal option
6. in the Terminal, enter "ssh **cs15lsp22zzz@ieng6.ucsd.edu**" from step 3
> * Answer yes to these messages by typing "yes" and pressing enter. When asked to enter password, enter the same password used to login into your course-specific account from step 1.
 
You now have your terminal connected to a computer in the CSE basement-a step necessary to run commands on that computer in the basement from your computer.


## 3. Trying Some Commands

1. in the Terminal, try these commands:
* "cd"
> * meaning 'change directory', used to change the current working directory.
* "cd ~"
> * ""^ but where ~ is the directory name
* "ls -lat"
> * used to view the contents of a directory
* "ls -a"
> * used to view the contents of a directory, including the hidden files
* "ls **directory**" 
> * **directory** is "/home/linux/ieng6/cs15lsp22/**username**"-the **username** is from step 3 of step *Remotely Connecting*
> * 
* "cp /home/linex/ieng6/cs15lsp22/public/hello.txt ~/"
> * used to copy files and directories
* "cat /home/linex/ieng6/cs15lsp22/public/hello.txt"
> * used to read the data from the file and prints the content of the file

You now have an idea of how to run commands from your computer.

## 4. Moving Files with 'scp'
   * note: this step is a demonstration using an example file

1. create a file called **WhereAmI.java* and paste the following into it:
> class WhereAmI {
     public static void main(String[] args) {
         System.out.println(System.getProperty("os.name"));
         System.out.println(System.getProperty("user.name"));
         System.out.println(System.getProperty("user.home"));
         System.out.println(System.getProperty("user.dir"));
    }
 }
2. run it using the following lines successively:
> javac WhereAmI.java
> java WhereAmI
> scp WhereAmI.java cs15lsp22zz@ieng6.ucsd.edu:~/
   * note: the password it asks for is the same one from step 6 of step *Remotely Connecting*


You now can copy files back and forth between computers: here, between the *client*-your computer-and the computer it's connected to in the CSE basement.

## 5. Setting an SSH Key

1. run the following command and do not add a passphrase:
> ssh-keygen
* if you're using **Windows**, follow the extra ssh-add steps [here](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement#user-key-generation)
2. with the two new files on your system-the private key and public key-now runthe followig command to copy the public key to the .ssh directory of your user account
> ssh **cs15lsp22zzz@ieng6.ucsd.edu**
   * remember to replace the zzz with your personal 3 characters

You now are able to use ssh or scp here without having to enter your password each time.

## 6. Optimizing Remote Running
the following is one way to more quickly make a local edit to your file, copying it to the remote server, and then running it

using the file **WhereAmI.java** as an example:
* the concept is you condense 118 total keystrokes of commands to 2 by using the up arrow keys

* 118: scp WhereAmI.java cs15lsp22acz@ieng6.ucsd.edu:~/; ssh cs15lsp22acz@ieng6.ucsd.edu "javac WhereAmI.java; java WhereAmI"
* however if the history is one where ^that is executed in 4 different lines of code, like:

* scp WhereAmI.java cs15lsp22zzz@ieng6.ucsd.edu:~/; ssh 
* cs15lsp22zzz@ieng6.ucsd.edu "javac WhereAmI.java; java WhereAmI"

* you can save and then for each one press the arrow key and enter-this reduces the number of key strokes to 2

You are now familar with how to remote run more efficently.