# Array Methods

- This will contain methods that is related to arrays.

## Add / Remove items

1. `.push(...items)` - adds items to the end.
2. `.pop()` - removes items from the end.
3. `.unshift()` - adds item to the beginning.
4. `.shift()` - extracts an item from beginning.
5. `.splice()` - this is a multifunction method that can _insert_, _remove_, and _replace_ elements.
   - **Syntax**: `arr.splice(start[, deleteCount, elem1, ..., elemN])`
     - it modifies `arr` starting from the `start`: removes `deleteCount`elements and then inserts `elem1`, `...`, `elemN` at their place.
     - It is a _mutating_ method, meaning it changes the _original_ array.
     - `return` an array of removed elements.
   - **Deletion**

     ```JavaScript
     let arr = ["I", "study", "JavaScript"]

     arr.splice(1,1); // from index 1 remove 1 element

     console.log(arr) // ["I", "JavaScript"]
     ```

   - **Removing**

     ```JavaScript
     let arr = ["I", "study", "JavaScript", "right", "now"];

     //remove 3 first element and replace them with another
     arr.splice(0, 3, "Lets", "dance")

     console.log(arr) // now ["Let's", "dance", "right", "now"]
     ```

   - **return** the removed elements

     ```JavaScript
     let arr = ["I", "study", "JavaScript", "right", "now"];

     //removed 2 first elements
     let removed = arr.splice(0, 2)

     console.log(removed) // [ "I", "study"] returns an array of removed elements.
     ```

6. `.slice()` - this is the same as splice but simplier syntax
   - **Syntax**:
     - `arr.slice([start], [end])`
   - It **returns** a new array copying al the items from `start` to `end`(not including `end`). Both `start` and `end` can be negative. It is a `non-mutating` method, meaning it does not change the _original array_ but instead returns a new one.
   - `arr.slice()` without arguments can be use to copy the _original_ array if we want to make any changes and we do not want it to affect the _origina_ array.

     ```JavaScript
     let arr = ["I", "study", "JavaScript", "right", "now"];

     //copy the arr array and store it in copiedArr
     let copiedArr = arr.slice()

     //replace study with love
     copiedArr.splice(1,1, "love")

     console.log(arr) //["I", "study", "JavaScript", "right", "now"]

     console.log(copiedArr) // now ["I", "Love", "JavaScript" "right", "now"]
     ```

7. `.concat()` - this is a _non-mutating_ method that creates a new array
   - **Syntax**:
     - `arr.concat(arg1, arg2...)`
   - It **returns** a new array containing items from `arr`, then `arg1`, `arg2` etc. It accepts any number of arguments - either `array` or values.
   - In the example below you can see that the original values has not been modified.
   - Remember that `concat` contains the items from the variable where it is attached.

     ```JavaScript
     let arr = ["I", "study", "JavaScript", "right", "now"];
     let arr2 = ["and", "also"];
     let string1 = "mutability and non-mutability";
     let randNum = 7;


     //create an array from arr, arr2, string1m, randNum
     let concatArr = arr.concat(arr, arr2, string1, randNum)

     console.log(concatArr) //['I','study','JavaScript','right','now','and',also','mutability and non-mutability',7 ]
     console.log(arr) //  ["I", "study", "JavaScript", "right", "now"]
     console.log(arr2) // ["and", "also"]
     console.log(string1) // "mutability and non-mutability"
     console.log(randNum) // 7

     ```

## Iterate

1. `.forEach()` - this is a `non-mutating method`.
   - **Syntax**
     ```JavaScript
       arr.forEach(function(item, index, array) {
         // ... do something with an item
       });
     ```
   - This methods allows to run a function for every element of the array.
     ```JavaScript
     ["Me", "Myself", "I"].forEach((item, index, array)=> {
       console.log(`The item, '${item}', is at index: ${index}, of the array:${array}`)
     })
     //The item, 'Me', is at index: 0, of the array:Me,Myself,I
     //The item, 'Myself', is at index: 1, of the array:Me,Myself,I
     //The item, 'I', is at index: 2, of the array:Me,Myself,I
     ```
   - Take note that when assigned to a variable, the `.forEach` method _returns_ `undefined`.

     ```JavaScript
     let arr = ["Good", "Rich", "Happy"]

     let iteratedArr = arr.forEach((item)=>{
       "I am" + item
     })

     console.log(arr) // ["Good", "Rich", "Happy"]
     console.log(iteratedArr) // undefined
     ```

   - If you need to iterate over the array and store the returned result to a variable, using `.map()` or `.filter()` will be more fitting.

## Searching in array

