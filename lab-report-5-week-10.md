# CSE 15L Lab Report 5
## Compare Results From Two Files
* Step 1: Creating script.sh file with execution direction on running the java file.
* Step 2: Store the result of executing `MarkdownParse.java` on all the `.md` files in a txt file using: `bash script.sh > results.txt`
* Step 3: Repeat step 2 on another repository, store the result using: `bash script.sh > otherResult.txt`
* Step 4: Compare results using: `vimdiff <my-markdown-parser>/results.txt <provided-markdown-parser>/otherResult.txt`

Note: The red line indicates different results.

## Test Files with Different Results
[File 1](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/514.md?plain=1)

[File 2](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/516.md?plain=1)

## Behavior for File 1
### Correct implementation: 

My implementation returns the wrong output (infinite loop) while the provided implementation returns the correct output (`[/url]`).

### Actual Outputs
![output 1](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport%205.png?raw=true)

### Expected Output
Content of file: `[link \[bar](/uri)`

The expected output should be a list (i.e. `[/url]`), because the link content is in valid format.

### Potential Fix
My file ran into an infinite loop because in my algorithm, after I check for the existence of another open bracket between openbracket and closebracket, I update the closebracket to the next close bracket after the index of closebracket. However, I assumed that there will be another close bracket and did not break from the loop or continue if there's only one close bracket. So I should insert after searching for the index of closebracket2:
```
if(closebracket2 == -1) 
{currIndex = closebracket + 1; 
continue;}
```


## Behavior for File 2
### Correct implementation:
My implementation returns the correct output (`[]`), while the provided implementation returns the wrong output(`[moon.jpg]`).

### Actual Outputs
![output 1](https://github.com/fjiang316/cse15l-lab-reports/blob/main/labreport%205.png?raw=true)

### Expected Output
Content of file: `[![moon](moon.jpg)](/uri)`

The expected output should be empty list (`[]`). This is because the link inside the bracket is an image link, therefore should not be a valid returned value for out getLink method.

### Potential Fix
After line 75 of the MarkdownParse.java file in the provided repository, which is right before the line where we add the substring to the toReturn, we should added there an if statement to check whether this link is a valid markdown link or an image. To do this, we should add:
```
if (markdown.substring(openParen-1, openParen).equals("!")) {
    currIndex = closebracket + 1;
    continue;
}
```