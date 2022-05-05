# Week 6: Lab Report 3

## Efficiency Improvement in Remote Server

Hi there!

This lab report will focus on improving our working efficiency by 1) Streamline ssh Configuration, 2) Set up Github Access from ieng6, and 3) Copy Whole Directories with scp -r to ieng6. In these ways, we'll be able to take advantage of this Linux-based remote server and improve our efficiency when working in both local and remote environments at the same time.

In this lab, we'll continue with the Markdown Parse program in which a java file reads a markdown file and detects the URL links in it. 

## Streamline ssh Configuration


## Set up Github Access from ieng6


[Link for the resulting commit](https://github.com/jypipi/markdown-parser/commit/d4ed78d6c33ad4670682da88c537b15ab3b0efeb)

## Copy Whole Directories with scp -r

```
# One-Line Command to copy the whole directory to remote server and then compile and run on it
$ scp -r *.java *.md lib/ cse15l:markdown-parse; \
  ssh cse15l \
  "cd markdown-parse; \
   /software/CSE/oracle-java-17/jdk-17.0.1/bin/javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java; \
   /software/CSE/oracle-java-17/jdk-17.0.1/bin/java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest \
  "
```
