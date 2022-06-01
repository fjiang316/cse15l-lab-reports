# CSE 15L Lab Report 5
## Compare Results From Two Files
* Step 1: Creating script.sh file with execution direction on running the java file.
* Step 2: Store the result of executing `MarkdownParse.java` on all the `.md` files in a txt file using: `bash script.sh > results.txt`
* Step 3: Repeat step 2 on another repository, store the result using: `bash script.sh > otherResult.txt`
* Step 4: Compare results using: `vimdiff <my-markdown-parser>/results.txt <provided-markdown-parser>/otherResult.txt`

Note: The red line indicates different results.

## Test Files with Different Results
[File 1](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/510.md)

[File 2](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/516.md?plain=1)

## Behavior for File 1
