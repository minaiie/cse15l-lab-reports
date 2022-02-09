# Lab Report 2 
## Code Change 1
![Image](https://github.com/minaiie/cse15l-lab-reports/blob/main/Screen%20Shot%202022-02-02%20at%203.49.23%20PM.png)
Link to failure inducing file: [Test File 2]https://github.com/minaiie/markdown-parse/blob/main/test-file2.md)
### Command used to produce the output

`
javac MarkdownParse.java
`

`
java MarkdownParse test-file2.md
`
### Failing Output

`
[https(, https(, this is an image address]
`

The original code follows the following order when it look fors the content to print:
1) first instance of an open bracket
2) a close bracket
3) an open parenthesis
4) a closed parenthesis

The problem arises when the link itself contained brackets or parentheses because the code would take those characters to enclose the link. `test-file2.md` contains links not only with parenthesis but also an image address, which should not show up in the output of `MarkdownParse.java` leading to an incorrect ouptut.

---
## Code Change 2
![Image](https://github.com/minaiie/cse15l-lab-reports/blob/main/Screen%20Shot%202022-02-02%20at%204.00.45%20PM.png)
Link to failure inducing file: [Test 6](https://github.com/minaiie/markdown-parse/blob/main/test-6.md)


### Command used to produce the output

`
javac MarkdownParse.java`

`
java MarkdownParse test-file6.md
`
### Failing Output

`
[pages.com]
`

Our newly implemented `MarkdownParse.java` incudes a helper method `isOfLinkForm` that fixes the problem of the code breaking when there are brackets or parentheses in the links. However, when printing test-6, the problem now becomes an incorrect printed image link while the result sohuld be an empty array of no links.

---
## Code Change 3
![Image](https://github.com/minaiie/cse15l-lab-reports/blob/main/Screen%20Shot%202022-02-02%20at%204.37.36%20PM.png)
Link to failure inducing file: [Test File 8](https://github.com/minaiie/markdown-parse/blob/main/test-file8.md)

### Command used to produce the output

`
javac MarkdownParse.java`

`
java MarkdownParse test-file8.md
`
### Failing Output

`
[a link on the first line]
`

The updated helper method `isOfLinkForm` fixes the issue when images were added as links. However, in `test-file8.md` the method returns the url when it should return an empty array as the link is correctly put into a bracket.
