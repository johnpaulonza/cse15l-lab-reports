# Lab Report 4 Week 8

#### My markdown-parse repo: https://github.com/johnpaulonza/markdown-parser
#### Reviewed markdown-parse implementation from week 7: https://github.com/Miyuki-L/markdown-parser

---

## **Snippet 1:**
~~~
`[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
~~~
### Expected output is:
![snippet1_expected_output](lr4_ss\lr4_ss1.png)

### Code in test file:
![snippet1_test_code](lr4_ss\lr4_ss2.png)

### Result of my implementation:
The test passed.

### Result of reviewed implementation:
![snippet1_other_result](lr4_ss\lr4_ss3.png)

---

## **Snippet 2:**
~~~
[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)
~~~
### Expected output is:
![snippet2_expected_output](lr4_ss\lr4_ss4.png)
### Code in test file:
![snippet2_test_code](lr4_ss\lr4_ss5.png)

### Result of my implementation:
![snippet2_my_result](lr4_ss\lr4_ss6.png)

### Result of reviewed implementation:
![snippet2_other_result](lr4_ss\lr4_ss7.png)

---

## **Snippet 3:**
~~~
[this title text is really long and takes up more than 
one line

and has some line breaks](
    https://www.twitter.com
)

[this title text is really long and takes up more than 
one line](
https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule
)


[this link doesn't have a closing parenthesis](github.com

And there's still some more text after that.

[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/



)

And then there's more text

~~~
### Expected output is:
### Code in test file:
![snippet3_test_code](lr4_ss\lr4_ss8.png)

### Result of my implementation:
![snippet3_my_result](lr4_ss\lr4_ss9.png)

### Result of reviewed implementation:
![snippet3_other_result](lr4_ss\lr4_ss10.png)

---

**Do you think there is a small (<10 lines) code change that will make your program work for snippet 1 and all related cases that use inline code with backticks? If yes, describe the code change. If not, describe why it would be a more involved change.**

For my code, I was able to ignore the backticks since my code only checked the contents within the parenthesis, only if the open parenthesis is preceded by a close bracket. So yes, I think there can be a small code change that can fix any cases with backticks. The code doesn't take the backticks into account.
<br>
<br>
<br>
**Do you think there is a small (<10 lines) code change that will make your program work for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets? If yes, describe the code change. If not, describe why it would be a more involved change.**

I think there would definitely be a more involved change. You would have to determine if each link read by the program is nested within brackets. Or another approach would be to notice the pattern of a nested link and prevent it from reading the nested link. That would require more variables added, and new if statements, totaling more than 10 lines of code added.
<br>
<br>
<br>
**Do you think there is a small (<10 lines) code change that will make your program work for snippet 3 and all related cases that have newlines in brackets and parentheses? If yes, describe the code change. If not, describe why it would be a more involved change.**

In my test implementation, I didn't count any of the content in snippet 3 as links. I think this could be a small code change as the program could check for new lines within either the brackets or parenthesis and immediately not count it as a link.