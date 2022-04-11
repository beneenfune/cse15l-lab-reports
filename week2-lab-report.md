# How to log into a course-specific account on ieng6
//needs at least 6 screenshots

## 1. Installing VScode

1. go to [Visual Studio Code](https://code.visualstudio.com/) and follow instructions to install the application based on which system you have, including OSX for Mac and Windows for PC

you now have VScode downloaded to your computer


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
 
you now have your terminal connected to a computer in the CSE basement-a step necessary to run commands on that computer in the basement from your computer


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

you now have an idea of how to run commands from your computer

## 4. Moving Files with 'scp'
   * note: this step is a demonstration using an example file

1. create a file called **WhereAmI.java* and paste the following into it:
> class WhereAmI {
  >public static void main(String[] args) {
    >System.out.println(System.getProperty("os.name"));
    >System.out.println(System.getProperty("user.name"));
    >System.out.println(System.getProperty("user.home"));
    >System.out.println(System.getProperty("user.dir"));
  >}
>}
2. run it using the following lines successively:
> javac WhereAmI.java
> java WhereAmI
> scp WhereAmI.java cs15lsp22zz@ieng6.ucsd.edu:~/
   * note: the password it asks for is the same one from step 6 of step *Remotely Connecting*


you now can copy files back and forth between computers: here, between the *client*--your computer--and the computer it's connected to in the CSE basement

## 5. Setting an SSH Key
## 6. Optimizing Remote Running