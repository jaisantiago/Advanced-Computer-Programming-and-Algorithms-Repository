### Created by: Jai M. Santiago | 2ECE-B
# Advanced-Computer-Programming-and-Algorithms-PA-1
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
#### This concludes the Program Assignment 1 showcase. If you would like to access the file and see the code yourself, please click this link: https://github.com/jaisantiago/Advanced-Computer-Programming-and-Algorithms-Repository/blob/main/ECE2112_PA1_Santiago%2C%20Jai.ipynb



# Advanced-Computer-Programming-and-Algorithms-PA-2
#### In this part, the problems and solutions for Programming Assignment 1 for the course "Advanced Computer Programming and Algorithms" will be explained and presented given the topic, Module 2 - Numpy.
## A. REPRODUCIBLE NORMALIZATION PROBLEM
#### Problem: Create a reproducible random 5 × 5 integer ndarray named X. Normalize the complete array using: Z = X - x̄/ σ Where x̄ is the mean of all 25 elements and σ is their population standard deviation as returned by NumPy’s default std() call. Store the normalized array in X_normalized.
#### Clear Condition: The normalized mean must be 0 and the normalized standard deviation must be 1.
#### Solution: The suggested two statements from the instructions were used to generate 25 random numbers from 1 to 100 then resize them into a 5 x 5 array.
```
np.random.seed(2112)
X = np.random.randint(10, 101, size=(5, 5))
X
```
#### After that, modeled after the given equation of Normalizing, the X Normalize code was created ```X_normalized = (X - X.mean())/ X.std()```. Lasty, ```X_normalized.mean()``` and ```X_normalized.std()``` was used to get its mean and standard deviation, respectively, all while using ```np.round``` to round them into whole numbers. 

