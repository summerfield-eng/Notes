# JavaScript Developer Tools

This note will contain all the important things that I've learn while learning web developement. It is formatted by the title and under it is the learnings that I've gathered.

### Notes:

- [Javascript info](https://javascript.info/debugging-chrome)
- [Function Basics](https://javascript.info/function-basics)
  - **nullish coalescing(??) vs or(||) operator**
    what is the difference? This is the whole point. 
    - || falls back on any falsy value; 
    - ?? falls back only on null/undefined:
    - || asks "is it falsy?" — ?? asks "is it missing?" Those are very different questions. 🤔
    ```
        function setVolume(level) {
          const volume = level || 50;   // 🐛
          // ...
        }

        setVolume(0);   // user wants MUTE → gets 50! 😱
    ```
    Based on the rule of the || operator, `const volume = level || 50;` returns the first truthy value, which is in this case is the `50`. In Javascript, other than the following: `false`, `undefined`, `null`, `0 (zero)`, `NaN` and ("") empty string, all values are considered truthy values. This is not what is the expected outcome. Thus the proper way to evaluate this is to use a nullish coalescent.
    Same trap with empty strings
    ```
      const name = input || "Anonymous";   // "" → "Anonymous" (maybe wrong!)
      const name = input ?? "Anonymous";   // "" stays "" ✅
    ```
- [Function Expressions](https://javascript.info/function-expressions)
    - a function is a **value**. Regardles if it is a _declared function_ or a _function expression_.
    - **A function is a value representing an “action”**. Regular values like strings or numbers represent the data. A function can be perceived as an action. We can pass it between variables and run when we want.
- [Arrow Functions](https://javascript.info/arrow-functions-basics)
- [Javascript Execution Context](https://www.javascripttutorial.net/javascript-execution-context/)
- [Javascript Call Stack](https://www.javascripttutorial.net/javascript-call-stack/)

