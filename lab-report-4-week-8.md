# Lab Report 4 - Week 8: Testing Snippets


## Link to MarkdownParse

[My MarkdownParse](https://github.com/Alexander-Qinn/markdown-parse.git)

[Reviewed MarkdownParse](https://github.com/Alexander-Kourjanski/markdown-parse.git)

### Snippet 1: 

![Snippet1](snippet-1.png)

Test file should be printing the links

## My Test:
```
@Test
    public void testSnippet1() throws IOException {
        String regFile = Files.readString(Path.of("./snippet-1.md"));
        String[] regLines = regFile.split("\n");
        assertEquals(List.of("`google.com", "google.com", "ucsd.edu"), MarkdownParse.getLinks(regLines));
    }
```

## Their Test:
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