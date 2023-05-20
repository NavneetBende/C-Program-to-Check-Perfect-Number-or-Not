# C-Program-to-Check-Perfect-Number-or-Not

Perfect number in C
Basically, a perfect number is a positive number that is equal to the sum of all its divisors(excluding itself) excluding itself.

We have to find all divisors of that number and find their sum if the sum of divisors is equal to the number. We will look at different ways of coding Perfect Number in C.

Ex:- Take a number:  6
6 is a perfect number as 1 + 2 + 3 = 6.
Ex:- Take a number: 28

28 is a perfect number as 1 + 2 + 4 + 7 + 14 = 28
perfect number or not in c
Methods to find 
Method 1: Using For Loop, Linear traversal between [1, num -1] to find factors
Method 2: Using While Loop, Linear traversal between [1, num – 1] to find factors
Method 3: Linear traversal between [1, num/2] to find factors
Method 4: Using Function and Linear traversal between [1, num/2] to find factors
Method 5: Uses recursion in C
Method 6: Linear traversal between [1, √num] but using a pair-based approach
Perfect Number in C
Related Pages
Finding Prime Factors of a number

Strong number

Perfect number

Perfect Square

Automorphic number

Harshad number

Method 1 (For Loop)
For a user input num

Using loop in the iteration of (i) traverse from [1, num-1]
Add all (i) that divide num perfectly (num % i == 0)
Method 1 C Program:-
Lets have a look at the program below –

Run
#include <stdio.h>

int main ()
{
    int num = 28, sum = 0;
    // iteratively check for all numbers in range [1, 27]
    for(int i = 1; i < num; i++){
        // check if i is a divisor, if yes then add to sum
        if(num % i == 0)
            sum = sum + i;
    }
    
    if(sum == num)
        printf("%d is a perfect number",num);
    else
        printf("%d is not a perfect number",num);
    

}
// Time complexity: O(N)
// Space complexity: O(1)
Output:-
28 is a perfect number
Method 2 C Program:-
Lets have a look at the program for perfect number in C below –

Run
#include <stdio.h>

int main ()
{
    int num = 28, sum = 0, i = 1;
    
    // iteratively check for all numbers if they are divisors
    while(i < num)  
    {
        // check if i is a divisor, if yes then add to sum
        if(num % i == 0)  
            sum = sum + i;  
        i++;  
    }  
    
    if(sum == num)
        printf("%d is a perfect number",num);
    else
        printf("%d is not a perfect number",num);
    

}
// Time complexity: O(N)
// Space complexity: O(1)
Method 2 (While Loop)
Uses the same logic as method 1.1 but rather than a for loop uses a while loop.

Output:-
28 is a perfect number
Method 3 In Range [1, num/2]
This method uses optimization that all divisors of the number(excluding itself) can be found in the range [1, num/2]

Method 3 C Program:-
Lets have a look at the program for perfect number in C below –

Run
#include <stdio.h> 

int main ()
{
    int num = 28, sum = 0, i = 1;
    
    // all divisors of the numbers (excluding the number itself)
    // can be found before num/2
    // note we will need to use '=' sign as for even numbers
    // like 28, half of the number i.e 14 will also be the divisor    
    while(i <= num/2)  
    {
        // check if i is a divisor, if yes then add to sum
        if(num % i == 0)  
            sum = sum + i;  
        i++;  
    }  
    
    if(sum == num)
        printf("%d is a perfect number",num);
    else
        printf("%d is not a perfect number",num);
    

}
// Time complexity: O(N)
// Space complexity: O(1)
Output:-
28 is a perfect number
Method 4 C Program:-
Lets have a look at the program for perfect number in C below –

Run
#include <stdio.h>

int isPerfect(int num)
{
    int sum = 0;
    
    // all divisors of num(excluding itself) can be found before num/2
    // remember put = sign as for even numbers like 28
    // half of it i.e. 14 would be divisor too e
    for (int i = 1; i <= num/2; i++){
        if (num % i == 0)
            sum = sum + i;
        }

    if (sum == num)
        return 1;

    return 0;
}
int main ()
{
    int num = 28, sum = 0, i = 1;
    
    if(isPerfect(num))
        printf("%d is a perfect number",num);
    else
        printf("%d is not a perfect number",num);
    

}
// Time complexity: O(N)
// Space complexity: O(1)
Method 4 In Range [1, num/2] using a function
In this method, we use a function.

This method also uses optimization that all divisors of the number(excluding itself) can be found in the range [1, num/2]

Output:-
28 is a perfect number
Method 5
This method uses recursion in C

Method 5 C Program:-
Lets have a look at the program for perfect number in C below –

Run
#include <stdio.h>

static int sum = 0;
int getSumDivisors(long num, int i)
{
    // since, all factors can be found will num/2
    // we will only check in this range
    if(i <= num/2)
    {
        if(num % i ==0)
            sum = sum + i;

        i++;
        // recursively call isPerfect
        getSumDivisors(num, i);
    }

    //returns the sum
    // when i becomes > num/2
    return sum;
}

int main ()
{
    int num = 28;
    
    if(getSumDivisors(num, 1) == num)
        printf("%d is a perfect number",num);
    else
        printf("%d is not a perfect number",num);
    
    return 0;
}
// Time complexity: O(N)
// Space complexity: O(1)
// Auxiliary Space complexity: O(N) due to function call stack
Output:-
28 is a perfect number
Method 6
This method uses observations that all factors come in pairs.

All Factors come in pairs
For n = a * b (For each a there exists a unique b)

Example 1 : 100
(1,100), (2, 50), (4, 25), (5, 20), (10, 100)

Example 2 : 28
(1, 28), (2, 14), (4, 7)
Note : We will need to ignore pair of 1. As it will be the number itself.
Shorten the Loop
We can shorten the loop running between [1, num] to [1, √num]

Since we will find all pairs before √num (n = sqrt(n) * sqrt(n))

Example: For 28, all pairs can be found before √28 = 5.2
Method 6 C Program:-
Run
#include <stdio.h>
#include <math.h>

int main ()
{
    int num = 28, sum = 0;
    
    for(int i = 1; i < sqrt(num); i++)
    {
        if (num % i == 0)
        {
            // For num : (1, num) will always be pair of divisor
            // acc to def., we must ignore adding num itself as divisor
            // when calculating for perfect number
            if(i == 1)
                sum = sum + i;
            
            // Example For 100 (10,10)  will be one pair
            // But, we should add value to the sum just once
            else if(i == num/i)
                sum = sum + i;
            
            // add both pairs as divisors
            // For any divisor i, num/i will also be a divisor
            else
                sum = sum + i + num/i;
        }
    }
    
    if(sum == num)
        printf("%d is a perfect number",num);
    else
        printf("%d is not a perfect number",num);
    

}
// Time complexity: O(sqrt(N))
// Space complexity: O(1)
Output:-
28 is a perfect number
