# Practical Big O Notation for JavaScript Developers

Big O notation is one of those things we usually learn about when we go through some kind of formal education (i.e college), otherwise the practical aspects of our day-to-day tend to overrun it and leave it as a completely secondary term that we can live without — and many of you do!

With that being said, I still believe there are benefits to understanding this notation at a high level. Quickly understanding the performance implications of an algorithm is not only useful but very practical.

So let’s take a quick look at what Big O notation is and what exactly should you be looking out for.

## What is Big O notation?

The Big O notation is nothing more than a mathematical way of describing the complexity and performance of an algorithm.

I refuse to go in-depth into how to calculate the exact expression because honestly, you will likely never need it. Instead, you’ll only be needed the abbreviated version of it, something that will give you an idea of how fast the complexity of an algorithm will grow once the amount of values it needs to work with grows.

Let’s me put it like this: Big O notation is a way to graphically represent how fast the complexity of an algorithm grows while the number of data points it requires approaches infinity. Or it’s also a way to compare two algorithms within the same domain, the one with the lower BigO notation is usually better, at least performance-wise.

I know, it doesn’t sound a lot easier, but let me show you what I mean:

<img src="https://res.cloudinary.com/practicaldev/image/fetch/s--A-6wvO1G--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/95ybuwyn8vmnkzftyurx.png">

Look at the above image and consider the Y-axis as complexity, while the X-axis is the number of elements your algorithm will deal with (here “elements” can be anything from the number of variables to potential different values, or perhaps even number of instructions it needs to execute, we’ll be seeing some examples).

I won’t go into every single option here, because again, if you haven’t been using BigO until now, you can already benefit by understanding what O(n!), O(nlogn), O(n), O(logn) and O(1) mean. The rest of them are in-between and after reading this article you should be able to determine whether they’re good for you or not.

## O(n!)

Let’s start at the worst-case scenario, the O(n!) case, that’s the black line in the above chart.

Sometimes you can’t avoid it, but if you can you should try to keep away from these types of algorithms as they are the ones that scale for the worst.

Note: If you see yourself not being able to solve the problem following a linear approach in less than n! time, then consider alternatives such as parallel processing, distributed computing or other, more complex solutions that might yield better results.

But personal note aside, some algorithms such as finding all permutations of a list of values, or even calculating the factorial number of a value have very common O(n!) solutions.

Also, another very common problem to solve, such as calculating the Fibonacci sequence. If you do it recursively — which unless you’re using a programming language that has “tail call optimization” (and JS doesn’t) you’ll run into problems for very small numbers— you would get an O(n!) algorithm.

## O(nlogn)

I think it’s important to understand this particular order of magnitude because many common algorithms fall inside it.

In particular, sorting algorithms such as Merge Sort, Heap Sort and Quick Sort will have this performance. This means that if you’re trying to sort enough elements with them, the execution times will not scale gracefully. In fact, they’ll keep going up and up very quickly.

Many developers claim that JavaScript’s Array.sort method has a Big O complexity of O(nlogn), but in reality, it depends on the implementation the runtime has used. For instance, Firefox uses Merge Sort, so yes, O(nlogn) is correct as a usual execution complexity. However, the V8 runtime for instance (and thus Chrome, Node.js and even Deno), uses Timsort a mixture of Merge Sort and Insert sort that has a best-case scenario of O(n) which if you go back to the chart from above, it’s considerably better.

## O(n)

The green line on the chart can be read as: your algorithm will have to go through every data point to perform the task at hand. The more data points to process, the more time it’ll take to do it.

These are not necessarily bad algorithms, but if the value of n (i.e the number of data points) is meant to grow quite high, then you have to consider the implications and maybe even, some kind of optimization.

A classical O(n) algorithm would be one that needs to traverse all the elements of a list to perform an action, for instance, imagine having to count the number of odd values in your array:

```js
function countOdds(list) {
  let totalOdds = 0;
  list.forEach((n) => {
    if (n % 2 == 0) totalOdds++;
  });

  return totalOdds;
}
```

