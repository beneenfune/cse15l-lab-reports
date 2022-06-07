## Lab Report 5

# How I found the tests with different results
I found the results by saving te results of the implementation and the lab's implementation in two different txt files, the comparing them using *vimdiff*

I did this by running the bash script:

    for file in test-files/*.md;
    do
        echo $file
        java MarkdownParse $file
    done

on the their implementation and saved it to results.txt by typing

    bash script.sh > results.txt

I then did the same ting to my own implementation and saved it to myResults.txt using

    bash script.sh > myResults.txt

I then used

    vimdiff myResults.txt results.txt

to see the differences in the results of my implementation vs their implementation.

# Link to test files

The two tests in my [repo](https://github.com/beneenfune/markdown-parser.git)
Test 1: [test 487](asdlkfjakgjlfkjeasv)
Test 2: [test 578](fjqeljdsbnmqrgkljegrnbfdk)

# Test 1
When comparing implementations, their implementation was correct.

As the preview shows, the expected output should be an empty list, [].
![test1_ExpectedOutput](lab5_test1ss.png)

My implementation's output
![test1_MyOutput](lab5_test1myOutput.png)

Lab 9 implementation's output
![test1_9output](lab5_test1theirOutput.png)

The bug can be found in the lab 9 write-up's implementation. It did not check the condition that the open parenthesis should be directly next to the end bracket. The code should run as tough that if they are not next to each other, it is not recognized as a valid link. The edit in the code would be to when finding openParen, we should check if closeBracket + 1 index is (. If it is a (, we should check for a valid link, else we can start the loop over and try to find the next open bracket again.


# Test 2
When comparing implementations, their implementation was correct.

As the preview shows, the expected output should be an empty list, [].
![test2_output](lab5_test2ss.png)

My implementation's output
![test2_MyOutput](lab5_tes21myOutput.png)

Lab 9 implementation's output
![test2_9output](lab5_test2theirOutput.png)

The bug can be found in my implementation. What's wrong was that my implementation does not check if the content inside parenthesis is actually a valid link. So, in the cases that it wasn't a link like now, it would be read as valid when it actually isn't. So the edit in the code would be to make it so that it checks for a " " and a "\n" in the link contents: it needs to make this check regardless of whether or not the brackets and the parentheses are in the right place and content exists in the bracket.