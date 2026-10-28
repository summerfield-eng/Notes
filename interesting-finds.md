# New Learnings

- This will document all the things that I didn't know before but made my life easier.

## Sets

- A **Set** is a collection of unique values. It automatically prevents duplicate values from being stored.
- So lets say you want to filter an array for any duplicate values. Normally we would iterate over it using a _for_ loop or use the _.map_ object.

  ```JavaScript
   1| let arr1 = [4,5,2,6,7,2,5]
   2| let filteredArr = [];
   3|
   4| for(let i = 0; i < arr1.length; i++){
   5|   if(!(filteredArr.includes(arr1[i]))){
   6|     filteredArr.push(arr1[i])
   7|  }
   8|}
   9|
  10| console.log(filteredArr) // [4, 5, 2, 6, 7]

  ```

- Using _Set_ object, we can lessen the code we need to write.
  ```JavaScript
  1| let arr1 = [4,5,2,6,7,2,5]
  2| let filteredArr = new Set(arr1);
  3| // filteredArr is currently an object, so in order
  4| // to convert it, we need to use a spread operator
  5| // or use the Array.from() object method.
  6|
  7| console.log(Array.from(filteredArr))
  8| // [4, 5, 2, 6, 7]
  ```
- It can also be written like this. The _..._ is a spread operator.
  ```JavaScript
   1| let arr1 = [4,5,2,6,7,2,5]
   2| let filteredArr = [...new Set(arr1)];
   3| console.log(filteredArr)
   4| // [4, 5, 2, 6, 7]
  ```

### Set methods

- Below are the 4 methods you should learn.
  1. .add(value)
     - this will add a value to the Set if it is not already present. Adding 101 twice doesn't create a duplicate.

     ```JavaScript
         const ids = new Set();
         ids.add(101);
         ids.add(102);
         ids.add(101);

         console.log(ids); // Set {101, 102}
     ```

  2. .has(value)
     - checks whether a value exist. Returns `true` or `false`.This is useful when you need to check whether you've already encountered something.

     ```JavaScript
     const ids = new Set([101, 102, 103]);

     console.log(ids.has(102)); // true
     console.log(ids.has(999)); // false
     ```

  3. .delete(value)
     - removes a specific value. Returns `true` if the value was removed, otherwise `false`.

     ```JavaScript
     const ids = new Set([101, 102, 103]);

     ids.delete(102);

     console.log(ids); // Set {101, 103}
     ```

  4. .clear()
     - removes every value.

     ```JavaScript
     const ids = new Set([101, 102, 103]);

     ids.clear();

     console.log(ids.size); // 0
     ```

     - Note: **.size** to get the number of values in a Set. Unlike arrays, Sets don't use `.length`.
