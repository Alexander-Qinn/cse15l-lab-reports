# CSE 15L Week 4 Lab Report 2


# 1. Code Change 1

## Dealing with open parenthesis

![Image](Paren.png)\
Test File: [First Test](https://github.com/Alexander-Qinn/cse15l-lab-reports/blob/main/test-file1.md)

Symptom:

```
Exception in thread "main" java.lang.OutOfMemoryError: Java heap space
        at java.base/java.lang.StringLatin1.newString(StringLatin1.java:769)
        at java.base/java.lang.String.substring(String.java:2709)
        at MarkdownParse.getLinks(MarkdownParse.java:18)
        at MarkdownParse.main(MarkdownParse.java:27)
```

As a lab group me and Shad had agreed that the while looped seemed
very unnecesary to use to loop through our objects and instead we
switched it out with a `for(String line : markdown)` loop. Furthermore with the out of memory error, we decided to correct it with `if (line.subscript(")", line.length))` in order to prevent the program from reading the rest of the files.

# 2. Code Change 2

## Dealing with text after code

![Image](Text.png)\
Test File: [Second Test](https://github.com/Alexander-Qinn/cse15l-lab-reports/blob/main/test-file2.md)

Symptom:

```
Exception in thread "main" java.lang.StringIndexOutOfBoundsException: begin 0, end -1, length 27
        at java.base/java.lang.String.checkBoundsBeginEnd(String.java:4601)
        at java.base/java.lang.String.substring(String.java:2704)
        at MarkdownParse.getLinks(MarkdownParse.java:18)
        at MarkdownParse.main(MarkdownParse.java:27)
```

The bug present was that the program couldn't differientiate empty links and real links within the brackets. Then it would attempt to find the parenthesis and then throw an IndexOutOfBoundsExceptions. To overcome this we simply check for the indices of the brackets and parenthesis.
# 3. Code Change 3

## Dealing with an empty Link

![Image](Empty.png)\
Test File: [Third Test](https://github.com/Alexander-Qinn/cse15l-lab-reports/blob/main/test-file3.md)

Symptom:

```
alexq@Alexanders-MacBook-Pro cse15l-lab-reports % java MarkdownParse test-file3.md
39
[page.com]
```

This is a case where the program should skip all extra commentary and text within brackets and parenthesis in order to fish out the link. The original would only find `[]`  without reading anything between the parenthesis.