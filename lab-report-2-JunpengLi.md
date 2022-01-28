# Lab-Report-2
**Name:Junpeng Li**
>
**Professor Joe**
>
**Date:01/27/2022**
>
**CSE 15L**
>
*In this lab report, I will introduce the three types of code changes in the `MarkdownParse.java` file in particular to resolve three different issues*
___
# Test 1 with no parenthesis in the link format
___
![image](s1.png)
>
Link to the test file for a failure-inducing input:
[link](https://github.com/rinakaura/markdown-parse/blob/main/new-file.md)
>
The symptom of this failure-inducing input:
```
Exception in thread "main" java.lang.StringIndexOutOfBoundsException: begin 0, end -1, length 20
        at java.base/java.lang.String.checkBoundsBeginEnd(String.java:3756)
        at java.base/java.lang.String.substring(String.java:1902)
        at MarkdownParse.getLinks(MarkdownParse.java:18)
        at MarkdownParse.main(MarkdownParse.java:26) 
```
Literally, the failure-inducing input `[a link!] google.com` has no parenthesis in the link format which will cause the line ` toReturn.add(markdown.substring(openParen + 1, closeParen));`to have a index out of bound bug because the index of *openParen* and *closeParen* are *-1*. Therefore, as long as the user complies and runs the java file with this failure-inducing input, an symptom called *StringIndexOutOfBoundException* will be thrown out.
>
The way to fix this bug is to check the comparision before running the while loop.For instance, if the index of the open-parenthesis is not -1 which typically means it exists in the test file, the while loop will run.
>
___






