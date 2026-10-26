# Event loop

This will contain all the notes about the event loop. This will answer the questions below.

- What is it?
- Why do we need it?
- What problem does it solve?
- How does it work ?

## Event Loop, What is it?

Event loop is a component inside a JavaScript runtime environment. Whether it is in a browser or the Node runtime environment.

The other components/parts are below.

- Call Stack (+ Heap memory)
- Web API's Environment
- Task Queue
- Microtask Queue
- Event loop
  ![The JavaScript runtime environment](image-1.png)

This components work together to make JavaScript non-blocking.

## Event Loop, why do we need it?

### Single Threaded

- JavaScript is a single-threaded language. Meaning it only has one _call stack_ and can only handle one task at a time. This call stack manages the execution order of all a program. It's duty is to execute any code inside it.
- When a program runs, JavaScript will create all the variables in the memory (Heap) and it would create a _global execution_ context, that would be added in the call stack. The call stack run on the basis of _Last In First Out_ principle, meaning, the all the functions will be stacking up on top of each other. A _function execution_ context would be created for these functions that would be added on top of the global execution context.
- So in summary, any function call will be first push into the call stack, executed, and after exectution will be pop-off the call stack.
- This is perfect for synchronous code. But real life applications work differently. Occasionally, we would need to wait for a certain resources before we could run a certain code. We would need to set some timers etc. Since JavaScript is a single threaded language, it can only perform task one a time, it could not pause or delay the execution of a task. So if a programs requires it to wait for a few seconds, JavaScript is unable to handle it or else, it would slow the program or even cause the program to freeze. To solve this, JavaScript uses a different approach.

## Event Loop, what problem does it solve?

- Since we know that JavaScript can only handle one task at a time and could not pause any process, then how does it deal with timers, fetching resources, url's etc?
- To solve this, JavaScript would rely on other components. Namely the **web Environment API**.

### Web API's

- What are APIs? These are functionalities provided by the runtime environment (Browser or Node) but not by JavaScript. JavaScript at it's core is simply code.
  These api's allows us to communicate outside to other resources.
- API's are divided if it is a _synchronous process_ or _asynchronous process_
  - 🔵 SYNCHRONOUS APIs → run on the call stack, block until done
    console.log, document.querySelector, Math.random, JSON.parse

  - 🟠 ASYNCHRONOUS APIs → handed to the browser, callback queued later
    setTimeout, fetch, addEventListener, geolocation

- Lets first define what are the APIs that is being passed from the call stack to the web api environment.
  - Asynchonous API 🟠
    - Timers ⏱️
      - setTimeOut(fn, time), setInterval(fn, time)
    - Fetch 🌐
      - networking (HTTP), for calling backend services.
    - Event APIs 👂
      - adding event listeners for click, drag, hover, key presses etc.
    - Geolocation API's 📍
      - Accessing the users location
    - Web Sockets 🔌

  - Synchonous API 🔵
    - DOM APIs 🏗️
      - getting specific html elements, updating the elements
    - Storage 🗄️
      - Accessing the localStorage, session storage
    - Console 📢
      - console.log, console.warn, console.error etc
    - URL 🔗
      - fetching some data
      - The URL object
    - Media & Canvas
    - Web Workers

### Window Object

- To reiterate, these API are provide by the runtime environment. And we can access these api through the **window** object. That is why occasionally you will see `window.setInterval()` or `window.document.querySelector("li")`. The _window_ can be omitted when calling these APIs.
  ![Web API Environment](image.png)

## Event Loop, how does it work?

- Since we now have a general idea on how synchronous code works and how does web api's work, this section will discuss how asynchronous code words in JavaScript. How does it keep JavaScript non-blocking despite being single-threaded.
- Lets see the code below:

```JavaScript
1|  console.log("Start")
2|
3|  setTimeout(()=>{
4|     console.log("Callback")
5|  }, 4000)
6|
7|  console.log("End")
```

- The result of this code will look like this:

```JavaScript
1| Start
2| End
3| Callback
```

### Event Loop in action

