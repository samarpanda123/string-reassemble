# string-reassemble
Reassemble the string


PART-1: CREATING THE Reassemble CLASS

The following code segment, gives the details about the declared variabes for the program.

import java.util.*;

public class Reassemble
{
    public static void main(String[] args)
    {

    }
}
EXPLAINATION

1. Import the header file import java.util.*;

2. Create the class using the class keyword.

3. Create the public static void main(String[] args), which is main() function.

.

PART-2: ACCEPTING THE LIST OF INPUT STRINGS

The following code segment, gives the details about this part.

        //Inside the main() function
        List<String> list = new ArrayList<String>();
        Scanner scanner = new Scanner(System.in);
        String line = scanner.nextLine();
        String[] words = line.split(" ");
        for(String word : words)
        {
            list.add(word);
        }
EXPLAINATION

1. Create the object of the List Interface, as an Arraylist. Here, keeping ArrayList name as list.

2. Declare a Scanner class object, for accpeting input as Scanner scanner = new Scanner(System.in);

3. Accept the input from user using the scanner.nextLine() function for String, which is line

4. Using the split() method, we will split the words, of the string and store them, separately in List using the add() method.

5. We will implement a for loop, for the step-4.

.

PART-3: MAIN LOGIC OF PROGRAM (WHILE LOOP)

The following code segment, gives the details about this part.

        //String for storing final output word
        String originalWord = "";
        
        //Until ArrayList size reaches zero
        while(list.size() > 0)
        {
             //Part-3.1
             //Part-3.2
             //Part-3.3
        }
EXPLAINATION

1. Create a String originalWord, to store the final output string value.

2. Declare a while loop, that will run Until ArrayList size reaches zero.

3. Inside the while loop we will have three parts, 3.1, 3.2, 3.3 discussed further.

.

PART-3.1: If ArrayList has one element (Inside While Loop)

The following code segment, gives the details about this part.

            int i=0;
            int flag=0;
            
            //If ArrayList has one element
            if(list.size() == 1){
                StringBuffer s = new StringBuffer(list.get(0));
                s.deleteCharAt(0);
                originalWord += s;
                break;
            }
EXPLAINATION

1. Creating two variables i and flag, for acessing list elements.

2. The code will execute if list.size() == 1.

3.As we cannot alter a String, so we will use StringBuilder object, which is mutable in nature.

4. We will fetch the only remaining element from the list and delete the first character of it, using the s.deleteCharAt(0); statement.

5. Merge the s into the original word and exit the while loop.

.

PART-3.2: For reassembling words (Inside While Loop)

The following code segment, gives the details about this part.

            //If last character of a string matches with the 
            //first character of string pointed by i, i.e., current String
            String current = list.get(i);
            for(int j=i+1; j<list.size(); j++)
            {
                int len = list.get(j).length();
                if(current.charAt(0) == list.get(j).charAt(len-1))
                {
                    flag = 1;
                    
                    //Deleting the first character of current string
                    StringBuffer s = new StringBuffer(current);
                    s.deleteCharAt(0);
                    String second = list.get(j);
                    
                    list.remove(i);
                    list.remove(j-1);
                    
                    //If size of ArrayList is greater than 2
                    if(list.size()>2)
                    {
                        list.add(second + s);
                    }
                    else
                    {
                        originalWord += (second + s);
                    }
                    break;
                }
            }
EXPLAINATION

1. Creating a String variable current to store the i-th element of the ArrayList list.

2. The current will always contain the first element of list.

3. Traversing the list from next position, from i+1 until list.size(), using a for loop.

4. Calculating the length of the other string fetched using get(j), and storing in len variable.

5. Using if(current.charAt(0) == list.get(j).charAt(len-1)) statement to match that, if first character of the current string matches with the last character of the traversed string.

If matches proceed to step-6. Else the part-3.2 is skipped.

6. Make flag=1, signifying that a match was found. As we cannot alter a String, so we will use StringBuilder object, which is mutable in nature. Deleting the first character of current string, using s.deleteCharAt(0);

7. Storing the other string in a variable second as, String second = list.get(j);

8. Removing the two elements from the list using the remove() function, as we will merge them.

9. If the size of ArrayList is greater than 2, we will add the merged string back to the list. This is done, in order to merge it with other elements. The same is done using list.add(second + s);

10. Else, add the merged string to the final word, i.e, using the originalWord += (second + s); statement.

11. Break, the for loop to proceed to next iteration of while loop.

.

PART-3.3: For joining words for which no 'match' is found (Inside While Loop)

The following code segment, gives the details about this part.

            //If last character of a string matches does not matches 
            //with the first character of string pointed by i, i.e., current String
            if(flag == 0)
            {
                StringBuffer s = new StringBuffer(current);
                s.deleteCharAt(current.length()-1);
                originalWord += s;
                list.remove(i);
            }
.EXPLAINATION

1. The code will execute if flag is 0.

2. flag=0, will mean that last character of a string matches does not matches with the first character of string pointed by i, i.e., current String.

3.As we cannot alter a String, so we will use StringBuilder object, which is mutable in nature.

4. We will fetch the only remaining element from the list and delete the last character of it, using the s.deleteCharAt(current.length()-1); statement.

5. Merge the s into the original word.

6. Also, we will use the statement list.remove(i), to remove the current string from the list.

.

PART-4: PRINTING THE FINAL STRING

The following code segment, gives the details about this section.

        //Printing the final string        
        System.out.println("Word is:: " + originalWord);
        scanner.close();
    }
}
.EXPLAINATION

1. Using the System.out.println() we will print the final string to console.

2. Also, close the Scanner class object, using close() method.

.

.

JAVA CODE (COMBINED FINAL CODE)

The following is the final version of code.

import java.util.*;

public class Reassemble
{
    public static void main(String[] args)
    {
        
        //Accepting the input from the user
        List<String> list = new ArrayList<String>();
        Scanner scanner = new Scanner(System.in);
        String line = scanner.nextLine();
        String[] words = line.split(" ");
        
        //Storing the words of the input string separately
        for(String word : words)
        {
            list.add(word);
        }

        //String for storing final output word
        String originalWord = "";
        
        //Until ArrayList size reaches zero
        while(list.size() > 0)
        {
            int i=0;
            int flag=0;
            
            //If ArrayList has one element
            if(list.size() == 1){
                StringBuffer s = new StringBuffer(list.get(0));
                s.deleteCharAt(0);
                originalWord += s;
                break;
            }
            
            //If last character of a string matches with the 
            //first character of string pointed by i, i.e., current String
            String current = list.get(i);
            for(int j=i+1; j<list.size(); j++)
            {
                int len = list.get(j).length();
                if(current.charAt(0) == list.get(j).charAt(len-1))
                {
                    flag = 1;
                    
                    //Deleting the first character of current string
                    StringBuffer s = new StringBuffer(current);
                    s.deleteCharAt(0);
                    String second = list.get(j);
                    
                    list.remove(i);
                    list.remove(j-1);
                    
                    //If size of ArrayList is greater than 2
                    if(list.size()>2)
                    {
                        list.add(second + s);
                    }
                    else
                    {
                        originalWord += (second + s);
                    }
                    break;
                }
            }
            
            //If last character of a string matches does not matches 
            //with the first character of string pointed by i, i.e., current String
            if(flag == 0)
            {
                StringBuffer s = new StringBuffer(current);
                s.deleteCharAt(current.length()-1);
                originalWord += s;
                list.remove(i);
            }
        }
        
        //Printing the final string
        System.out.println("Word is:: " + originalWord);
        scanner.close();
    }
}



