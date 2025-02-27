# **Executing Promises in Sequence in JavaScript**

## **Introduction**
In JavaScript, when working with multiple asynchronous tasks, we often need to execute them **one after another** instead of running them in parallel.  
This can be achieved using:

1. **`reduce()` with Promises**
2. **`async/await` with a loop**

---

## **Approach 1: Using `reduce()` with Promises**

```javascript
function executeInSequence(tasks) {
    return tasks.reduce((promiseChain, currentTask) => {
        return promiseChain.then(currentTask);
    }, Promise.resolve());
}

// Example: Array of functions returning promises
const task1 = () => new Promise(resolve => setTimeout(() => { 
    console.log("Task 1 done"); 
    resolve(); 
}, 1000));

const task2 = () => new Promise(resolve => setTimeout(() => { 
    console.log("Task 2 done"); 
    resolve(); 
}, 500));

const task3 = () => new Promise(resolve => setTimeout(() => { 
    console.log("Task 3 done"); 
    resolve(); 
}, 800));

executeInSequence([task1, task2, task3])
    .then(() => console.log("All tasks completed"));
```


```javascript
 async function executeInSequence(tasks) {
    for (const task of tasks) {
        await task();
    }
}

// Same tasks array
executeInSequence([task1, task2, task3])
    .then(() => console.log("All tasks completed"));

