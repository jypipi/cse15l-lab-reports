# Week 10: Lab Report 5

## Continued Testing of Markdown Parse with `vimdiff`

Hi there!

Welcome to the last report of CSE15L! In this lab, we'll continue to deal with the Markdown Parse program in which a java file reads a markdown file (.md) and detects the URL links in it.

This time, we will compare the outputs of my implementation with those of a provided one, based on a large input containing 652 test files. By looking at two of these tests that have different outputs, we continue to point out the bugs existing in either/both of these implementations of markdown parsers.

Let's go!

## Preparation

To run the tests and compare the results efficiently, I saved the outputs of the two implementations in two files and then employed a powerful tool `vimdiff` to highlight the differences line by line.

```
# A Simplified Procedure

# Run tests and save my implementation's output
$ bash script.sh > resultsForReport5MyParse.txt

# Run tests and save the provided implementation's output
$ bash script.sh > resultsForReport5Provided.txt

# Run vimdiff to see differences
$ vimdiff resultsForReport5MyParse.txt resultsForReport5Provided.txt
```

For example, if two outputs are different from each other, the content would be shown like this:

![Image](Images\Lab-Report-5\example.png)


## Test 1

* Test file: *201.md*

```
# Link to the test file
$ https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/201.md
```
```
# Test file content:
[foo]: <bar>(baz)

[foo]

```

* Expected Output

![Image](Images\Lab-Report-5\expected201.png)

```
# Expected List
[]
```

* Actual Outputs

![Image](Images\Lab-Report-5\test201.png)

```
# My Output
[]

# Provided Output
[baz]
```

* Discussion

1. In this case, **my implementation** is correct.

2. Bug in the provided implementation: this program doesn't check the content between brackets [] and parentheses (). After it confirms the existence of parentheses, it creates a string called potentialLink to store the content within the parentheses and only checks this string without considering the content between the closed bracket and the open parenthesis. Therefore, in this case, when "<>" exists between them, the content within () should not be considered a valid link while the provided program still adds it to the returned list.

3. Code that should be fixed and possible changes:

![Image](Images\Lab-Report-5\test201CodeNeededFixed.png)

One of the possible changes is that, between line 73 and 74, it can create a string to store the content between closed bracket and open parenthesis and then add an if statement to check its content. If "<>" exists, skip this pair of (), update currentIndex, and move on to another loop.


## Test 2

* Test file: *376.md*

```
# Link to the test file
$ https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/376.md
```
```
# Test file content:
_(bar)_.

```

* Expected Output

![Image](Images\Lab-Report-5\expected376.png)

```
# Expected List
[]
```

* Actual Outputs

![Image](Images\Lab-Report-5\test376.png)

```
# My Output
[bar]

# Provided Output
[]
```

* Discussion

1. In this case, **the provided implementation** is correct.

2. Bug in my implementation: to handle the inputs provided in the previous weeks, I added an if-else if-else statement in my program to distinguish the following situations: a link exists while: 1) only [] or () exists; 2) neither of them exists in a markdown file. However, one of its disadvantages is that, as long as () exists, the program considers the content within the () a valid link even though it's not.

3. Code that should be fixed and possible changes:

![Image](Images\Lab-Report-5\test376CodeNeededFixed.png)

One of the possible changes is that, between line 39 and 44, a code block can be added to check if the content should be considered a valid link based on different situations and the standard of CommonMark.


# Conclusion

In this report, we covered a main theme that testing and debugging via the comparison between different Markdown Parse programs.

Taking advantage of `vimdiff`, we can easily perform the comparison  in a few seconds and detect the potential bugs by looking at the different outputs. In this way, we will be able to keep improving our programs to make it suit more situations by testing, debugging and continuous integration. As our codes "grow up", so do our programming skills!

This is the last lab report of CSE15L, goodbye and see you in the future!

> [Return to Main Page](https://jypipi.github.io/cse15l-lab-reports/index.html)