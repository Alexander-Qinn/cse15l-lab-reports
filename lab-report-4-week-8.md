# Lab Report 4 - Week 8: Testing Snippets


## Link to MarkdownParse

[My MarkdownParse](https://github.com/Alexander-Qinn/markdown-parse.git)

[Reviewed MarkdownParse](https://github.com/Alexander-Kourjanski/markdown-parse.git)

# Snippet 1: 

![Snippet1](snip1.png)

Test file should be printing the links

### My Test:
```
@Test
    public void testSnippet1() throws IOException {
        String regFile = Files.readString(Path.of("./snippet-1.md"));
        String[] regLines = regFile.split("\n");
        assertEquals(List.of("`google.com", "google.com", "ucsd.edu"), MarkdownParse.getLinks(regLines));
    }
```

### Their Test:
```
@Test
    public void testSnippet1() throws IOException {
        ArrayList<String> Image = new ArrayList<>();
        Image.add("`google.com");
        Image.add("google.com");
        Image.add("ucsd.edu");
        String ImageTest = MarkdownParse.converter("snippet-1.md");
        assertEquals(Image, MarkdownParse.getLinks(ImageTest));
    }
```

## CompileTime/RunTime 

The test fails with my MarkdownParse producing error message:
```
testSnippet1(MarkdownParseTest)
java.lang.AssertionError: expected:<[`google.com, google.com, ucsd.edu]> but was:<[url.com, `google.com, google.com, ucsd.edu]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet1(MarkdownParseTest.java:66)

FAILURES!!!
```
My parser includes url.com as a link when it shouldn't be one



Their code also fails the first test: 
```
testSnippet1(MarkdownParseTest)
java.lang.AssertionError: expected:<[`google.com, google.com, ucsd.edu]> but was:<[`google.com, google.com]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet1(MarkdownParseTest.java:66)

FAILURES!!!
```
They failed to include the ucsd.edu link due to the second bracket which made their code consider it empty instead of holding a link.
