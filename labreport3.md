# CSE 15L
## Lab Report 3 | Chosen Command : ```grep```

The command ```grep``` takes a pattern, like a string, and a file, and then prints out all lines of the file that match the given pattern.

*Note: Some output has been modified in ways such as deleting extra whitespace, adding newlines etc for formatting purposes.*

### Command-line Option 1 : ```-i```
The command-line option ```-i``` is used with ```grep``` when we want to ignore the case of the specified pattern we are searching for. With this option we search for
the pattern in both upper and lower case.

1) Example 1: 
First, we use the ```grep``` command without the option ```-i```, to find a string in both upper and lower case individually, and see that it only prints the line matching the case of the string passed. Then, when the command-line option is used, we can see that the output includes lines that contain the string in both upper and lower case. 

~~~
docsearch % grep "terrorism" ./technical/911report/chapter-2.txt  
  terrorism and of attacks on civilians, he replied:"We believe that the worst thieves
  terrorism, without the need for the Islamic Army Shura. Bin Ladin was prepared to
docsearch % grep "TERRORISM" ./technical/911report/chapter-2.txt   
  THE FOUNDATION OF THE NEW TERRORISM
docsearch % grep -i "TERRORISM" ./technical/911report/chapter-2.txt
  THE FOUNDATION OF THE NEW TERRORISM
  terrorism and of attacks on civilians, he replied:"We believe that the worst thieves
  terrorism, without the need for the Islamic Army Shura. Bin Ladin was prepared to
~~~

2) Example 2:
Here, we do the same thing again, using a different string on a different file. We can again see the same results. One interesting thing to see is how it also includes strings that are a mix of both upper and lower case as seen in the example below. So, it is completely case-insensitive.

~~~
docsearch % grep "March" ./technical/government/About_LSC/Comments_on_semiannual.txt
  March 31, 2001.
  in March 2001, highlights the state planning successes of 18 states
  Columbia. In March, LSC organized and sponsored a national 2-day
  TIGs. In October 2000 and March 2001, LSC hosted meetings of TIG
  At the Equal Justice Conference ("EJC") held in March 2001 in
  first conference was held on March 31, 2001 in conjunction with the
  Practices" at the March ABA/NLADA Equal Justice Conference.
  during the March ABA/NLADA Equal Justice Conference. Approximately
  Ending March 31, 2001 TABLE 2
  Period Ending March 31, 2001, With Recommendations That Funds Be
docsearch % grep "MARCH" ./technical/government/About_LSC/Comments_on_semiannual.txt
  OCTOBER 1, 2000 - MARCH 31, 2001
docsearch % grep "march" ./technical/government/About_LSC/Comments_on_semiannual.txt
docsearch % grep -i "march" ./technical/government/About_LSC/Comments_on_semiannual.txt
  OCTOBER 1, 2000 - MARCH 31, 2001
  March 31, 2001.
  in March 2001, highlights the state planning successes of 18 states
  Columbia. In March, LSC organized and sponsored a national 2-day
  TIGs. In October 2000 and March 2001, LSC hosted meetings of TIG
  At the Equal Justice Conference ("EJC") held in March 2001 in
  first conference was held on March 31, 2001 in conjunction with the
  Practices" at the March ABA/NLADA Equal Justice Conference.
  during the March ABA/NLADA Equal Justice Conference. Approximately
  Ending March 31, 2001 TABLE 2
  Period Ending March 31, 2001, With Recommendations That Funds Be
~~~

Both these examples successfully show that the command-line option ```-i``` for ```grep``` is used when we want to ignore the case of the passed string, and print out all matching lines.


### Command-line Option 2 : ```-v```
The command-line option ```-v``` is used with ```grep``` when we want to exclude the specified pattern passed. With this option we print out all the lines that do not contain the passed string.

1) Example 1: 
First, we use the ```grep``` command without the option ```-v```, to find a string ```" the "``` in a file, and see that it only one line contains the string. Then when we use the command-line option, we see that it prints out all lines of the file except that one line which contained the string.

~~~
docsearch % grep " the " technical/plos/pmed.0020191.txt
  meta-question: who is to decide who is to decide? I apologize to the authors if my brief
docsearch % grep -v " the " technical/plos/pmed.0020191.txt
  The excellent article by Jordan Paradise, Lori B. Andrews, and colleagues, “Ethics.
  Constructing Ethical Guidelines for Biohistory” [1], neither advocates nor argues against
  biohistorical research; instead, it points out that such investigations are currently
  taking place without guidelines—ethical, scientific, moral, or religious. The question
  remains: if such guidelines were to be established, what individuals, institutions,
  governments, medical examiners, family members, or intrepid biographers are to be given
  permission? Who is to decide what is “historically significant”? Not to mention the
  comments [2] implied that they took a position on this issue.
~~~

