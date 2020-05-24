# Async JS

Hey. Today I want to talk to you about async in javascript.
If you don`t want to be surprised by Javascript, then you should learn how it works.
Javascript is a single flow asynchronous programming language. It was created in 1995. Since then it has undergone many changes and its main specification is now EcmaScript edition 10(June 2019).
To understand async in javascript, you need to understand two concepts: JavaScript Engine and JavaScript Run-time Environment.
The JavaScript engine is a program that is used to process a given code and convert it into machine code for execution.

And JavaScript Run-time Environment is an environment with a variety of features, services and support, such as arrays, functions, key libraries that make it easy to work with the code.

The javascript engines include gecko, quantum(for mozilla firefox), v8(for chrome and  edge). And browsers also provide us with methods to make it easier to use, and is called the browser api model.

The browser also provides us with event-loop, which allows us to implement async in javascript.

But first, let's understand what async is. Synchronization is when a second block of code is not executed until the first one is executed.
JavaScript is single threaded, as we said at the beginning, so only one block of code can be executed at a time.  

### Stack

The JS engine executes our code, processing line by line and to do this it needs a call stack to keep track of the code that is executed in the specified order. Stack is a data structure that takes blocks of code and executes them in "Last In First Out" style.

### Heap

A heap is just a name for marking a large unstructured memory area where data objects are located.

### Queue

Queue is a list of tasks to be processed. Each task is a function that will process this task when called.

When the stack is completely free, the first task is extracted from the queue and processed. The processing of a task consists of calling an associated function with the parameters written in that task.  The function call creates a new execution context and is written to the call stack.

Task processing finishes when the stack becomes empty. The next task is taken out of the queue and its processing begins.

### Starting before it finishes

Each task must be completed in full, before the next one. That's why we know exactly: when the current function is executed, that it won't be suspended and will be fully executed, before another code (which can change the data the current function is working with) is executed.

The disadvantage of this approach is that if the task takes too long, the application cannot process the user's actions at this time (e.g., scroll or click). The browser tries to help solve the problem and displays the message "a script is taking too long to run" and allows you to stop it, so it's a good practice to create tasks that run quickly, and if possible split the tasks into smaller ones.

### Adding events to the queue

To add a browser event to the queue, it must have a handler and it must happen. Without a handler, it will be lost and not added to the queue. But the call of setTimeout to add the event to the queue at the time specified in its second argument. and therefore it is correct to consider the minimum time it will run out. If the second setTimeout argument is 0, then the minimum time will be greater than 0, because there is a limitation in the browser on how often internal counters can be executed. The HTML5 standard says: "After five nested timers, the interval should be at least four milliseconds.

Async is when the first code block starts in the background, allowing the second block to start and run without waiting for the first block to complete. We may find this useful for tasks that take a long time to complete. For example, uploading images, dealing with files, or making requests to a server. And so blocking can occur. This is when the user cannot interact with the page or other code cannot be executed at the same time until blocking is executed.

Over the years we have had several ways to handle async without any crazy code. In most cases, we simply relied on callbacks. But when using callbacks for async you have to be careful, because the more nested calls our code will have, the more nested it will be, which is difficult to maintain, especially if instead of ... we have code that contains other call chains, conditions, etc. Sometimes this is called "callbacks hell" or "hellish callbacks pyramid".

### Promise

Promises is trying to solve one of the main headaches of the language since its inception: it is asynchronous.
Promise in JavaScript is a new tool for working with delayed or asynchronous computations added to ECMAScript 2015 (version 6 of ECMA-262).

Promise is an object that represents an asynchronous task that must be completed. And after the end you can start the callback then, which you passed when the promise was completed successfully or catch - starts the callback if the promise was not completed successfully or with an error.

### Promises methods

There are also additional built-in methods for working with a promise, like:

The Promise.all method returns a promise that will be fulfilled when all promise passed as a listed argument are fulfilled or any of the promise passed are rejected

The Promise.allSettled method returns a promise that is executed when all received promise are completed (executed or rejected), containing an array of promise execution results.

The Promise.race method returns a completed or rejected promise, depending on the outcome of the first promise passed, with the value or reason for rejecting that promise.

### Async/ await

Async/ await syntactic sugar for Promise.
Async/ await is a language addition already included in the latest EcmaScript draft.

Thank you :)