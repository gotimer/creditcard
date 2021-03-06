creditcard
==========

Here is a summary of the business rules for the credit card coding exercise. A more complete description of credit card number formats is on Wikipedia (http://en.wikipedia.org/wiki/Bank_card_number), but the rules below should be considered sufficient for the exercise.

* Visa: begin with a 4, can be 13 or 16 digits long
* Mastercard: begin with a 50, 51, 52, 53, 54, or 55, must be 16 digits long
* American Express: begin with a 34 or 37, must be 15 digits long
* Discover Card: begin with 6011 or 65, must be 16 digits long
* Other cards will be 12-19 digits long. 

Assume all cards using this library use the Luhn algorithm (http://en.wikipedia.org/wiki/Luhn_algorithm) for the check digit (which is the last digit).

The Luhn algorithm works by adding the digits starting with the 2nd to last digit and moving left (towards the first digit). Double the value of the 2nd to last and then every 2nd digit from there on. If the doubled value is greater than 9, add those digits. The check digit will be the digit that when added makes the resulting sum a multiple of 10.

For example, if the card number is 4567-8901-2345-6783:

    8 x 2 -> 16 -> 7  
    7 x 1       -> 7  
    6 x 2 -> 12 -> 3  
    5 x 1       -> 5  
    4 x 2       -> 8  
    3 x 1       -> 3  
    2 x 2       -> 4  
    1 x 1       -> 1  
    0 x 2       -> 0  
    9 x 1       -> 9  
    8 x 2 -> 16 -> 7  
    7 x 1       -> 7  
    6 x 2 -> 12 -> 3  
    5 x 1       -> 5  
    4 x 2       -> 8  

The resulting sum is 7+7+3+5+8+3+4+1+0+9+7+7+3+5+8=77. The next multiple of 10 is 80, so the check digit is 80-77=3.  So the check digit on the card number 4567-8901-2345-6783 is valid.

Another example, popular test card number 4111-1111-1111-1111 is also valid:

    1 x 2 -> 2  
    1 x 1 -> 1  
    1 x 2 -> 2  
    1 x 1 -> 1  
    1 x 2 -> 2  
    1 x 1 -> 1  
    1 x 2 -> 2  
    1 x 1 -> 1  
    1 x 2 -> 2  
    1 x 1 -> 1  
    1 x 2 -> 2  
    1 x 1 -> 1  
    1 x 2 -> 2  
    1 x 1 -> 1  
    4 x 2 -> 8  
            --  
            29  

So the check digit is 1.

