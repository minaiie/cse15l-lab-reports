# Lab Report 3 - Streamlining SSH Configuration
## Creating the SSH Config File
![Image](https://github.com/minaiie/cse15l-lab-reports/blob/main/Screen%20Shot%202022-02-11%20at%2010.17.50%20PM.png)

The `ssh` process of logging into ieng6 can be streamlined through the command `ssh ieng6`. I created a file named `config` in the `.ssh` directory and filled with the information above to login.

## SSH Login With New Alias
![Image](https://github.com/minaiie/Skill-Demo/blob/main/Screen%20Shot%202022-02-11%20at%2010.19.56%20PM.png)

After the `ssh ieng6` terminal command is setup, I can automatically logged in using a one liner. 

## SCP Command Using New Alias
![Image](https://github.com/minaiie/cse15l-lab-reports/blob/main/Screen%20Shot%202022-02-13%20at%204.48.23%20PM.png)

`ieng6` can now be used in replacement of `cs15lwi22abj@ieng6.ucsd.edu` for any command. Running `scp /Users/mingjieni/Desktop/cse15/markdown-parse/test-file.md  ieng6:~ ` will copy the file test-file.md to my ieng6 profile without typing out the long username.
