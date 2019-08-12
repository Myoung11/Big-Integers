 /* Assisted by and Assisted line numbers: Dr.Su lines 235, 51-151, 382-440 (Assignment 9 driver)
 
 * Matthew Young
 
 * This program will perform mathematical operations on big integers
 
 */

//Modified from textbook Larry Nyhoff,  ADTs, Data Structures, and Problem Solving
//with C++, 2nd ed., Prentice-Hall, 2005.

/*-- BigInt.cpp-------------------------------------------------------------
 This file implements BigInt member functions.
 --------------------------------------------------------------------------*/

#include <iostream>
#include <cmath>
using namespace std;

#include "BigInt.h"



//--- Definition of read()
void BigInt::read(istream & in)
{
    static bool instruct = true;
    if (instruct)
    {
        cout << "Enter " << DIGITS_PER_BLOCK << "-digit blocks, separated by "
        "spaces.\nEnter a negative integer in last block to signal "
        "the end of input.\n\n";
        instruct = false;
    }
    short int block;
    const short int MAX_BLOCK = (short) pow(10.0, DIGITS_PER_BLOCK) - 1;
    for (;;)
    {
        in >> block;
        if (block < 0) return;
        
        if (block > MAX_BLOCK)
            cerr << "Illegal block -- " << block << " -- ignoring\n";
        else
            myList.push_back(block);
    }
}




//--- Definition of display()
void BigInt::display(ostream & out) const
{
    int blockCount = 0;
    const int BLOCKS_PER_LINE = 20;   // number of blocks to display per line
    
    for (list<short int>::const_iterator it = myList.begin(); ; )
    {
        out << setfill('0');
        if (blockCount == 0)
            out << setfill(' ');
        
        if (it == myList.end())
            return;
        
        out << setw(3) << *it;
        blockCount++ ;
        
        it++;
        if (it != myList.end())
        {
            out << ',';
            if (blockCount > 0 && blockCount % BLOCKS_PER_LINE == 0)
                out << endl;
        }
    }
}



//--- Definition of operator+()
BigInt BigInt::operator+(BigInt addend2)
{
    BigInt sum;
    short int first,        // a block of 1st addend (this object)
    second,                 // a block of 2nd addend (addend2)
    result,                 // a block in their sum
    carry = 0;              // the carry in adding two blocks
    
    list<short int>::reverse_iterator // to iterate right to left
    it1 = myList.rbegin(),         //   through 1st list, and
    it2 = addend2.myList.rbegin(); //   through 2nd list
    
    while (it1 != myList.rend() || it2 != addend2.myList.rend())
    {
        if (it1 != myList.rend())
        {
            first = *it1;
            it1++ ;
        }
        else
            first = 0;
        if (it2 != addend2.myList.rend())
        {
            second = *it2;
            it2++ ;
        }
        else
            second = 0;
        short int temp = first + second + carry; // Equation for adding integerss
        result = temp % 1000;
       
        carry = temp / 1000;
       
        sum.myList.push_front(result);
    }
    
    if (carry > 0)
        sum.myList.push_front(carry);
    
    return sum;
}

//--- Definition of operator>()

bool BigInt::operator>(BigInt addend5)
{
    BigInt sum;
    bool compare;           // Bool to compare both integers
    short int first,        // a block of 1st addend (this object)
    second;                // a block of 2nd addend (addend2)
    
    list<short int>::reverse_iterator // to iterate right to left
    it1 = myList.rbegin(),         //   through 1st list, and
    it2 = addend5.myList.rbegin(); //   through 2nd list
    
    while (it1 != myList.rend() || it2 != addend5.myList.rend())
    {
        if (it1 != myList.rend())
        {
            first = *it1;
            it1++ ;
        }
        else
            first = 0;
        
        
        if (it2 != addend5.myList.rend())
        {
            second = *it2;
            it2++ ;
        }
        else
            second = 0;
    
        if (first - second < 0){ // Equation for comparison
            compare = false;
        }
        
        if (first - second > 0){ // Equation for comparison
            compare = true;
        }
    }
        return compare;
}


