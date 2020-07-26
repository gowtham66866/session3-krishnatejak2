# **Numeric Types** 

## **Objective :**

    1. Base conversion from decimal base to any given base with out using python in-built functions
    for ex : 
        dec(10) --> bin(1010)
        dec(10) --> hex(a)
        dec(10) --> 5(20)    
    2. Emulate ISCLOSE functionality of default python to compare floats with out using any of the default int, float, etc classes along with relative and absolute tolerances
    3. Emulate TRUNC function of default python with out using any of default int, float, etc classes
    4. Enumlate ROUND fucntion of default python with out using any of the default int, float, etc classes
   
## **Functions :**

### encoded_from_base10 

    This function returns a string encoding in the "base" for the the "number" using the "digit_map"
    Conditions that this function must satisfy:
    - 2 <= base <= 36 else raise ValueError
    - invalid base ValueError must have relevant information
    - digit_map must have sufficient length to represent the base
    - must return proper encoding for all base ranges between 2 to 36 (including)
    - must return proper encoding for all negative "numbers" (hint: this is equal to encoding for +ve number, but with - sign added)
    - the digit_map must not have any repeated character, else ValueError
    - the repeating character ValueError message must be relevant
    - you cannot use any in-built functions in the math module
    - respective errors are thrown with some condition checks

**Idea :**

     The following formula comes in handy when doing the calculations 
        n = d * (n // d) + (n % d)

    if we need to convert a number say 10 to binary which is of base 2 and has a encoding map of '01', that is any number has to be represented with only 0 or 1, then we do the following steps:
        10 = 2 * (10 // 2) + (10 % 2)
    the above step has 2 important parts the div part and the modulo part
    The result of modulo is used as the position holder in the new base and the steps are looped over the result of the div operator till it reaches 0


### float_equality_testing
    This function emulates the isclose method from the math module
        We are going to assume:
        - relative_tolerance = 1e-12
        - absolute_tolerance = 1e-05

**Idea :**  

    The relative_tolerance is the maximum allowed difference between value a and b
    The absolute_tolerance is used to compare values near 0. The value must be at least 0
    
    It uses the following formula and returns the boolean value of the comparison:
        abs(a-b) <= max(rel_tol * max(abs(a), abs(b)), abs_tol)

### manual_truncation_function
    This function emulates python's MATH.TRUNC method. 
    It ignores everything after the decimal point.
    It must check whether f_num is of correct type before proceed. 
    We can not use inbuilt constructors like int, float, etc

    It is like finding the quotient when dividing 2 numbers, provided we take care of the negatives

### manual_rounding_function
    This function emulates python's inbuild round function. 
    We are not allowed to use round function, but expected to write one manually.

    It is the same as above as we do not need to provide precision in this function(yet!)

### rounding_away_from_zero
    This function implements rounding away from zero as covered in the class
    Desperately need to use INT constructor? Well we can't.
    Hint: use FRACTIONS and extract numerator.