```
mean = np.round(X_normalized.mean(), 1)
mean
np.float64(0.0)
```
```
standard_deviation = np.round(X_normalized.std(), 1)
standard_deviation
np.float64(1.0)
```
## B. CUBES DIVISIBLE BY 4 PROBLEM
#### Problem: Using NumPy, create the first 100 positive integers, cube every element, and reshape the result into a 10 × 10 ndarray named C. Thus, C begins with 1^3 and ends with 100^3. Use a Boolean condition on C to obtain every cubed value divisible by 4. Store the selected values in div_by_4. Preserve NumPy’s normal row-major selection order.
#### Clear Condition: A correct solution has 50 selected elements; the first is 8 and the last is 1,000,000.
#### Solution: ```np.arange(1, 101)``` was used to create an array that is automatically arranged in an increasing order from 1 to 100 while ```C**3``` cubes every element in C. Then, ```C = C.reshape(10,10)``` takes all of this and reshapes it into a 10 x 10 array. Finally, to find the elements divisible by 4, the Boolean condition ```div_by_4 = C[C%4 == 0]``` was utilized by first getting the modulo of each element by 4, and if this is 0, then the element is divisible by 4.
```
div_by_4 = C[C%4 == 0]
div_by_4
array([      8,      64,     216,     512,    1000,    1728,    2744,
          4096,    5832,    8000,   10648,   13824,   17576,   21952,
         27000,   32768,   39304,   46656,   54872,   64000,   74088,
         85184,   97336,  110592,  125000,  140608,  157464,  175616,
        195112,  216000,  238328,  262144,  287496,  314432,  343000,
        373248,  405224,  438976,  474552,  512000,  551368,  592704,
        636056,  681472,  729000,  778688,  830584,  884736,  941192,
       1000000])
```
```
div_by_4.size
50
```
## C. ABOVE-MEAN SQUARES PROBLEM
#### Problem: Create a 6 × 6 ndarray named S containing the squares of the first 36 positive integers in increasing row-major order. Compute the mean of all elements of S and store it in S_mean. Then use Boolean filtering to select only the elements strictly greater than S_mean. Store these values in above_mean.
#### Clear Condition: A correct solution has 15 selected elements; the first is 484 and the last is 1296.
#### Solution: The first call is to create an array with the first 36 cubed integers which can be arranged and simultaneously cubed using ```S = (np.arange(1, 37))**2```. Afterwards, the function ```S.mean()``` was chosen to get the mean of all of its elements, then this mean would be compared with each element to find whether or not they are greater than this with the help of the Boolean condition ```above_mean = S[S>S_mean]```.
```
above_mean = S[S>S_mean]
above_mean
array([ 484,  529,  576,  625,  676,  729,  784,  841,  900,  961, 1024,
       1089, 1156, 1225, 1296])
```
```
above_mean.size
15
````
#### This concludes the Program Assignment 2 showcase. If you would like to access the file and see the code yourself, please click this link: https://github.com/jaisantiago/Advanced-Computer-Programming-and-Algorithms-Repository/blob/main/ECE2112_PA2_Santiago%2C%20Jai.ipynb


# Advanced-Computer-Programming-and-Algorithms-PA-3
#### In this section, the problems and solutions for Programming Assignment 3 which covers the topic, Module 3 - Pandas, will be discussed.
## A. POSITIONAL AND LABEL-BASED SLICING
#### Problem: (a) Display the shape and complete list of column names of cars. (b) Then, using positional slicing, create cars_6_to_10 containing rows 6 through 10 of the dataset, where the first data row is row 1. (c) From cars 6 to 10, display only the columns Model, mpg, cyl, hp, and gear, in that order.
#### Clear Condition: The row selection in part (b) must use iloc; the column selection in part (c) must use column labels.
#### Solution: Before anything, the file cars.csv was uploaded into the files of the notebook. Then to display its content, ```cars = pd.read_csv('cars.csv')``` was used. Then, ```cars.shape``` was utilized to get the shape of the table. 
```
cars.shape
(32, 12)
```
#### Next, to specifically take rows 6 through 10 with row 0 being row 1 in the data row, a slicing function ```cars_6_to_10 = cars.iloc[5:10]``` was used.
```
cars_6_to_10 = cars.iloc[5:10]
cars_6_to_10
| Model     | mpg  | cyl | disp  | hp  | drat | wt   | qsec  | vs | am | gear | carb |
|-----------|------|-----|-------|-----|------|------|-------|----|----|------|------|
| Valiant   | 18.1 | 6   | 225.0 | 105 | 2.76 | 3.46 | 20.22 | 1  | 0  | 3    | 1    |
| Duster 360| 14.3 | 8   | 360.0 | 245 | 3.21 | 3.57 | 15.84 | 0  | 0  | 3    | 4    |
| Merc 240D | 24.4 | 4   | 146.7 | 62  | 3.69 | 3.19 | 20.00 | 1  | 0  | 4    | 2    |
| Merc 230  | 22.8 | 4   | 140.8 | 95  | 3.92 | 3.15 | 22.90 | 1  | 0  | 4    | 2    |
| Merc 280  | 19.2 | 6   | 167.6 | 123 | 3.92 | 3.44 | 18.30 | 1  | 0  | 4    | 4    |
```
#### Lastly, to only display Model, mpg, cyl, hp, and gear in cars_6_to_10, slicing was used once more but there is no specific index as we wanted to take all of the rows, but since we want a specific data for the columns, ```['Model', 'mpg','cyl','hp','gear']``` was input in the code.

```
cars_6_to_10.loc[:,['Model', 'mpg','cyl','hp','gear']]
| Model      | mpg  | cyl | hp  | gear |
|------------|------|-----|-----|------|
| Valiant    | 18.1 | 6   | 105 | 3    |
| Duster 360 | 14.3 | 8   | 245 | 3    |
| Merc 240D  | 24.4 | 4   | 62  | 4    |
| Merc 230   | 22.8 | 4   | 95  | 4    |
| Merc 280   | 19.2 | 6   | 123 | 4    |
```

## B. MODEL LOOKUP
#### Problem: Use Boolean indexing on the Model column to answer both requests. 
 (a) Display the complete row for Toyota Corolla.                                                          
 (b) For Pontiac Firebird, display only Model, mpg, hp, and wt
#### Solution: Boolean indexing was used to create the line of codes for both a and b where in a the condition to find the row was ```cars['Model']=='Toyota Corolla'```, and in b it was ```(cars['Model']=='Pontiac Firebird')``` while specifying the columns ```['Model','mpg', 'hp','wt']```, displaying only these in the final table.
```
toyota = cars.loc[cars['Model']=='Toyota Corolla']
toyota
| Model          | mpg  | cyl | disp | hp | drat | wt    | qsec | vs | am | gear | carb |
|----------------|------|-----|------|----|------|-------|------|----|----|------|------|
| Toyota Corolla | 33.9 | 4   | 71.1 | 65 | 4.22 | 1.835 | 19.9 | 1  | 1  | 4    | 1    |
```
```
pontiac = cars.loc[(cars['Model']=='Pontiac Firebird'), ['Model','mpg', 'hp','wt']]
pontiac
| Model           | mpg  | hp  | wt    |
|-----------------|------|-----|-------|
| Pontiac Firebird | 19.2 | 175 | 3.845 |
```


## C. MULTI-MODEL SUBSETTING
#### Problem: Create a DataFrame named selected_cars containing only the records for three models: Datsun 710, Lotus Europa, and Ferrari Dino. For these records, retain only Model, mpg, cyl, hp, and gear. Select the rows by their model values rather than by row numbers. Display selected cars and its shape.
#### Clear Condition: The final DataFrame must contain exactly three rows and five columns.
#### Solution: Another Boolean condition was employed to get the rows asked by the problem. By using the boolean or ```|```, the rows for the models Datsun 710, Lotus Europa, and Ferrari Dino were selected. Then to get the specific their specific characteristics in the columns ```['Model','mpg','cyl','hp','gear']``` was utilized.
```
selected_cars = cars.loc[(cars['Model']=='Datsun 710') | (cars['Model']=='Lotus Europa') | (cars['Model']=='Ferrari Dino'), ['Model','mpg','cyl','hp','gear']]
selected_cars
| Model        | mpg  | cyl | hp  | gear |
|--------------|------|-----|-----|------|
| Datsun 710   | 22.8 | 4   | 93  | 3    |
| Lotus Europa | 30.4 | 4   | 113 | 5    |
| Ferrari Dino | 19.7 | 6   | 150 | 5    |
```
#### Upon checking using the code with ```selected_cars.shape```, it showed that it had three rows and five columns.
```
selected_cars.shape
(3, 5)
```

#### This concludes the Program Assignment 3 showcase. If you would like to access the file and see the code yourself, please click this link: https://github.com/jaisantiago/Advanced-Computer-Programming-and-Algorithms-Repository/blob/main/ECE2112_PA1_Santiago%2C%20Jai.ipynb

##### README File Version History:
##### Aug. 26, 2026 - created README file and uploaded PA1 output with problems and explanation
##### Sept. 2, 2026 - updated README file to include PA2 output with problems and explanation and uploaded PA2
##### Sept. 9, 2026 - updated README file to include PA3 output with problems and explanation and uploaded PA3