BigInt BigInt::operator-(BigInt addend3)
{
    BigInt sum;
    short int first,        // a block of 1st addend (this object)
    second,                 // a block of 2nd addend (addend2)
    result,                 // a block in their sum
    carry = 0;              // the carry in adding two blocks
    
    list<short int>::reverse_iterator // to iterate right to left
    it1 = myList.rbegin(),         //   through 1st list, and
    it2 = addend3.myList.rbegin(); //   through 2nd list
    
    while (it1 != myList.rend() || it2 != addend3.myList.rend())
    {
        if (it1 != myList.rend())
        {
            first = *it1;
            it1++ ;
        }
        else
            first = 0;
        if (it2 != addend3.myList.rend())
        {
            second = *it2;
            it2++ ;
        }
        else
            second = 0;
        
        short int temp = first - second + carry; //Equation for subtraction
        result = temp % 1000;
        
        if (result < 0){
        carry = temp + 1000;                // Equation for negative numbers and the carry variable
            sum.myList.push_front(carry);
            carry = 0;
        }
       
        
        if (result > 0){
        sum.myList.push_front(result);
        }
    }
    
    if (carry > 0)
        sum.myList.push_front(carry);
    
    if (first < second) { // Returns 0 if the first integer is smaller than the second integer
        result = 0;
        sum.myList.push_front(result);
    }
    
    return sum;
}

//--- Definition of operator-()

//--- Definition of operator*()
BigInt BigInt::operator*(BigInt addend4)
{
    BigInt sum;
    short int first,        // a block of 1st addend (this object)
    second,                 // a block of 2nd addend (addend4)
    result,                 // a block in their sum
    carry = 0;              // the carry in adding two blocks
    
    list<short int>::reverse_iterator // to iterate right to left
    it1 = myList.rbegin(),         //   through 1st list, and
    it2 = addend4.myList.rbegin(); //   through 2nd list
    
    while (it1 != myList.rend() || it2 != addend4.myList.rend())
    {
        
        if (it1 != myList.rend())
        {
            first = *it1;
            it1++ ;
        }
        else
            first = 0;
        if (it2 != addend4.myList.rend())
        {
            second = *it2;
            it2++ ;
        }
        else
            second = 0;
        
       
        int temp = (first * second) + carry;
       
        result = temp % 1000;
    
        carry = temp / 1000;
       
        sum.myList.push_front(result);
        sum.myList.push_front(carry);
        
    }
    
    //if (carry > 0)
        //sum.myList.push_front(carry);
    
    return sum;
}












//cmpsc122 Assignment 6
// Please do not modify this file!
// --- Program to test BigInt class.
// Modified from textbook Larry Nyhoff,  ADTs, Data Structures, and Problem Solving
// with C++, 2nd ed., Prentice-Hall, 2005.

#include <iostream>
using namespace std;

#include "BigInt1.h"

int main()
{
    
    //  However, you are not allowed to modify the following codes.
    
    char response;
    do
    {
        BigInt number1, number2;
        cout <<"Enter a big integer:\n";
        cin >> number1;
        cout <<"Enter another big integer:\n";
        cin >> number2;
        
        // original one: test the operation +
        cout << "The sum of\n\t"
        << number1 << " + " << number2
        << "\nis\n\t" << number1 + number2 << endl;
        
     //1. test the operation >
     cout << "\nThe bigger number of\n\t"
     << number1 << "\nand\n\t" << number2
     << "\nis\n\t" << ((number1 > number2) ? number1 : number2) << endl;
        
        
        // 2. test the operation -
        cout << "\nThe subtraction of\n\t"
        << number1 << " - " << number2
        << "\nis\n\t" << number1 - number2 << endl;
        
        
        // 3.(bonus) test the operation *
        
        
        // comment the following out if you don't do 3.
        cout << "\nBONUS part:" << endl;
        cout << "The multiplication of\n\t"
        << number1 << " * " << number2
        << "\nis\n\t" << number1 * number2 << endl;
     
        
        cout << "\nAdd more integers (Y or N)? ";
        cin >> response;
    }
    while (response == 'y' || response == 'Y');
    
    return 0;
}
