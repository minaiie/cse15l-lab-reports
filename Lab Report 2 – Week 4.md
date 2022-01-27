# Installing VScode

Go to https://code.visualstudio.com/ to download and install VScode on my computer.
<img width="763" alt="Screen Shot 2022-01-14 at 5 07 00 PM" src="https://user-images.githubusercontent.com/92061511/149603871-6c0c25f6-7e1e-4e9f-9660-abef56a2577a.png">


# Remotely Connecting
## Find  course-specific account for CSE15L
at: https://sdacs.ucsd.edu/~icc/index.php

## Connect to the remote computer
1) open a terminal in VSCode (Ctrl or Command + `)
2) enter: `$ ssh cs15lwi22abj@ieng6.ucsd.edu `
3) I get the following message, enter `yes`
  ```
  ⤇ ssh cs15lwi22abj@ieng6.ucsd.edu
  The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.
  RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
  Are you sure you want to continue connecting (yes/no/[fingerprint])? 
  ```
4) then enter the password, I get connected!
<img width="763" alt="Screen Shot 2022-01-14 at 5 07 00 PM" src="https://user-images.githubusercontent.com/92061511/149603900-c72e6af3-85c0-478d-b1bb-5ac110522189.png">

# Trying Some Commands, for example `ls`
<img width="499" alt="Screen Shot 2022-01-14 at 5 07 47 PM" src="https://user-images.githubusercontent.com/92061511/149603905-aecf3f81-dcea-44ed-80a7-38f7d26dc0a0.png">

# Moving Files with scp
1) Create a file named WhereAmI.java with following contents:
```
class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}
```
2) In the terminal from the directory of this file, run this command:`scp WhereAmI.java cs15lwi22abj@ieng6.ucsd.edu:~/`
3) log into ieng6 with ssh and enter ls.
<img width="540" alt="Screen Shot 2022-01-14 at 5 08 05 PM" src="https://user-images.githubusercontent.com/92061511/149603916-d4340994-9bdc-47c6-bb1d-58430745c296.png">

# Optimizing Remote Running-set up SSH keys
1) Build the key on client:
```
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/joe/.ssh/id_rsa): /Users/joe/.ssh/id_rsa
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /Users/joe/.ssh/id_rsa.
Your public key has been saved in /Users/joe/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:jZaZH6fI8E2I1D35hnvGeBePQ4ELOf2Ge+G0XknoXp0 joe@Joes-Mac-mini.local
The key's randomart image is:
+---[RSA 3072]----+
|                 |
|       . . + .   |
|      . . B o .  |
|     . . B * +.. |
|      o S = *.B. |
|       = = O.*.*+|
|        + * *.BE+|
|           +.+.o |
|             ..  |
+----[SHA256]-----+
```
2) copy the public key to the .ssh directory of your user account on the server.
```
$ ssh cs15lwi22zz@ieng6.ucsd.edu
<Enter Password>
# now on server
$ mkdir .ssh
$ <logout>
# back on client
$ scp /Users/joe/.ssh/id_rsa.pub cs15lwi22@ieng6.ucsd.edu:~/.ssh/authorized_keys
```

# Optimizing Remote Running
<img width="540" alt="Screen Shot 2022-01-14 at 5 47 23 PM" src="https://user-images.githubusercontent.com/92061511/149604324-9b369b9d-9bc6-4416-80fb-1b4b5b4ff8b8.png">
There are sveral ways to make our programming faster. One way would be to add a command after an ssh command to run it directly on the remote server. Semicolons also allow for multiple commands to run on one line. For example:

```
$ ssh cs15lwi22@ieng6.ucsd.edu "ls"; cp WhereAmI.java; javac WhereAmI.java; java WhereAmI
```
![Image](https://github.com/minaiie/cse15l-lab-reports/blob/main/Screen%20Shot%202022-01-26%20at%207.57.59%20PM.png)