- We know that JavaScript loads the code from top to bottom. So how did the call stack and web api worked to produce this result?
  1. The moment the code runs, a _Global Execution_ context is created inside the call stack.
  2. JavaScript then starts executing the code `console.log("Start")`. Since this api(`window.console.log("Start")`) is a synchrounous one, the _call stack_ will execute the code and print `Start` on the console.
  3. JavaScript will then go to the next line, which we have the `setTimeout()` api. Inside this api is an arrow function with `console.log("Callback")` which will then be passed to the wep api environment where it would be stored and registered and it will wait until it finishes the minimum 4 seconds timeout. **Alt**: `setTimeout()` is called and executes synchronously on the call stack — its only job is to register the arrow function and the 4000ms timer with the Web API environment. It then returns a timer ID and pops off the stack. The browser handles the countdown."
  4. Since the call stack **cannot** delay any code execution or pause it, it will continue running the code.
  5. On the next line, `console.log("End")` will be executed and print `End` on the console.
  6. Now that we reached the end of the code, the whole code execution is completed. The _global execution_ context will be pop-out the call stack.
  7. But we still have the function that came from the`setTimeout()` api counting down inside the web api environment. What happens next? The moment it reaches 0, the function is now ready to be executed.
  8. Since all code executions is done inside the call stack, we need to put the function back inside it. In this scenario, the call stack is empty, but what if there are still code being process inside the call stack, we cannot directly put it into the call stack as it might interfere with the process. So this is where the **Event loop** and the **Task / Callback queue / Macrotask queue** comes in.
  9. Since there might be some code being executed inside the call stack, the function will have be push into the _callback queue_. This is where the _event loop_ will start it's job.
  10. The _event loop_ will start by checking two things continously:
      1. Is the _call stack_ empty?
      2. Are there tasks inside the Task/Callback queue?
  11. The _event loop_ will check the _call stack_. Since the _call stack_ is empty after running our last code. It will then check for the _task / callback queue_ for any task. Since the function exist inside the _callback queue_, the _event loop_ will take that function and add it inside the _call stack_. where it will be executed.
  12. Since it is a function, internally it would create a _function execution_ context. The function will run the `console.log("Callback")` and print the `Callback`.
  13. The _call stack_ will now be empty.

#### Other scenario

- Lets say the call stack is executing some code while other task exist in the callback queue. How will event loop handle it?
  1. Since we know the event loop continously check if the call stack is empty and checks if there are tasks inside the callback queue, the event loop will first wait until the all the task inside call stack are completed and is empty.
     ![scenario 2](image-2.png)

  2. Now that the call stack is empty, the event loop will now be active and push the task inside the callback queue, one task at a time.
     ![scenario 2.1](image-3.png)
     ![secnario 2.2](image-4.png)
  3. The event loop will then start to wail until the call stack is empty and if it does, it will pust the task inside the callback queue into the call stack for it to be executed.
     ![scenario 2.3](image-5.png)
     ![scenario 2.4](image-6.png)
  4. After finishing the execution, both the callstack and the callback queue are empty.
     ![scenario 2.5](image-7.png)

- Now we finally understand how event loop works. It is simple but very impactful as it acts as a bridge that connects all the components inside the runtime environment. Making the JavaScript non-blocking.

### Another example using Geolocation API

- Take a look at the code below:

```JavaScript
1|  navigator.geolocation.getCurrentPosition(
2|
3|  (position) => console.log(position),
4|
5|  (error) => console.log(error)
6|
7|  );
```

- This api will get the location of the user through the _navigator_ object. If the user approves it, we will get the `position`, if the user denies it, we will get `error`.

- Now here are what will happen.
  1. Before the code runs, JavaScript will create a _global execution_ context inside the _call stack_.
     ![scenario 3](image-8.png)
  2. Line 1 runs, JavaScript 'sees' that this line has a web api called `geolocation`. Javascript will execute the `.getCurrentPosition()` synchronously and pass the callback functions (position and error) in the web api environment. The `.getCurrentPosition()` will then be pop-out of the call stack
     ![scenario 3.1](image-9.png)
  3. The web api environment will show a prompt asking for permission to get the user's information.
  4. While it is waiting for the user's approval, the code execution will continue. It will proceed to line 7. At this point the code execution is complete. The _global execution_ content will be popped off the call stack and will become empty. Note: That the global execution context will only be created the first time the code runs.
     ![scenario 3.2](image-10.png)
  5. The user can choose if he wants to allow or denied sharing his location. Based on this two posibilities, we can either received a position or an error.
     ![scenario 3.3](image-11.png)
  6. Let's assume the user gave their permission. The success callback function containing the `console.log()`_position_ will then be passed to the _callback queue_
     ![scenario 3.4](image-12.png)
  7. The event loop will do its job checking if the _call stack_ is empty and if there are tasks inside the _callback queue_.
  8. The callback function _position_ will now be pass to the _callstack_ by the _event loop_. Where an execution context will be creatd for it.
     ![scenario 3.5](image-13.png)
  9. The `console.log(position)` will be executed in the call stack and will be pop-out after execution. Remember that `console` is a synchronous api. So it will happen inside the _call stack_, and the user position will appear in the console.
     ![scenario 3.6](image-14.png)
