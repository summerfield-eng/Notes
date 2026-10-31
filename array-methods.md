# Array Methods

- This will contain methods that is related to arrays.

## Add / Remove items

1. `.push(...items)` - adds items to the end.
2. `.pop()` - removes items from the end.
3. `.unshift()` - adds item to the beginning.
4. `.shift()` - extracts an item from beginning.
5. `.splice()` - this is a multifunction method that can _insert_, _remove_, and _replace_ elements.
   - **Syntax**: `arr.splice(start[, deleteCount, elem1, ..., elemN])`
     - it modifies `arr` staring from the `start`: removes `deleteCount`elements and then inserts `elem1`, `...`, `elemN` at their place.
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
