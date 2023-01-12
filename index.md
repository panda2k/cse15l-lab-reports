# Lab Report 1
Hello! In this lab report, I'll be documenting my experience installing VScode 
and ssh'ing into my `ieng6` account.
## Installing VScode
To start, download VScode from [here](https://code.visualstudio.com/download). 
Once it is finished downloading, move it to the `Applications` folder. 

Once it is finished copying, open it and you should see this screen: 
![VScode Open](https://cdn.discordapp.com/attachments/639543567521415171/1063195821258051664/image.png)

## Remotely Connecting
To remotely connect to my `ieng6` account, I first needed to reset my password. 
I didn't know my username so I went [here](https://sdacs.ucsd.edu/~icc/index.php)
used the `Forgot Username or New Student?` form. From there,
I copied my `ieng6` username account (the username that isn't in your email).

Next, I reset the password [here](https://sdacs.ucsd.edu/~icc/password.php).
After resetting the password, I tried to SSH with `ssh cs15lwi23zz@ieng6.ucsd.edu`
(replace `zz` with your account's personal letters) but it kept saying my password was
wrong and this was because the password change takes up to 15 minutes to take
effect.


After waiting 15 minutes, I was able to connect and see this screen: 
![Successful ssh screen](https://cdn.discordapp.com/attachments/639543567521415171/1063197954342654135/image.png)


## Trying Some Commands
Now that I was able to ssh, I tried some commands. 

Trying `ls` lists the files in the current directory and
it revealed a file named `perl5`.
![ls command](https://cdn.discordapp.com/attachments/639543567521415171/1063198876741414942/image.png)



However, `ls` doesn't reveal all files in the directory so I then tried 
`ls -al` which revealed every file. As you can see from the screenshot, there
are a lot of files prepended with `.`.
![ls -al](https://cdn.discordapp.com/attachments/639543567521415171/1063199546173300836/image.png)


The last command I tried was `cat /home/linux/ieng6/cs15lwi23/public/hello.txt`
which printed the output of the `hello.txt` file to the command line.
![cat](https://cdn.discordapp.com/attachments/639543567521415171/1063200184839966750/image.png)

## Conclusion
Thank you for reading my lab report! I hope it can help guide you through the process
of setting up your CSE15L development environment!

