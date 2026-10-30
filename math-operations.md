# Math Operators 
- Since we have variables, it is totally normal to expect that we would do some calculations. This is where the math side of Javascript comes in.

## Terms
1. _Operand_ - are what the operations appied to. Like numbers or variables
2. _Operator_ - addition, subtraction, etc. An operator can also be _unary_, meaning it is doing an operation with one variable. Like `-` which reverses the sign of a number. `!` is also unary. It reverses the boolean value of a variable.
    The following math operations are supported:

        - Addition +,
        - Subtraction -,
        - Multiplication *,
        - Division /,
        - Remainder %, 
        Note: if the right value is higher than the left value, this operator returns the left value instead.
        - Exponentiation **.

### Types of Number
- So in programming, there are different terms to describe a number. Below are some examples
    1. Integers - this numbers are all negative number, zero, and positive number
    2. Float - this numbers are similar to integers but they also have a decimal point.

## Number object
- This is an object that contains multiple methods that would help us manipulate any numbers. Below are some example:
    1. **Convert strings to numbers.**
        ```
            let a = "10";
            let b = 10;
            let sum = Number(a) + b;
            console.log(sum) //answer is 10
        ```
        Notice how we converted variable `a` before doing an operation. If we did not convert it, the answer would be `sum = "1010";` because of _type conversion_. Unlike other operations, the `+` operator has many function. One of those is `concatenation`, which is joining of two `strings`. The sum operator thinks by default that we are _joining_ two variable instead of doing a sum operation. That is why we need to convert any string to a number before doing a sum operation. Alternatively, adding a "+" before the variable converts that string variable into a number
        ```
            let a = "10";
            let b = 10;
            let sum = +a + b;
            console.log(sum) //answer is 10
        ```
        Although this might be confusing to read. Another thing that you might find useful is the `typeof` command. It shows you what type of data you are dealing with.
            ```
                let a = "10";
                console.log(typeof a) // string
            ``` 

    2. **.toFixed()**
    This is a method to limit how many decimal places we want to be displayed.
        ```
            let pi = 3.14156;
            console.log(pi.toFixed(2))// 3.14
        ```

## Increment and Decrement
- You will find yourself wanting to increase or decrease the value of variable because of a certain scenario. We do this by using the increment syntax (++) and decrement syntax (--). Note: You can only use this on a variable. Incrementing/Decrementing a number directly will lead to error.
    ```
        3++ // this will produce an error
        let guessCount = 10;
        guestCount++
        console.log(guessCount) // this will pring 11
    ```
- Sometime you will see scenarios where increment/decrementing syntax will look like this. `++guessCount;`. This still does the same thing. Increase the count of `guestCount`. But is a difference between the two.

1. `guessCount++` - this will increase the number by one but not immediate
    ```
        let guessCount = 10;
        console.log(guestCount++)
        // this will still pring 10. Although the value of it already changed, you wont see it until you print the guessCount again
        console.log(guessCount) // 11
        
    ```
2. `++guessCount` - this will increase the number and show it immediately
    ```
        let guessCount = 10;
        console.log(++guessCount) // This will immediately print 11
    ```

## Comparison Operators
- Sometimes you will need evaluate some variable if they meet a certain condition. This is where the comparison operators comes in.

- == vs ===
    - == - this will evaluate if both variables or data is equal. regardles of data types.
    ```
        let a = "10";
        let b = 10;
        let c = a == b;
        console.log(c) // This will print true
    ```
- === - this will evaluate if both variables or data is equal and if the data type is also the same.
    ```
        let a = "10";
        let b = 10;
        let c = a === b;
        console.log(c) // This will print false
    ```
- This became `false` because the data type `a`(string) and `b`(number) are different. Even though technically, they are the same value. You can check this by console logging the `typeof` of the variables.
Fun fact: You can convert booleans(true / false) into a number. Doing `Number(true / false)` will print `1` or `0` respectively. Same goes with `+true / +false` will print 1 or 0.

## && Operator
- This is the AND operator. In programming, this will return true if both operands are truthy and false if not.
    ```
       alert( true && true );   // true
       alert( false && true );  // false
       alert( true && false );  // false
       alert( false && false ); // false 
    ```

- This operator finds the first falsy value. And if it did not find any falsy values, it would return the last operand.
   ```
        // if the first operand is truthy,
        // AND returns the second operand:
        alert( 1 && 0 ); // 0
        alert( 1 && 5 ); // 5
    
        // if the first operand is falsy,
        // AND returns it. The second operand is ignored
        alert( null && 5 ); // null
        alert( 0 && "no matter what" ); // 0      
    ```
- The AND && operator does the following:

    1. Evaluates operands from left to right.
    2. For each operand, converts it to a boolean. If the result is false, stops
    3. and returns the original value of that operand.
If all operands have been evaluated (i.e. all were truthy), returns the last operand.
In other words, AND returns the first falsy value or the last value if none were found.

## Reference
[Javascript.info](https://javascript.info/operators)
[Logical Operators](https://javascript.info/logical-operators)







