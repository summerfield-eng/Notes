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

## Transpilers and Polyfills

- JavaScript is a language that keeps on changing ang improving. So it is not surprising that there will be new features coming out every now and then.
- But sometimes, these features might not be supported in some browsers and could take a while to be implemented. So how do we make sure that codes using the new features will be able to run on unsupported browser or environment,
- The solutions is to make use of the currently existing functionalities to imitate what the new features does.

### Transpilers

- _Transpiler_ is a piece of software that translates a code to another source code. It can parse ("read and understand") modern code and rewrite it using older syntax constructs, so that it can work on outdated engines.
- There used to be no _nullish coalescing operator_ on JavaScript. So older engines would not understand `height = height ?? 100`.
- A transpiler would analyze our code and rewrite `height ?? 100` into `(height !== undefined && height !== null) ? height : 100`.

  ```JavaScript
    // before running the transpiler
    height = height ?? 100;

    // after running the transpiler
    height = (height !== undefined && height !== null) ? height : 100;
  ```

### Polyfills

- A script that updates/adds new functions is called “polyfill”. It “fills in” the gap and adds missing implementations.
- For example, `Math.trunc(n)` is a function that “cuts off” the decimal part of a number, e.g `Math.trunc(1.23) `returns `1`.
- For this particular case, the polyfill for Math.trunc is a script that implements it, like this:
  ```JavaScript
    if (!Math.trunc) { // if no such function
      // implement it
      Math.trunc = function(number) {
        // Math.ceil and Math.floor exist even in ancient JavaScript engines
        return number < 0 ? Math.ceil(number) : Math.floor(number);
      };
    }
  ```
  [Source](https://javascript.info/polyfills)

## Mutability and Immutability

- In order to understand these, we need to know about `Primitives` and `Reference` data types. And also the difference between `reassignment` and `mutation`
- `Primitives` are data types that is _immutable_. Meaning that we cannot change the _value_ once it is declared.
- `Reference` are data types that are _mutable_. Meaning that we can change the value once it is declared.
- Look at the example below:

  ```JavaScript
  let a = 30;
  a = 31; //This is reassignment.

  console.log(a) // 31
  ```

- Look at variable `a`, it is holding the value `30`. Then we reassign the value of `a` to `31`. We did not _mutate_ the value of variable `a`, we reassigned it.
  - Even if we add a value to variable `a`, like this, `a = a + 1` would be considered still as _reassignment_.

  ```JavaScript
  let a = 30;
  a = a + 1; //This is still reassignment

  console.log(a) // 31
  ```

- So think of mutability like a box with a label. The label is the _variable_. Whats inside the box is the _value_. So when we reassign a variable, we are actually removing the the label of the box, and sticking it to a box that hold the new value. The box still exist with the old value, it just does not have any label. This is reassignment.

### Mutating Array Methods

- push()
- pop()
- unshift()
- shift()
- splice()
- sort()
- reverse()
- fill()
- copyWithin()

Note:
A method can be non-mutating while its callback

### NOTES:

- `Stack` and `Heap` does not determine `mutability`.
- `Reassignment` is not the same as `mutability`.
- `Non-mutating` means it does **NOT** modify the original _value_ or _object_. It also does not necessarily mean creating a new copy. Because when we talked about _non-mutating methods_, that method might retun other values such as `strings`, `number`, `boolean` etc.
- `Non-mutating methods`: These are _methods_ that is _non-mutating_. Meaning it does not modify the original data when you apply that method to a data type. All _non-mutating methods_ returns a value without modifying the original data. But the returned valued may be:
  - A _new_ `array` (slice(), filter())
  - A _new_ `string` (toUpperCase(), trim())
  - A `boolean` (includes(), startsWith())
  - A `number` (indexOf())
  - `undefined` (forEach())
  - The important distinction is:
    - Mutation: Does the operation modify the original data?
    - Return value: What does the operation give back?
- `Mutating` means it modifies the original _value_ or _object_.
- `Mutating methods` - These are _methods_ that **does** modify the original data. Some methods returns a value and some methods returns `undefined` like `forEach()`.
- `Summary` A method can be _non-mutating_ and _mutating_. They can also return a value or return `undefined`.
- `Mutability` describes whether the original gets changed, **NOT** whether memory gets allocated.
- `Reassignment`: Changing what a `variable` holds.
  [reasignment](../../../..)

---

### AI NOTES

## Mutability and Immutability

- To understand these, you need `Primitives` vs `Reference` data types — and
  above all, the difference between **reassignment** and **mutation**. These are
  TWO DIFFERENT OPERATIONS, and confusing them is the main source of confusion.
  - 🔄 **Reassignment** — point a _variable_ at a different value.
    Available for every type. Never affects other variables.
  - ✏️ **Mutation** — change the _thing itself_, in place.
    Only possible on mutable types. Always affects every variable pointing at it.

- `Primitives` (number, string, boolean, null, undefined, symbol, bigint) are
  **immutable**: they have no parts you can reach into, so there is nothing to
  change. `5` is always `5`. The only thing you can do is reassign the variable
  to a _different_ value — which leaves the original value untouched.
