## Repositories
[My Repository](https://github.com/minaiie/markdown-parse)

[Reviewed Repository](https://github.com/AnniePhan02/CSE15L-Panther)

## Snippet 1
### Markdown Preview
![Image](./9.33.18.png)
### JUnit Tester Code
```
@Test
    public void getLinksLabReportTest1() throws IOException{
        Path fileName = Path.of("./lab-report-test-files/test-1.md");
        String contents = Files.readString(fileName);
        assertEquals(List.of("`google.com", "google.com", "ucsd.edu"),
            MarkdownParse.getLinks(contents));
    }
```
### My Implementation Tester Output
![Image](./9.33.39.png)
### Reviewed Implementation Tester Output
![Image](./9.33.47.png)

## Snippet 2
### Markdown Preview
![Image](./9.33.56.png)
### JUnit Tester Code
```
@Test
    public void getLinksLabReportTest2() throws IOException{
        Path fileName = Path.of("./lab-report-test-files/test-2.md");
        String contents = Files.readString(fileName);
        assertEquals(List.of("a.com", "a.com(())", "example.com"),
            MarkdownParse.getLinks(contents));
    }
```
### My Implementation Tester Output
![Image](./9.34.09.png)
### Reviewed Implementation Tester Output
![Image](./9.34.21.png)

## Snippet 3
### Markdown Preview
![Image](./9.34.31.png)
### JUnit Tester Code
```
@Test
    public void getLinksLabReportTest3() throws IOException{
        Path fileName = Path.of("./lab-report-test-files/test-3.md");
        String contents = Files.readString(fileName);
        assertEquals(List.of("https://www.twitter.com", "https://ucsd-cse15l-w22.github.io/", "https://cse.ucsd.edu/"),
            MarkdownParse.getLinks(contents));
    }
```
### My Implementation Tester Output
![Image](./9.34.53.png)
### Reviewed Implementation Tester Output
![Image](./9.35.04.png)
___
## Code Snippet Questions
### Snippet 1
Yes. Our code checks the markdown file line by line. By adding a procedure to check for  backticks within the line and ignore the stuff between the backticks, the program will work for snippet 1 and all related cases
### Snippet 2
Yes. Our code got every link right except `)](b.com`, meaning a fix in the parentheses matching methods can make our program work for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets.
### Snippet 3
No. Our program misses all the contents within the snippet. While our code assumes each line contains a link container and the link, it requires more indepth changes in adopting newline characters to try to make it work for snippet 3 and all related cases that have newlines in brackets and parentheses