2) Example 2:
We can also combine it with ```-i```, and so it finds all lines that don't contain that string (regardless of case). We can see that the output of the example above and below are different.

~~~
docsearch % grep -v -i " the " technical/plos/pmed.0020191.txt





  Constructing Ethical Guidelines for Biohistory” [1], neither advocates nor argues against
  biohistorical research; instead, it points out that such investigations are currently
  remains: if such guidelines were to be established, what individuals, institutions,
  governments, medical examiners, family members, or intrepid biographers are to be given
  permission? Who is to decide what is “historically significant”? Not to mention the
  comments [2] implied that they took a position on this issue.



~~~

Both these examples successfully show that the command-line option ```-v``` for ```grep``` is used when we want to exclude the passed string, and print out all lines that don't contain the string.


### Command-line Option 3 : ```-c```
The command-line option ```-c``` is used with ```grep``` when we want to find the number/count of the matching lines. It returns the number of lines that match the given string.

1) Example 1: 
We saw in command-line option 2's example 1 that the command ```grep " the " technical/plos/pmed.0020191.txt```, printed out only 1 line. In this example we used ```c``` with the same command to show that the number of lines that matched our search was just 1.

~~~
docsearch % grep -c " the " technical/plos/pmed.0020191.txt 
  1
~~~

2) Example 2:
We can also combine it with other command-line options. Again, using command-line option 2's example 2, we know that the command ```grep -v -i " the " technical/plos/pmed.0020191.txt``` outputs 14 lines (including whitespace lines, which I did not remove from that example's output for demonstration purposes). Combining this with ```c```, we can see just that in the output.

~~~
docsearch % grep -v -i -c " the " technical/plos/pmed.0020191.txt 
  14
~~~

Both these examples successfully show that the command-line option ```-c``` for ```grep``` is used when we want to find the count of the number of lines that match our search.


### Command-line Option 4 : ```-r```
The command-line option ```-r``` is used with ```grep``` when we want to search for our string recursively in a specified directory as well as all of its sub-directories.

1) Example 1: 
In this example, we first tried to search for the string in the ```technical``` directory, but we were unable to do so. Using ```-r```, we were able to recursively search for our string in the given directory and all its sub-directories, and output the lines that matched.

~~~
docsearch % grep " Bin Laden " ./technical
  grep: ./technical: Is a directory
docsearch % grep " Bin Laden " ./technical/
  grep: ./technical/: Is a directory
kriishmehta@Kriishs-MacBook-Pro docsearch % 
docsearch % grep -r " Bin Laden " ./technical/911report 
./technical/911report/chapter-13.5.txt:            8. Tim Weiner, "U.S. Hard Put to Find Proof Bin Laden Directed Attacks," New York
./technical/911report/chapter-6.txt:                to resolve the Bin Laden problem at the earliest possible time." But Zinni came back
./technical/911report/chapter-11.txt:                terrorist leader, with the headline "U.S. Hard Put to Find Proof Bin Laden Directed
~~~

2) Example 2:
Here I combined ```-r``` with ```-c``` to show that it recursively looked for the string in each sub-directory, and displayed the count of that string in that directory along with it. We can see that the count of matching lines corresponds to the output we got above.

~~~
docsearch % grep -c -r " Bin Laden " ./technical/911report
  ./technical/911report/chapter-13.4.txt:0
  ./technical/911report/chapter-13.5.txt:1
  ./technical/911report/chapter-13.1.txt:0
  ./technical/911report/chapter-13.2.txt:0
  ./technical/911report/chapter-13.3.txt:0
  ./technical/911report/chapter-3.txt:0
  ./technical/911report/chapter-2.txt:0
  ./technical/911report/chapter-1.txt:0
  ./technical/911report/chapter-5.txt:0
  ./technical/911report/chapter-6.txt:1
  ./technical/911report/chapter-7.txt:0
  ./technical/911report/chapter-9.txt:0
  ./technical/911report/chapter-8.txt:0
  ./technical/911report/preface.txt:0
  ./technical/911report/chapter-12.txt:0
  ./technical/911report/chapter-10.txt:0
  ./technical/911report/chapter-11.txt:1
~~~

Both these examples successfully show that the command-line option ```-r``` for ```grep``` is used when we want to recursively search through a directory and all of its sub-directories.


### Sources:
Instead of individually citing sources for each command-line option, I will just mention it here collectively, since I found everything from just one source:

[ComputerNetworkingNotes.com](https://www.computernetworkingnotes.com/linux-tutorials/grep-options-regex-parameters-and-regular-expressions.html) 

I searched for grep command-line options on google, and found this useful website which had a list and description of many command-line options used with grep. I then played around with the command-line options on my own to better understand what they did, and used that understanding to finish my lab report. 

I already had knowledge of the ```-c``` command-line option from one of the labs. I could not find my exact source for that since I didn't remember what I looked up during that lab class, but that knowledge stuck with me and so I used that directly.

