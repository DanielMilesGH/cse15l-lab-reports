# Code Diff #1
![image](https://user-images.githubusercontent.com/13767574/165031931-70b35fc7-7088-42ce-b056-2a90a8df5298.png)
test-file7.md had a failure inducing input which prompted me to add a checker if the required symbol was ever found. 
Symptom:
Infinite loop, zero output. 
![image](https://user-images.githubusercontent.com/13767574/166407395-0b1126dc-b2e7-4604-a672-636c2d9083bd.png)
I added `System.out.println(currentIndex)` in order to show that it never gets off index 1 without this fix. 

The failure happens because of a bug, where there is no check to make sure that the required symbol is found. When a symbol is not found, it returns -1, which causes the while loop to never end. This causes the symptom of an infinite loop, when given a failure-inducing input which does not contain ( or ].

# Code Diff #2
![image](https://user-images.githubusercontent.com/13767574/165034320-154f138e-3e66-44e9-9b62-86413cd40244.png)
test-file5.md is a failure inducing input, as it is detecting a link when there is none. =
Symptom:
It incorrectly outputs `[page.com]`.
![image](https://user-images.githubusercontent.com/13767574/166407514-b9cd0217-1ddc-4f26-94e2-6de46e759ce3.png)

This failure happens due to no check being done to see if the ] actually touches the (. This prompted me to add a quick fix for that, which caused the bug to go away, and removed the symptoms. 

# Code Diff #3
![image](https://user-images.githubusercontent.com/13767574/166408194-1b88ee46-4717-4f9b-8488-9761507a49f2.png)

A new test file I made with the content "\\[link1](website.com)", which in markdown does not create a link because of the '\\' character, but with MarkdownParse.java, it incorrectly states it is a link.

Symptom:
Incorrectly outputting `[website.com]`.
![image](https://user-images.githubusercontent.com/13767574/166408069-cc83b3cd-b831-4626-a04f-9da970c9ffd2.png)

(the here1 print is an irrelevant check with regards to the failure)
This failure happens in the same way the code diff #2 fail happens, where the code does not check for the '\\' character which would cause all links starting with '\\' to appear as a link in the parser. To fix this, I made it check the index before the link to fix this. The test file is called "lab-report-test.md". 
