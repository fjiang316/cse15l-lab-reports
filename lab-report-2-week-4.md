# CSE 15L Lab Report 2 (Week 4 Debugging)
## Introduction
In this lab report, we are going to demonstrate the process of fixing bugs within the code program through incremental developing. We are going to demeonstrate the steps it takes to discover the bug, attempt to fix it, and reflect on the algorithm.

## First Error (Index out of bound)
### Code After Change

![bug1](https://github.com/fjiang316/cse15l-lab-reports/blob/main/bug%201%20fix,%20index%20out%20of%20bound.png?raw=true)

### Failure Inducing Input
> Test case file that induce this change to happen: [failed test case](https://github.com/fjiang316/markdown-parser-fork/blob/main/test2.md)

The brief view of the content in markdown format is as following:
```
# Title

(link 1)
(link 2)
```

### Symptom in Previous Version
![bug1 Symptom](https://github.com/fjiang316/cse15l-lab-reports/blob/main/bug%201%20symptom.png?raw=true)

### Reason Behind Symptom
The bug within the original code is that it doesn't consider the case when the open bracket is not found after the specific index. When the currentIndex is valid and the while loop proceed, it will execute the line that find the index of the open bracket. If the open bracket cannot be found (like in the test case above), the value for openBracket will be -1. This means that if we don't check the value of openBracket at this point and break from the loop, the order `int closeBracket = markdown.indexOf("]", openBracket);` will proceed, which will return the index out of bound error.

## Second Error (Wrong Behavior - Link Inside Bracket)
### Code After Change

![bug 2 fix](https://github.com/fjiang316/cse15l-lab-reports/blob/main/bug%202%20fix.png?raw=true)

### Failure Inducing Input
> Test case file that induce this change to happen: [failed test case](https://github.com/fjiang316/markdown-parser-fork/blob/main/new-test.md)

The brief view of the content in markdown format is as following:
```
# Title

[link1](link1.com)
[[link2](link2.com)](real_link2.com)
```

### Symptom in Previous Version
![bug 2 symptom](https://github.com/fjiang316/cse15l-lab-reports/blob/main/bug%202%20symp.png?raw=true)

### Reason Behind Symptom
In the previous version, the algorithm checks for the open bracket, then the close bracket after it. This means for the test case above, when there's another link inside the bracket, the previous code will detect the link inside the bracket as the link, which results in wrong behavior. In the fixed version, we checked whether there's another bracket inside the bracket by checking if there's another open bracket between the open bracket and the close bracket. If this is the case we update the close bracket to the next one. The process is as following:
```
int openBracket2 = markdown.indexOf("[", openBracket+1);
            if (openBracket2 < closeBracket && openBracket2 != -1) {
                closeBracket = markdown.indexOf("]", closeBracket+1);
            }
```