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
let collection = ["Harvy" , 31, true]
let nameIndex = collection.indexOf("Harvy")
let ageIndex = collection.indexOf(31)
let booleanIndex = collection.indexOf(true)
let gfNameIndex = collection.indexOf("GF")

let hasGF = collection.inludes("GFName")
```

## General Rule

- IF a method has `.to*` in it, it means that it is a `non-mutating` method. It returns a new copy without changing the original array.
- All `non-mutating methods` returns a value. Some are `arrays`, `boolean`, `number` or `undefined`. Knowing what a method returns helps debugging.