If we’re dealing with 10 elements on the array, it’ll go through all of them but it’ll do it quickly. However, if your array suddenly contains 1.000.000 elements, it’ll take a while because its complexity is growing accordingly.

## O(logn)

The blue line (log2 n) tells you that while the complexity will grow, it’ll grow slowly, and even better, the growth rate is capped. It will not go past a certain point, no matter how many more data points you add. This is a very good algorithm and it can scale quite high.

A classical example of an O(logn) algorithm is the binary search, which is constantly dividing the problem universe in half.

In case you’re not familiar with the algorithm, here is a quick run down, always assuming you’re looking for a value inside a sorted list of elements.

- You identify the element in the middle of your list.
- You compare your target value with the middle value. If it matches, you’re done. Otherwise, continue to 3.
- If the target is lower than the middle value, drop the right-hand list and repeat from step 1 on the left-hand list.
- If the target is higher than the middle value, drop the left-hand list and repeat from step 1 on the right-hand side.
- Repeat the process until you find the target or run out of values to compare.

Now the magic of this algorithm is that if you grow the number of elements in the list, thanks to the fact that you’re constantly dropping half of it, you’ll still be able to finish very fast.

For instance, in a worst-case scenario, if you have 1.000.000 elements, you’ll have to compare values 20 times. That’s right, 20 times (which is quite close to 13.8, which is the value of **logn(1000000))**.

If you think about it, you’re going from 1.000.000 to 20 with a change from O(n) to O(logn).

## O(1)

Or constant time as others call it.

This is the ideal notation and it means that you’ll always be able to perform the action you’re looking for without caring for the number of elements you’re having to deal with.

If you’re able to write an algorithm that achieves constant time then it’s definitely worth the time and effort put into it.

An example of this would be using an object literal vs having multiple IF statements to decide what to do with your logic. Let me explain with an example, imagine having this code:

```js
function myFunction(myValue) {
  if (myValue == 1) {
    return doOneThing();
  }

  if (myValue == 3) {
    return doAnotherThing();
  }

  if (myValue == 4) {
    return doYetAnotherThing();
  }

  //default behavior
  return doTheDefaultThing();
}
```

Worst-case scenario, that code is checking every IF statement and then returned the default behavior. Granted, depending on your outside logic that decides the value of **myValue** you could argue that your best case scenario is a lot better, and 8 out of 10 times **myValue** will have the value of 1. However, we’re planning for the worst and hoping for the best here. And since we have an algorithm that is checking “n” times the value of **myValue** we can say that right now its Big O notation is O(n) — mind you, for a very small number of “n”, but nevertheless if you call this function often it could potentially be a performance hit.

Can we improve on it? I’d say yes, we can, let’s take a look:

```js
let logicBehavior = {
  1: doOneThing,
  3: doAnotherThing,
  4: doYetAnotherThing,
};

function myFunction(myValue, logic) {
  try {
    logic[myValue]();
  } catch (e) {
    doTheDefaultThing();
  }
}
```

Now you may or may not fully like this solution, but it’s no longer checking every value. In fact, it is directly accessing the function it should be calling. And since we’re planning for the worst, in our “worst-case scenario” it’s first checking for the index’s existence in **logic** and then calling **doTheDefaultThing**, that would be a Big O notation of O(2), which again, it’s a constant number for potentially millions of calls, so we can safely disregard that 2 and call it an O(1).

If you go back to the chart from the start, this would be the pink line. Of course not every single algorithm can be O(1).

Big O notation is nothing more than a tool. It helps us compare algorithms within the same space and understand at a glance, how performant they’ll be without having to read a lot of documentation or benchmarks about them.

Many libraries or even other software products will make use of this notation as well, a classic example of it is Redis. Redis’ documentation states the Big O notation for all of its commands, which helps you understand if you should or shouldn’t be using them considering the number of records they’ll be interacting with.

Keep in mind that this is also a “worst-case scenario” type of measurement and given the right circumstances you could still make do with a O(n^2) algorithm.