1. `.indexOf()`/ `.lastIndexOf()` and `.includes()`
   - the methods `arr.indexOf` and `arr.includes` have similar syntax and does exactly the same thing as the string counterparts. But operate on items rather than characters. This is a _non-mutating method_.
     - `arr.indexOf(item, from)` - looks for `item` starting from index `from`, and _returns_ the index where it was found, otherwise -1.
     - `arr.includes(item, from)` - looks for `items` starting from index `from`, _returns_ `true` if found.
       - In most cases, using the first argument is enough.

         ```JavaScript
         let collection = ["Harvy" , 31, false]

         console.log(collection.indexOf("Harvy"))  // 0
         console.log(collection.indexOf(31)) // 1
         console.log(collection.indexOf(true)) // 2
         console.log(collection.indexOf("GF")) // -1

         console.log(collection.inludes("GFName")) //-1
         ```

       - Please note that indexOf uses the strict equality === for comparison. So, if we look for false, it finds exactly false and not the zero.
       - If we want to check if `item` exists in the array and don’t need the index, then `arr.includes` is preferred.

     - `arr.lastIndexIf(item, from)` - same with the `.indexOf()` but looks for from right to left.

       ```JavaScript
       let collection = ["Harvy" , 31, false]

       console.log(collection.indexOf("Harvy")); // 0
       console.log(collection.lastIndexOf("Harvy")); // 2
       ```

2. `.find()` and `.findIndex()` / `.findLastIndex()`
   - `.find(fn)`
     - The methods above allows us to find the index of a specific item. But what if we want to find an item inside an array based on a condition ? This is where the `.find(fn)` method comes in.
     - **Syntax**:
       ```JavaScript
       let result = arr.find(function(item, index, array) {
         // if true is returned, item is returned and iteration is stopped
         // for falsy scenario returns undefined
       });
       ```
     - Each item on the array is passed as an argument to the callback function.
       - `item` is the element.
       - `index` is its index.
       - `array` is the itself.
     - IF it returns `true`, the search is stopped and returns the `item`. IF nothing is found, `undefined` is returned. Meaning it returns the first match it finds.

       ```JavaScript
       let me = [
         {name: "Harvy",  isEmployed: true},
         {name: "Luci",  isEmployed: false},
         {name: "Cab",  isEmployed: true}
       ]

       let hasWork = me.find((item)=>{return item.isEmployed === true})

       console.log(hasWork) //{name: "Harvy",  isEmployed: true}
       ```

   - `.findIndex()` - this is a _non-mutating method_ that returns the index where the element was found. It has the same syntax as `.find()`. A value of `-1` is returned if nothing is found.
   - `.findLastIndex()` - same as `.findIndex()` but searches from right to left.

     ```JavaScript
     let users = [
       {id: 1, name: "John"},
       {id: 2, name: "Pete"},
       {id: 3, name: "Mary"},
       {id: 4, name: "John"}
     ];

     // Find the index of the first John
     alert(users.findIndex(user => user.name == 'John')); // 0

     // Find the index of the last John
     alert(users.findLastIndex(user => user.name == 'John')); // 3
     ```

3. `.filter()`
   - So the `.find()` methods looks for a single (first) element that makes the function return `true`. So what if we want a collection of items that makes the callback function returns `true`. This case needs the `.filter(fn)` method.
   - Syntax is similar to `.find(fn)` but it returns a new array that makes the callback function `true`, and returns an empty array if `false`. This is a _non-mutating method_

```JavaScript
let me = [
          {name: "Harvy",  isEmployed: true},
          {name: "Luci",  isEmployed: false},
          {name: "Cab",  isEmployed: true}
        ]

let unEmployedUsers = me.filter((item)=>{return item.isEmployed === false })

console.log(unEmployedUsers)
// [ { name: 'Luci', isEmployed: false } ]
```

## Transform an array

- This section will talk about method that _transform_ and _reorder_ an array.

1. `.map()` - like the `.forEach` method, it call each element of the array **but** returns the array of results. Unlike the `.forEach()` which returns `undefined`. This is a _non-mutating method_.
   - **Syntax**

   ```JavaScript
   let result = arr.map(function(item, index, array) {
     // returns the new value instead of item
   });
   ```

   - The sample below shows how we transform the element of the array into its `length`. Notice that it returned an array.

   ```JavaScript
   let result = ["mango", "pineapple", "orange"].map(item => item.length)

   console.log(result) // [ 5, 9, 6 ]
   ```

2. `.sort(fn)` - this method sorts the array in place. Changing the order of the elements. It also returns the sorted array but it usually ignored because the array it is called upon on is modified. This is a _mutating method_.

   ```JavaScript
   let arr = [ 1, 2, 15 ];

   // the method reorders the content of arr
   arr.sort();

   alert( arr );  // 1, 15, 2
   ```

   - Notice how the order is incorrect? because **the items are sorted as strings by default**.
   - Literally, all elements are converted to strings for comparisons. For strings, lexicographic ordering is applied and indeed `"2" > "15"`.
   - You need to supply a function as the argument of `arr.sort()`
   - The function provided should compare two arbitrary values and return:
     ```JavaScript
     function compare(a, b) {
       if (a > b) return 1; // if the first value is greater than the second
       if (a == b) return 0; // if values are equal
       if (a < b) return -1; // if the first value is less than the second
     }
     ```
   - Let try it again. For instance, to sort as numbers:

     ```JavaScript
     function compareNumeric(a, b) {
       if (a > b) return 1;
       if (a == b) return 0;
       if (a < b) return -1;
     }

     let arr = [ 1, 2, 15 ];

     arr.sort(compareNumeric);

     alert(arr);  // 1, 2, 15
     ```

   - use `localeCompare` for strings
     - For many alphabets, it’s better to use str.localeCompare method to correctly sort letters, such as Ö.

     - For example, let’s sort a few countries in German:

       ```JavaScript
       let countries = ['Österreich', 'Andorra', 'Vietnam'];

       alert( countries.sort( (a, b) => a > b ? 1 : -1) ); // Andorra, Vietnam, Österreich (wrong)

       alert( countries.sort( (a, b) => a.localeCompare(b) ) ); // Andorra,Österreich,Vietnam (correct!)
       ```

