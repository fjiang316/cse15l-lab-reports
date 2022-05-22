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
![my test result](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport4%20snippet3%20my%20test.png?raw=true)
- **Reviewed MarkdownParse test file**: The test *failed* for line 234 of the test file. The details are as shown in the following screenshot.
![reviewed test result](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport4%20snippet3%20reviewed%20test.png?raw=true)

## Possible Fix for Snippet 1 (cases that use inline code with backticks)
I don't think there's a small code change (<10 lines) that can solve this issue. 
- This is because the only cases when this type of cases would work is: 
    - when both backticks are within brakets or both within parenthesis
    - or there's only one backtick. 
- This would require us to first find the location of the first backtick, then the location of second (if any), and compare the index with openbracket, closebracket, openparen, closeparen.


## Possible Fix for Snippet 2 (cases that nest parentheses, brackets, and escaped brackets)
The fix would take more than 10 lines.
- THis is because we need to address two types of issue:
    - The first is the nested links (i.e. [[a link](link)](link)). This would require us to manually check the position of inner bracket and parenthesis, which takes about 10 lines.
    - The second is the nested parenthesis. (i.e. after the bracket, the link is `a.com(())`). This would require a while loop to check if there's any nested parethesis after getting the substring.


## Possible Fix for Snippet 3 (cases that have newlines in brackets and parentheses)
The fix would take more than 10 lines. This is because there are 4 cases we need to check using a while loop inside the substring.

- Check if there are any *empty space at the begining* of the substring, remove them if there's any.
- Check if there's any *empty space at the back* of the substring, remove if any.
- Check if there's any *new lines at the beginning* of the substring, remove it.
- Check if there's any *new lines at the end* of the substring, remove it.

These would take more than 10 lines.