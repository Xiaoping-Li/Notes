# Big O Notation
## What is _Big O_
* **Big O notation is the language we use for talking about how long an algorithm takes to run**. It's how we compare the _efficiency_ of different approaches to a problem. With big O notation we express the runtime in terms of _how quickly it grows relative to the input, as the input gets arbitrarily large_.
  1. **how quickly the runtime grows** — It's hard to pin down the _exact runtime_ of an algorithm. It depends on the speed of the processor, what else the computer is running, etc. So instead of talking about the runtime directly, we use big O notation to talk about _how quickly the runtime grows_.
  2. **relative to the input** — With Big O notation, we use the _size of the input_, which we call`n`. So we can say things like the runtime grows "on the order of the size of the input" `(O(n))` or "on the order of the square of the size of the input" `(O(n^2))`.
  3. **as the input gets arbitrarily large** — Our algorithm may have steps that seem expensive when `n` is small but are eclipsed eventually by other steps as `n` gets huge. For big O analysis, we care most about the _stuff that grows fastest as the input grows_, because everything else is quickly eclipsed as `n` gets very large. (If you know what an _asymptote_ is, you might see why "big O analysis" is sometimes called "asymptotic analysis.")
  
