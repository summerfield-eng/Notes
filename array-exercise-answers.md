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
