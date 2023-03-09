# Lab Report 5: CSE Labs Done Quick with a Bash Script
Although using a bash script was against the rules, the task could've 
been done very quickly if I used a bash script. In this report, I'll be 
writing a bash script to replicate the actions done in lab report 4.

## Script Overview
All the commands need to be run on the `ieng6` server. To run the commands
remotely, the script needs to be set up like this: 
```
ssh cs15lwi23asr@ieng6.ucsd.edu "
    echo 'commands here'
    echo 'more commands here'
"
```
The script first ssh's into the remote server, then runs the commands inside
the quotes. Since the script only needs to do a pre-defined set of commands,
the commands will all be hard coded. 

## Cloning and Entering the Repository
To clone the repository, I can just copy paste the `git clone` command into 
the script. 
`git clone git@github.com:panda2k/lab7.git`

Next, to enter the folder, I'll use `cd lab7`.

## Compile and Run the Tests
Now that the script has navigated inside the `lab7` folder, I'll run the following
two commands to compile and run the tests. The tests will fail 
since there is still a bug in the code.
```
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests 
```

## Editing the File to Fix the Bug
Editing the file is a bit tricky, since I can't manually use `vim`
to navigate to the appropriate line and replace `index1` with `index2`.

However, I can use `vim` to run a find and replace command on line 43 (the
line with the bug). 

`vim ListExamples.java -c` will start vim, open `ListExamples.java`, 
and run a specified command.
I'll be able to use this to automatically run a find and replace command.

`:43s/index1/index2/` is the find and replace command I'll use. `:43s` is
the command to run a find and replace on line 43. `/index1` tells
the command to look for the string `index1`. `/index2` then tells the command
to replace matched strings with `index2`. The final `/` ends the command.

`vim` has now opened the file and fixed the bug, so now the file just needs
to be saved. `-c wq` will write the file and quit vim.

Now putting it all together, the command we'll run to edit the file and fix the 
bug is: `vim ListExamples.java -c :43s/index1/index2/ -c wq`.

## Compile and Run the Tests Again
To compile and run the tests again, I'll just copy the commands from earlier.
The tests will pass now that the bug is fixed.
```
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests 
```

## Staging, Committing, and Pushing to GitHub
Now that the bug is fixed and the tests pass, the script just
needs to stage, commit, and push the changes to GitHub. 

`git add .` stages all the files

`git commit -m 'f'` will commit all staged files with the commit message `f`.

`git push` will then push the new commit to GitHub. 

Putting it all together, the three commands we'll run are: 
```
git add .
git commit -m 'f'
git push
```

## Completed Script
Now that I've replicated all the required steps, here is the completed script
```
ssh cs15lwi23asr@ieng6.ucsd.edu "
    git clone git@github.com:panda2k/lab7.git
    cd lab7
    javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
    java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests 
    vim ListExamples.java -c :43s/index1/index2/ -c wq
    javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
    java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests 
    git add .
    git commit -m 'f'
    git push
"
```
## Running the Script
I can now run the completed script with `bash labs-quick.sh`.
Below is the output of running the script. There are a few warnings,
but the script successfully completes the "CSE Labs Done Quick" tasks.

![out 1](https://cdn.discordapp.com/attachments/639543567521415171/1083492297381007531/image.png)
![out 2](https://cdn.discordapp.com/attachments/639543567521415171/1083492372647772281/image.png)


