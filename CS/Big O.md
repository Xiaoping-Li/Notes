# Big O Notation
## What is _Big O_
* **Big O notation is the language we use for talking about how long an algorithm takes to run**. It's how we compare the _efficiency_ of different approaches to a problem. With big O notation we express the runtime in terms of _how quickly it grows relative to the input, as the input gets arbitrarily large_.
  1. **how quickly the runtime grows** — It's hard to pin down the _exact runtime_ of an algorithm. It depends on the speed of the processor, what else the computer is running, etc. So instead of talking about the runtime directly, we use big O notation to talk about _how quickly the runtime grows_.
  2. **relative to the input** — With Big O notation, we use the _size of the input_, which we call`n`. So we can say things like the runtime grows "on the order of the size of the input" `(O(n))` or "on the order of the square of the size of the input" `(O(n^2) or "quadratic time")`.
  3. **as the input gets arbitrarily large** — Our algorithm may have steps that seem expensive when `n` is small but are eclipsed eventually by other steps as `n` gets huge. For big O analysis, we care most about the _stuff that grows fastest as the input grows_, because everything else is quickly eclipsed as `n` gets very large. (If you know what an _asymptote_ is, you might see why "big O analysis" is sometimes called "asymptotic analysis.")
  
## Some rules
### N could be the _actual_ input, or the size of the input
So sometimes `n` is an _actual number_ that's an input to our function, and other times nn is the _number of items in an input array_ (or an input _map_, or an input _object_, etc.).

### Drop the constants
Remember, for big O notation we're looking at what happens _**as `n` gets arbitrarily large**_. As `n` gets really big, adding 100 or dividing by 2 has a decreasingly significant effect.

### Drop the less significant terms
Again, we can get away with this because the less significant terms quickly become, well, less significant as nn gets big.

## Space complexity
Sometimes we want to optimize for using less memory instead of (or in addition to) using less time. Talking about memory cost (or "space complexity") is very similar to talking about time cost. We simply look at the total size (relative to the size of the input) of any new variables we're allocating.
### Usually when we talk about space complexity, we're talking about additional space
so we don't include space taken up by the inputs.

### Sometimes there's a tradeoff between saving time and saving space
so you have to decide which one you're optimizing for.
