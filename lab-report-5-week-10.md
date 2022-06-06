In order to find tests wiht different results, I used vimdiff on the results 
of running the given bash script that prints test names, and searched manually. 
I Found test-files/14.md and test-files/194.md having different results, with my 14.md 
detecting no link but given implementation giving [/foo], while my 194.md infinitely looped 
and the given implementation returned [url].

https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/14.md
https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/194.md

Looking at the two md files and looking at how vscode inspects the links, 14.md
should have a link titled “not a link” linking to “/foo”, and 194.md should have 
“Foo\*bar]” as a link, linking to “title (with parens)”.
Image of vscode's interpretation of test files 14.md and 194.md, respectfully. 
![image](https://user-images.githubusercontent.com/13767574/172109276-67f81ee4-4cbe-4812-9e73-89e35384386a.png)

My implementation is incorrect for 14.md, as it detects no link, and my implementation is incorrect for 
194.md as it gets stuck in an infinite loop. For the given implementation, 14.md is correct, 
but 194.md is incorrect, as it incorrectly states “url” instead of the expected “title (with parens)”.
Image of vim diff showing this below: (my implementation left, given right)
![image](https://user-images.githubusercontent.com/13767574/172109420-d1af3697-4e48-445f-ad13-3c6d8ccc9690.png)

For my implementation on 14.md, this code snippet is what causes it to fail:
![image](https://user-images.githubusercontent.com/13767574/172109468-c9da0e67-908d-44fe-aefa-b8137adbac4d.png)

Specifically the last line, my parser assumes that there will only be one link, so it looks at the second bracket pair, sees that there is no open paren to close it, and returns an empty list instead of remembering the link it caught before. To fix this, I would have to make it remember previous links, and once it gets to a spot where it cannot find another pair, return those previous links instead of an empty ArrayList. 

For my implementation on 194.md, this code snippet is what causes it to fail:
![image](https://user-images.githubusercontent.com/13767574/172109493-37ad2ee3-e826-4bd6-8d77-e577912030aa.png)
There is an open parentheses not touching a bracket, so it adds one to currentIndex, then continues. This would fix it, if it wasn’t for this snippet:
![image](https://user-images.githubusercontent.com/13767574/172109515-27304303-b24e-413f-869e-7b1d73a6ff4b.png)
That causes it to reset back to 0, make it go to first bracket, see it isn’t touching, back to top, and so on. In order to fix this, I would have to add a check to make sure that openBracket is only being set to zero if this is the first iteration of the while loop. 

For the given implementation on 194.md, it is incorrectly giving url as there is no check to make sure that the closing bracket and open parenthesis are touching, so in order to fix this there would need to be a statement checking that their indexes are touching, accounting for nested brackets and parenthesis. 
