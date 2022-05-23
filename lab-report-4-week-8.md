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

(Based on the report writeup downloaded on 05/19/2022)

```
`[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
```

* Expected Output

![Image](Images\Lab-Report-4\1.png)

```
[google.com, google.com, ucsd.edu]
```

* Test Code in MarkdownParseTest.java

```
// For my implementation
@Test
    public void checkSnippet1() throws IOException {
        Path file = Path.of("LabReport4-Snippet-1.md");
        String content = Files.readString(file);
        ArrayList<String> links = MarkdownParse.getLinks(content);
        ArrayList<String> result = new ArrayList<String>(
            Arrays.asList("google.com", "google.com", "ucsd.edu"));

        assertEquals(true, links.equals(result));
    }

// For reviewed repo's implementation
    @Test
    public void checkReviewedSnippet1() throws IOException {
        Path file = Path.of("LabReport4-Snippet-1.md");
        String content = Files.readString(file);

        // Call getLinks() of the reviewed repo's MarkdownParse file
        ArrayList<String> links = reviewedMarkdownParse.getLinks(content);
        ArrayList<String> result = new ArrayList<String>(
            Arrays.asList("google.com", "google.com", "ucsd.edu"));

        assertEquals(true, links.equals(result));
    }
```

* Actual Outputs

1) For my implementation

![Image](Images\Lab-Report-4\output1.png)

2) For the reviewed repo's implementation

![Image](Images\Lab-Report-4\reviewed1.png)

* Discussion

#[Discussion here]


## Snippet 2

* Snippet 2 Content

(Based on the report writeup downloaded on 05/19/2022)

```
[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)
```

* Expected Output

![Image](Images\Lab-Report-4\2.png)

```
[a.com, a.com, example.com]
```

* Test Code in MarkdownParseTest.java

```
// For my implementation
@Test
    public void checkSnippet2() throws IOException {
        Path file = Path.of("LabReport4-Snippet-2.md");
        String content = Files.readString(file);
        ArrayList<String> links = MarkdownParse.getLinks(content);
        ArrayList<String> result = new ArrayList<String>(
            Arrays.asList("a.com", "a.com", "example.com"));

        assertEquals(true, links.equals(result));
    }

// For reviewed repo's implementation
@Test
    public void checkReviewedSnippet2() throws IOException {
        Path file = Path.of("LabReport4-Snippet-2.md");
        String content = Files.readString(file);

        // Call getLinks() of the reviewed repo's MarkdownParse file
        ArrayList<String> links = reviewedMarkdownParse.getLinks(content);
        ArrayList<String> result = new ArrayList<String>(
            Arrays.asList("a.com", "a.com", "example.com"));

        assertEquals(true, links.equals(result));
    }
```

* Actual Outputs

1) For my implementation

![Image](Images\Lab-Report-4\output2.png)

2) For the reviewed repo's implementation

![Image](Images\Lab-Report-4\reviewed2.png)

* Discussion

#[Discussion here]


## Snippet 3

* Snippet 3 Content

(Based on the report writeup downloaded on 05/19/2022)

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

* Expected Output

![Image](Images\Lab-Report-4\3.png)

```
[]
```

* Test Code in MarkdownParseTest.java

```
// For my implementation
@Test
    public void checkSnippet3() throws IOException {
        Path file = Path.of("LabReport4-Snippet-3.md");
        String content = Files.readString(file);
        ArrayList<String> links = MarkdownParse.getLinks(content);
        ArrayList<String> result = new ArrayList<String>(Arrays.asList());

        assertEquals(true, links.equals(result));
    }

// For reviewed repo's implementation
@Test
    public void checkReviewedSnippet3() throws IOException {
        Path file = Path.of("LabReport4-Snippet-3.md");
        String content = Files.readString(file);

        // Call getLinks() of the reviewed repo's MarkdownParse file
        ArrayList<String> links = reviewedMarkdownParse.getLinks(content);
        ArrayList<String> result = new ArrayList<String>(Arrays.asList());

        assertEquals(true, links.equals(result));
    }
```

* Actual Outputs

1) For my implementation

![Image](Images\Lab-Report-4\output3.png)

2) For the reviewed repo's implementation

![Image](Images\Lab-Report-4\reviewed3.png)

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