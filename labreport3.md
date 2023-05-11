# CSE 15L
## Lab Report 3 

### Chosen Command : ```grep```
The command ```grep``` takes a pattern, like a string, and a file, and then prints out all lines of the file that match the given pattern.
NOTE: I know my report is currently incomplete but wanted to submit to get feedback on the format and style of my examples so far.

**Command-line Option 1 : ```-i```**
The command-line option ```-i``` is used with ```grep``` when we want to ignore the case of the specified pattern we are searching for. With this option we search for
the pattern in both upper and lower case.

1) Example 1: 
First, we use the ```grep``` command without the option ```-i```, to find a string in both upper and lower case individually, and see that it only prints the line matching the case of the string passed. Then, when the command-line option is used, we can see that the output includes lines that contain the string in both upper and lower case. 

~~~
kriishmehta@Kriishs-MacBook-Pro docsearch % grep "terrorism" ./technical/911report/chapter-2.txt  
                terrorism and of attacks on civilians, he replied:"We believe that the worst thieves
                terrorism, without the need for the Islamic Army Shura. Bin Ladin was prepared to
kriishmehta@Kriishs-MacBook-Pro docsearch % grep "TERRORISM" ./technical/911report/chapter-2.txt   
            THE FOUNDATION OF THE NEW TERRORISM
kriishmehta@Kriishs-MacBook-Pro docsearch % grep -i "TERRORISM" ./technical/911report/chapter-2.txt
            THE FOUNDATION OF THE NEW TERRORISM
                terrorism and of attacks on civilians, he replied:"We believe that the worst thieves
                terrorism, without the need for the Islamic Army Shura. Bin Ladin was prepared to
~~~

2) Example 2:
Here, we do the same thing again, using a different string on a different file. We can again see the same results. One interesting thing to see is how it also includes strings that are a mix of both upper and lower case as seen in the example below. So, it is completely case-insensitive.

~~~
kriishmehta@Kriishs-MacBook-Pro docsearch % grep "March" ./technical/government/About_LSC/Comments_on_semiannual.txt
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
kriishmehta@Kriishs-MacBook-Pro docsearch % grep "MARCH" ./technical/government/About_LSC/Comments_on_semiannual.txt
  OCTOBER 1, 2000 - MARCH 31, 2001
kriishmehta@Kriishs-MacBook-Pro docsearch % grep "march" ./technical/government/About_LSC/Comments_on_semiannual.txt
kriishmehta@Kriishs-MacBook-Pro docsearch % grep -i "march" ./technical/government/About_LSC/Comments_on_semiannual.txt
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


**Command-line Option 2 : ```-v```**
The command-line option ```-v``` is used with ```grep``` when we want to exclude the specified pattern passed. With this option we print out all the lines that do not contain the passed string.

1) Example 1: 
First, we use the ```grep``` command without the option ```-v```, to find a string ```" the "``` in a file, and see that it only one line contains the string. Then when we use the command-line option, we see that it prints out all lines of the file except that one line which contained the string.

~~~
kriishmehta@Kriishs-MacBook-Pro docsearch % grep " the " technical/plos/pmed.0020191.txt
        meta-question: who is to decide who is to decide? I apologize to the authors if my brief
kriishmehta@Kriishs-MacBook-Pro docsearch % grep -v " the " technical/plos/pmed.0020191.txt
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

~~~

~~~

Both these examples successfully show that the command-line option ```-v``` for ```grep``` is used when we want to exclude the passed string, and print out all lines that don't contain the string.
