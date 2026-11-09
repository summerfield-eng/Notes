# Array Exercise

- This will contain my answers for the exercises on this [site](https://javascript.info/array-methods#tasks).

## Translate border-left-width to borderLeftWidth

```JavaScript
function camelize(str) {
  let splitStr = str.split(/[-,]\s/).filter(item => item !== "");

  let formattedSplitStr = [splitStr[0]];

 for (let index = 1; index < splitStr.length; index++) {
    let word = splitStr[index]
    formattedSplitStr.push(word[0].toUpperCase() + word.slice(1));
  }

  return formattedSplitStr.join("");

}

console.log( camelizeTwo("-webkit-transition") )
console.log( camelizeTwo("list-style-image") )
console.log( camelizeTwo("background-color") )

function camelizeTwo(str) {
  return str
    .split("-")
    .map((item, index) => index === 0 ? item : item[0].toUpperCase() + item.slice(1))
    .join("")
}
```

## Filter range

```JavaScript
let arr = [5, 3, 8, 1];
let range = {
  minRange: 1,
  maxRange: 4,
  rangeFilter(value) {
    return value >= this.minRange && value <= this.maxRange
  }
}

let filteredValues = arr.filter( item => range.rangeFilter(item) )

console.log(filteredValues)

function filterer(arrs, min, max) {
    return arrs.filter(item => item >= min && item <= max)
}

filterer(arr, 1, 4)
```

## Filter range "in place"

```JavaScript
let arr = [5, 3, 8, 1];

function filterRangeInPlace(arr, min, max) {
  return arr.filter( (item) => { return item >= min && item <= max })
}

console.log( filterRangeInPlace(arr, 1,4) )
```

## Sort in decreasing order

```JavaScript
let arr = [5, 2, 1, -10, 8]

console.log( arr.sort( (a, b) => b - a) )
```

## Filter unique array members

```JavaScript
function unique(arr) {
  return Array.from( new Set(arr) )
}


function uniqueArr(arr) {
  let newArr = [];
  arr.map( item => {
    if(!newArr.includes(item)){
      newArr.push(item)
    }
  });
  return newArr;
}
let strings = ["Hare", "Krishna", "Hare", "Krishna",
  "Krishna", "Krishna", "Hare", "Hare", ":-O"
];

console.log( uniqueArr(strings) ); // Hare, Krishna, :-O

```

## Map to Names

```JavaScript
let john = { name: "John", age: 25 };
let pete = { name: "Pete", age: 30 };
let mary = { name: "Mary", age: 28 };

let users = [ john, pete, mary ];

let names = users.map(item => item.name);

alert( names ); // John, Pete, Mary
```

## Map to Objects

```JavaScript
let john = { name: "John", surname: "Smith", id: 1 };
let pete = { name: "Pete", surname: "Hunt", id: 2 };
let mary = { name: "Mary", surname: "Key", id: 3 };

let users = [ john, pete, mary ];

let usersMapped = users.map(name => {
  return {
    fullName: name.name +" " + name.surname,
    id: name.id
  }
})



console.log(usersMapped)
```

## Sort users by age

```JavaScript
let john = { name: "John", age: 25 };
let pete = { name: "Pete", age: 30 };
let mary = { name: "Mary", age: 28 };

let arr = [ pete, john, mary ];

sortByAge(arr);

function sortByAge(arrs) {
  arrs.sort((a, b) => a.age - b.age )
} //Since it is inside the object, then just add the property needed to sort

alert(arr[0].name); // John
alert(arr[1].name); // Mary
alert(arr[2].name); // Pete
```

## Get average age

```JavaScript
let john = { name: "John", age: 25 };
let pete = { name: "Pete", age: 30 };
let mary = { name: "Mary", age: 29 };

let arr = [ john, pete, mary ];

function getAverageAge(arrs) {
  return arr.reduce((acc, person)=>{return acc + person.age},0) / arr.length
}// since we need to get the average, we iterate over the arr then reduce the age

alert( getAverageAge(arr) ); // (25 + 30 + 29) / 3 = 28
```

## Create keyed object from array

```JavaScript
let users = [
  {id: 'john', name: "John Smith", age: 20},
  {id: 'ann', name: "Ann Smith", age: 24},
  {id: 'pete', name: "Pete Peterson", age: 31},
];

let usersById = groupById(users);

function groupById(arr) {
  let mappedUsers = {};

  for(let user of users) {
    mappedUsers[user.id] = {
      id: user.id,
      name: user.name,
      age: user.age
    } // I used computed properties of objects.
  }

  return mappedUsers

}

console.log(usersById)
```