3. `.reverse()` - this method transform the original array by reversing the order of elements in the array that it is called upon on. This is a _mutating method_.
   - Lets take a look at the example below.

     ```JavaScript
     let arr = [1, 2, 3, 4, 5];
     arr.reverse();

     alert( arr ); // 5,4,3,2,1
     ```

   - This function returns the reversed array too like the `.sort()` method.

4. `.split()` and `.join()` - this method splits the string into an array by a given _delimiter_ `delim`. Since this is attached to a `string`, this is a _non-mutating method_.
   - **Syntax**: `str.split(delim, limit)`
     - Lets say we ask a user to enter their favorite games and the user types a straigth string.

       ```JavaScript
       let favoriteGames = "Pokemon, Persona, Final Fantasy, Rune factory"

       let faveGamesArr = favoriteGames.split(",")

       faveGamesArr.forEach((item, index)=>{console.log(`My number ${index + 1} favorite game is: ${item}`)})

       // My number 1 favorite game is Pokemon
       // My number 2 favorite game is Persona
       // My number 3 favorite game is Final Fantasy
       // My number 4 favorite game is Rune factory
       ```

     - the `limit` is an optional numeric argument, it present it puts a limit on the array length and would ignore extra elements.

       ```JavaScript
       let favoriteGames = "Pokemon, Persona, Final Fantasy, Rune factory";

       // we can also use regEx
       let faveGamesArr = favoriteGames.split(/,\s/, 2);

       faveGamesArr.forEach( (item, index)=>{console.log(`My number ${index + 1} favorite game is: ${item}`)} );

       // My number 1 favorite game is Pokemon
       // My number 2 favorite game is Persona
       ```

     - If you call this method with `arr.split("")`, this would separate the string into an array of letters.

   - **Syntax**: `arr.join(glue)` this method does the reverse of `.split()`. It creates a string of `arr` items joined by the `glue` between them.
     - Lets now restore the users input.

       ```JavaScript
       let favoriteGames = "Pokemon, Persona, Final Fantasy, Rune factory";

       // we can also use regEx
       let faveGamesArr = favoriteGames.split(/,\s/, 2);

       faveGamesArr.forEach( (item, index)=>{console.log(`My number ${index + 1} favorite game is: ${item}`)} );

       // My number 1 favorite game is Pokemon
       // My number 2 favorite game is Persona

       let restoredFaveGames = faveGamesArr.join(",");

       console.log(restoredFaveGames);
       // this return the string: Pokemon, Persona, Final Fantasy, Rune factory
       ```

5. `.reduce()` / `reduceRight()`
   - This method is a _non-mutating method_ that allows users to _reduce_ an item. They are used to calculate a single value based on the array
     - **Syntax**:
       ```JavaScript
       let value = arr.reduce(function(accumulator, item, index, array) {
         // ...
       }, [initial]);
       ```
     - The function is applied to all array elements one after another and “carries on” its result to the next call.
       - Arguments:
         - `accumulator` – is the result of the previous function call, equals initial the first time (if initial is provided).
         - `item` – is the current array item.
         - `index` – is its position.
         - `array` – is the array.
     - Lets say you took 5 exam to day and each exam has a maximum of 20 points that would be totaled to get the overall score. Your score are stored inside the array.

       ```JavaScript
       let scores = [ 20, 19, 15, 14, 20 ]

       let totalScore = scores.reduce( (acc, item) => { return acc + item}, 0 )
       let totalScoreTwo = scores.reduce( (acc, item) => { return acc + item} )

       console.log(totalScore) // 88
       console.log(totalScoreTwo) // 88
       ```

     - Notice how the answer is still the same even though we did not provide an `initial` argument.
     - **NOTE:** You can read more about this [here](https://javascript.info/array-methods#reduce-reduceright).

## Array.isArray()

- So we know that if we use `typeof` to an array, it would print `object` instead of `array`. So a method is specially created to validate a value.
  - `Array.isArray(value)`

    ```JavaScript
    alert(typeof {}); // object
    alert(typeof []); // object (same)

    alert(Array.isArray({})); // false
    alert(Array.isArray([])); // true
    ```

## General Rule

- IF a method has `.to*` in it, it means that it is a `non-mutating` method. It returns a new copy without changing the original array.
- All `non-mutating methods` returns a value. The returned values may be an `array`, `boolean`, `number` or `undefined`. Knowing what a method returns or what does it do to the original array helps in debugging.

## REREFENCE

[Array Methods](https://javascript.info/array-methods)
