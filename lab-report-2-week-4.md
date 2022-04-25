# Code Diff #1
![image](https://user-images.githubusercontent.com/13767574/165031931-70b35fc7-7088-42ce-b056-2a90a8df5298.png)
test-file7.md had a failure inducing input which prompted me to add a checker if the required symbol was ever found. 
Symptom:
Infinite loop, zero output. 

The failure happens because of a bug, where there is no check to make sure that the required symbol is found. When a symbol is not found, it returns -1, which causes the while loop to never end. This causes the symptom of an infinite loop, when given a failure-inducing input which does not contain ( or ].

# Code Diff #2
![image](https://user-images.githubusercontent.com/13767574/165034320-154f138e-3e66-44e9-9b62-86413cd40244.png)
test-file5.md is a failure inducing input, as it is detecting a link when there is none. =
Symptom:
It incorrectly outputs `[page.com]`.

This failure happens due to no check being done to see if the ] actually touches the (. This prompted me to add a quick fix for that, which caused the bug to go away, and removed the symptoms. 

Didn't have a third error. 
