# Lab Report 4: CSE Labs Done Quick
## 1. Log into ieng6
![ssh](https://cdn.discordapp.com/attachments/639543567521415171/1078163662134575134/image.png)

Keys pressed:

`ssh cs15lwi23asr@ieng6.ucsd.edu<enter>`

This command ssh'd into my ieng6 machine.
No shortcuts here. However, I didn't need to type my password because I 
configured my ssh key before the competition.

## 2. Clone your fork of the repository from your Github account
![clone](https://cdn.discordapp.com/attachments/639543567521415171/1078178961898606592/image.png)

Keys pressed: 

`git clone git@github.com:panda2k/lab7.git<enter>`

This command cloned my Github repository. 
Once again, no shortcuts here. However, I did make sure to clone with the ssh
url so I could `git push` with my Github ssh key.

## 3. Run the tests, demonstrating that they fail
![tests](https://cdn.discordapp.com/attachments/639543567521415171/1078172918766383146/image.png)

Keys pressed: 
1. `cd l<tab><enter>`

This command enters the lab7 repository. Since `lab7` is the only file/folder
that starts with `l`, `<tab>` autocompletes to `lab7/`

2. `ls l<tab>h<tab>:l<tab>j<tab> *.java <ctrl><a><ctrl><d><ctrl><d><ctrl><d> javac -cp .:<enter>`

This command compiles all the java files in the working directory (`lab7/`).
I first start with `ls` because using `javac` as the first command won't
allow for autocompletion to files. It will only allow me to autocomplete to `lib/`.

So, first `l<tab>` autocompletes to `lib/` since `lib` is the only file / folder
that starts with `l`. Then, `h<tab>` autocompletes to `hamcrest-core-1.3.jar`. 

Next, I type the `:` that needs to be between the hamcrest and junit jars.
Then, `l<tab>` once again autocompletes to `lib/` and `j<tab>` autocompletes to
`junit-4.13.2.jar`. Then, I type `*.java` to complete the command.

However, I still prefixed the command with `ls`, and I need to change it to
`javac`. To do this, I use `Ctrl-A` to move to the start of the line, then two
`Ctrl-D` to delete the `ls`. Then I finish writing the start of the command.

3. `<up> <delete><delete><delete><delete><delete><delete> org.junit.runner.JUnitCore 
T<tab> <delete>
<ctrl><a><right><right><right><right><ctrl><d><enter>`

This set of key strokes runs the JUnit tests. Since I already had the long class
path written out in my previous command, `<up>` fetches it from history. 
Then I trimmed the `*.java` from the end and typed out the rest of the command. 
`T<tab>` autocompletes to `TestListExamples.`, so I then trimmed the `.` from the end.

Now I need to change `javac` to `java`, so I use `Ctrl-A` to get to the start of the line,
navigate the cursor to `c`, delete it, and hit `<enter>` to run the tests.

## 4. Edit the code file to fix the failing test
![vim](https://cdn.discordapp.com/attachments/639543567521415171/1078176152952258670/image.png)

Keys pressed:

`vim L<tab><enter> 42j f1 r2 :wq`

This set of key strokes uses `vim` to edit the file and fix the bug.
`L<tab>` autocompletes to `ListExamples.java` and `<enter>` runs the command
to open the file in `vim`.

The bug is on line 42, so `42j` jumps to line 42, `f1` jumps the cursor to the `1` 
, and `r2` replaces the `1` with `2`. `:wq` then writes and closes the file.

## 5. Run the tests, demonstrating that they now succeed
![run tests again](https://cdn.discordapp.com/attachments/639543567521415171/1078176850209148958/image.png)

Keys pressed:
1. `<up><up><up><enter>`

The `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` command was
three up in history, so I used `<up>` to access it and `<enter>` to run it.

2. `<up><up><up><enter>`

The `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples`
command was three up in history, so I used `<up>` to access it and `<enter>` to run it.

## 6. Commit and push the resulting change to your Github account
![git](https://cdn.discordapp.com/attachments/639543567521415171/1078179335367839844/image.png)

Key pressed:
1. `git add . <enter>`

This stages all changed / new files in the current directory.

2. `git commit -m 'f' <enter>`

This commits all the staged files with the commit message `f`. For the sake of speed,
the totally non-descript commit message of `f` is used.

3. `git push <enter>`

This pushes the changes to my Github repository. It doesn't prompt me for 
authentication because I've used the Github ssh key.

