# CSE 15L Lab Report 4
## Introduction

## Repository Used
- [My MarkdownParse Repository](https://github.com/fjiang316/markdown-parser-fork)
- [Repository I Reviewed](https://github.com/calistajlee/lab6-markdown-parser.git )

## Snippet 1 
### Desired Output
The first line does not produce any link, the last three lines produce valid links. The output should be `['google.com, google.com, ucsd.edu]`
### Test Designed for Snippet 1
The test I designed for testing snippet 1 is the same for both repositories. It is as following:
```
@Test
    public void testSnippet1() throws IOException {
        Path fileName = Path.of("Snippet1.md");
        String content = Files.readString(fileName);
        ArrayList<String> result = MarkdownParse.getLinks(content);
        assertEquals(List.of("`google.com", "google.com", "ucsd.edu"), result);
    }
```
### Result of the Test
- **My MarkdownParse test file**: The test *failed* for line 54 of the test file. The details are as shown in the following screenshot.
![test result for snippet 1](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport4%20snippet1%20my%20test%20output.png?raw=true)
- **Reviewed MarkdownParse test file**: The test *failed* for line 218 of the test file. The details are as shown in the following screenshot.
![result for snippet 1](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport4%20snippet1%20reviewed%20repo%20result.png?raw=true)

## Snippet 2
### Desired Output
All three lines in the snippet should produce valid links. The resulting output should be `[a.com, a.com(()), example.com]`.
### Test Designed for Snippet 2
The test I designed for testing snippet 2 is the same for both repositories. It is as following:
```
@Test
    public void testSnippet2() throws IOException {
        Path fileName = Path.of("Snippet2.md");
        String content = Files.readString(fileName);
        ArrayList<String> result = MarkdownParse.getLinks(content);
        assertEquals(List.of("a.com", "a.com(())", "example.com"), result);
    }
```
### Result of the Test
- **My MarkdownParse test file**: The test *failed* for line 62 of the test file. The details are as shown in the following screenshot.
![my test result](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport4%20snippet2%20my%20test.png?raw=true)
- **Reviewed MarkdownParse test file**: The test *failed* for line 218 of the test file. The details are as shown in the following screenshot.
![reviewed test result](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport4%20snippet2%20reviewed%20test.png?raw=true)

## Snippet 3
### Desired Output
The snippet file should produce three valid links. The output should be as the following: `[https://www.twitter.com, https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule, https://cse.ucsd.edu/]`
### Test Designed for Snippet 3
The test I designed for testing snippet 3 is the same for both repositories. It is as following:
```
@Test
    public void testSnippet3() throws IOException {
        Path fileName = Path.of("Snippet3.md");
        String content = Files.readString(fileName);
        ArrayList<String> result = MarkdownParse.getLinks(content);
        assertEquals(List.of("https://www.twitter.com", "https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule", "https://cse.ucsd.edu/"), result);
    }
```
### Result of the Test
- **My MarkdownParse test file**: The test *failed* for line 70 of the test file. The details are as shown in the following screenshot.
![my test result](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport4%20snippet2%20my%20test.png?raw=true)
- **Reviewed MarkdownParse test file**: The test *failed* for line 218 of the test file. The details are as shown in the following screenshot.
![reviewed test result](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport4%20snippet2%20reviewed%20test.png?raw=true)