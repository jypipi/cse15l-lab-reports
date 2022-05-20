# Week 8: Lab Report 4

## Continued Testing and Debugging of Markdown Parse

Hi there!

In this lab report, we'll continue to deal with the Markdown Parse program in 
which a java file reads a markdown file (.md) and detects the URL links in it.

This time, we are given three additional snippets to test our program and the
one we reviewed at week 7. By looking at the current implementations and the
test results, we'll be able to determine whether these programs can be improved
via small code changes (less than 10 lines for each snippet) and explain the
reasons.

Let's go!

## Clone Repositories

```
# Link to My Repo
$ https://github.com/jypipi/markdown-parser.git

# Link to Reviewed Repo
$ https://github.com/brandoluu/markdown-parser.git

# Clone My Repo
$ git clone git@github.com:jypipi/markdown-parser.git

# Clone Reviewed Repo
$ git clone git@github.com:brandoluu/markdown-parser.git
```

## Snippet 1

* Snippet 1 Content

```
`[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
```

![Image](Images\Lab-Report-4\1.png)

* Expected Output

```
[url.com, google.com]
```

* Test Code in MarkdownParseTest.java

```

```

* Actual Outputs

```

```

* Discussion

#[Discussion here]


## Snippet 2

* Snippet 2 Content

```
[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)
```

![Image](Images\Lab-Report-4\2.png)

* Expected Output

```
[a.com, b.com, a.com, example.com]
```

* Test Code in MarkdownParseTest.java

```

```

* Actual Outputs

```

```

* Discussion

#[Discussion here]


## Snippet 3

* Snippet 3 Content

```
[this title text is really long and takes up more than
one line

and has some line breaks](
    https://www.twitter.com
)

[this title text is really long and takes up more than
one line](
https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedu
le
)


[this link doesn't have a closing parenthesis](github.com

And there's still some more text after that.

[this link doesn't have a closing parenthesis for a
while](https://cse.ucsd.edu/



)

And then there's more text
```

![Image](Images\Lab-Report-4\3.png)

* Expected Output

```
[https://www.twitter.com, https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule, github.com, https://cse.ucsd.edu/]
```

* Test Code in MarkdownParseTest.java

```

```

* Actual Outputs

```

```

* Discussion

#[Discussion here]


# Conclusion

Today, we covered a main theme that testing and debugging our Markdown Parse 
program via JUnit tests and code snippets that provide multiple situations:

1) Inline Code with Backticks

2) Nested Parentheses, Brackets, and Escaped Brackets

3) Newlines Existing in Brackets and Parentheses

Perfection can hardly be reached in one time. When practicing continuous integration, we will be able to keep improving our programs to make it suit increasing situations by testing and debugging. Therefore, as our codes "grow up", so do our programming
skills!

See you next time!

> [Return to Main Page](https://jypipi.github.io/cse15l-lab-reports/index.html)