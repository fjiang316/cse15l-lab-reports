# CSE 15L Lab Report 2 (Week 4 Debugging)
## Introduction
In this lab report, we are going to demonstrate the process of fixing bugs within the code program through incremental developing. We are going to demeonstrate the steps it takes to discover the bug, attempt to fix it, and reflect on the algorithm.

## First Error (Index out of bound)
- ### Code After Change

![bug1](https://github.com/fjiang316/cse15l-lab-reports/blob/main/bug%201%20fix,%20index%20out%20of%20bound.png?raw=true)

- ### Failure Inducing Input
> Test case file that induce this change to happen: [failed test case](https://github.com/fjiang316/markdown-parser-fork/blob/main/test2.md)

The brief view of the content in markdown format is as following:
```
# Title

(link 1)
(link 2)
```

- ### Symptom in Previous Version
![bug1 Symptom](https://github.com/fjiang316/cse15l-lab-reports/blob/main/bug%201%20symptom.png?raw=true)

- ### Reason Behind Symptom
**Bug within the original code**: lack cases when the open bracket is not found. 
1. For every iteration, the line to find open bracket will be carried out. 
2. If the open bracket cannot be found (like in the test case above), the value for openBracket will be -1. 
3. This means that if we don't break from the loop, the order `int closeBracket = markdown.indexOf("]", openBracket);` will proceed, which will return the index out of bound error.

## Second Error (Wrong Behavior - Link Inside Bracket)
- ### Code After Change

![bug 2 fix](https://github.com/fjiang316/cse15l-lab-reports/blob/main/bug%202%20fix.png?raw=true)

- ### Failure Inducing Input
> Test case file that induce this change to happen: [failed test case](https://github.com/fjiang316/markdown-parser-fork/blob/main/new-test.md)

The brief view of the content in markdown format is as following:
```
# Title

[link1](link1.com)
[[link2](link2.com)](real_link2.com)
```

- ### Symptom in Previous Version
![bug 2 symptom](https://github.com/fjiang316/cse15l-lab-reports/blob/main/bug%202%20symp.png?raw=true)

- ### Reason Behind Symptom
**Bug in previous version**: not checking the content of substring before adding to list. 
1. When there's another link inside the bracket, the first open bracket and first close bracket will be deteched when we want it to detect the second close brakct.
2. The previous code will detect the substring within the parenthesis within the bracket as the link. 
3. In the fixed version, we checked whether there's another open bracket between the open bracket and the close bracket. 
4. If this is the case we update the close bracket to the next one. (`closeBracket = markdown.indexOf("]", closeBracket+1);`)

## Third Error (Wrong Behavior - Invalid Link)
- ### Code After Fix
![bug 3 fix](https://github.com/fjiang316/cse15l-lab-reports/blob/main/big%203%20fix.png?raw=true)

- ### Failure Inducing Input
> Test case file that induce this change to happen: [failed test case](https://github.com/fjiang316/markdown-parser-fork/blob/main/test-file6.md)
The brief overview of the content is as following:
```
[](a link)
[
```

- ### Symptom in Previous Version
![bug 3 symptom](https://github.com/fjiang316/cse15l-lab-reports/blob/main/bug%203%20symp.png?raw=true)

- ### Reason Behind Symptom
**Bug in previous code**: add without checking if the substring is a valid link. 
1. We capture the substring at correct position, but insert it to the list without checking its content. 
2. In the sample test file above, `[a link on the first line]` is returned, which is not a valid link because valid links don't contains spaces. 
3. In the fixed version of the code, we contains cases to check whether the link is valid by the line: 
```
if (link.contains(" ")) {
                continue;
            }
```
