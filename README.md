# Advanced-Computer-Programming-and-Algorithms-PA-1
### Created by: Jai M. Santiago | 2ECE-B
#### This part of the repository contains the Programming Assignment 1 for the course "Advanced Computer Programming and Algorithms." This goes over the three problems from Module 1, Base Computing with Python, and their solutions. 
## A. WORD ROTATION PROBLEM
#### Problem: Create a function named rotate_word() that accepts a non-empty string. Move the first character of the string to the end while keeping all remaining characters in their original order. Preserve the capitalization of every character
#### Example: ```rotate_word("python") -> "ythonp"```
#### Solution: ```text[1:]``` is used to get the remaining string characters after the first one which is ```text[0]```, then ```text[1:]``` will be concatenated before ```text[0]```.
```
def rotate_word(text): 
    word = text[1:] + text[0]
    return text
```
## B. USERNAME BUILDER PROBLEM
#### Problem: Create a function named make_username() that accepts two strings: first name and last name. The function must:
1. convert all letters to lowercase;
2. remove all spaces from the first name;
3. remove all spaces from the last name; and
4. join the processed first and last names using one period (.)
#### Example: ```make_username("Ada", "Lovelace") -> "ada.lovelace"```
#### Solution: First, both ```first_name``` and ```last_name``` are lowercased, then their spaces are removed using the replace function. Lastly, ```first_name```, ., and ```last_name``` are all concatenated to get the final result.
```
def make_username(first_name, last_name):
    first_name = first_name.lower()
    last_name = last_name.lower()
    first_name = first_name.replace(" ", "")
    last_name = last_name.replace(" ", "")
    full_name = first_name + "." + last_name
    return full_name
```
## C. BOOKEND SWAP PROBLEM
#### Problem: Create a function named swap_bookends() that accepts a list containing at least two elements. Unpack the list into three variables: 
1. first – the first element;
2. middle – a list containing everything between the first and last elements; and
3. last – the last element.
#### Using these variables, return a new list in which the first and last elements have exchanged positions. The elements in middle must remain in their original order. Do not modify the input list.
#### Example: ```swap_bookends([1, 2, 3, 4, 5, 6]) -> [6, 2, 3, 4, 5, 1]```
#### Solution: Since the line ```first, *middle, last = items``` already separates the list such that first takes the first element, last takes the last element, and middle takes the rest and turns it into a new list, half of the work is already done. All that is left is to concatenate them into the new order wherein the last and first elements are swapped.
```
def swap_bookends(items):
    first, *middle, last = items
    swapped = [last] + middle + [first]
    return swapped
```
### This concludes the end of the PA1 showcase. If you would like to access the file and see the code yourself, please click this link: https://github.com/jaisantiago/Advanced-Computer-Programming-and-Algorithms-Repository/blob/main/ECE2112_PA1_Santiago%2C%20Jai.ipynb

README File Version History:
Aug. 26, 2026 - created README file and uploaded PA1 output with problems and explanation
