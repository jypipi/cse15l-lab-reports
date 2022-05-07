# Week 6: Lab Report 3

## Efficiency Improvement in Remote Server (ieng6)

Hi there!

This lab report will focus on improving our working efficiency by 1) streamlining ssh Configuration, 2) setting up Github access from ieng6, and 3) copying whole directories with scp -r to this remote server. In these ways, we'll be able to take advantage of the Linux-based remote system and lift our efficiency when working on both local and remote environments at the same time.

In this lab, we'll continue with the Markdown Parse program in which a java file reads a markdown file and detects the URL links in it. 

## Streamline ssh Configuration

Although we've already simplified the procedures for ssh into our ieng6 accounts without entering password, typing the user and host names before login is still time-consuming, which also means we have to always remember those figures correctly.

Why not attempting to be "lazy"? In other words, we can **create a config file** to help us "remember" them.

First, open a terminal (in my case, I used Git bash):

```
# Go to the directory /.ssh
cd ~/.ssh

# Create the file
$ touch config

# Open this file
$ nano config
```

![Image](Images//Lab-Report-3/1-1.png)

In the config file, add the following content:

```
Host <customized alias>
    HostName ieng6.ucsd.edu
    User cs15lsp22xxx
```

![Image](Images//Lab-Report-3/1-2.png)

Then, save and exit the file. That's it!

Let's try:

```
# In general
ssh <customized alias>

# In my case, my alias is "cse15l"
ssh cse15l
```

![Image](Images//Lab-Report-3/1-3.png)





s
## Set up Github Access from ieng6


[Link for the resulting commit](https://github.com/jypipi/markdown-parser/commit/d4ed78d6c33ad4670682da88c537b15ab3b0efeb)

## Copy Whole Directories with scp -r

```
# Copy necessary files, compile and run a test via one command

$ scp -r *.java *.md lib/ cse15l:markdown-parse; ssh cse15l \
  "cd markdown-parse; \
   /software/CSE/oracle-java-17/jdk-17.0.1/bin/javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java; \
   /software/CSE/oracle-java-17/jdk-17.0.1/bin/java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest \
  "
```
