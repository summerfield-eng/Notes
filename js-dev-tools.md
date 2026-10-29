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
- [Pseudocode](https://builtin.com/data-science/pseudocode)
  - A pseudocode is a step by step problems in solving a problem in relation to a program.

    > Pseudocode describes the distinct steps of an algorithm in a way that anyone with basic programming skills can understand. Here’s how to write your own.

    > Pseudocode in data science or web development is a technique used to describe the distinct steps of an algorithm in a way that’s easy for anyone with basic programming knowledge to understand.

  - the main idea of a pseudocode is to represent the _six programming construct_ (always written in uppercase):
    1. SEQUENCE
    2. WHILE
    3. REPEAT-UNTIL
    4. FOR
    5. IF-THEN-ELSE
    6. CASE
       in a way that it is easier to be understood.

  ## How to Write Pseudocode
  1. Always capitalize the first word(often one of the main six constructs).
  2. Make one statement per line.
  3. Indent to show hierarchy, improve readability and shot nested constructs.
  4. Always end multi-line sections using any of the END keywords (ENDIF, ENDWHILE, etc.).
  5. Keep your statements programming language independent.
  6. Use the naming domain of the problem, not that of the implementation. For instance: “Append the last name to the first name” instead of “name = first+last".
  7. Keep it simple, concise and readable.
