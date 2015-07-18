> **The time required by a method is proportional to the number of "basic operations" that it performs. **

# Big O Notation - O(n)

`Order of N`, O is also known as the **Order function**. 

> Big-O is about the approximate worst-case performance of doing something. AKA determining the upper bound. 
> It is the language we use for articulating how long an algorithm takes to run, how we compare the efficiency of different approaches to a problem.

 - We're dealing with an approximation, which deals in "**orders of magnitude**".
	- Orders of magnitude tells the **difference between classes of numbers**. 10 vs 100 vs 1000 etc
	- So long as you're `within an order of magnitude, you're pretty close`.
	- n can be the **actual** input or the **size** of the input.
		- N = 15 or N = array.length
 - In calculating Big-0, we're **only interested in the biggest term.**
	 - term = "portion of algebraic statement"
	 - **Drop constants** of the (aka things multiplying) variables - 2 from `O(2n)`.
		 - Products only change the `rate of growth` not the `type of growth`
 - Big-O is sometimes called "**asymptotic analysis**"
	 - an asymptote of a curve is a line such that the distance between the curve and the line approaches zero as they tend to infinity.


The `complexity` of a function is some derivation of `O(...)`. 

In a graph, the y-axis would represent the `time` and the x-axis represents the input `size`. The higher the curve, the slower it takes.

--- 
With big O notation, we **express runtime in terms of how quickly it grows relative to the input, as the input gets arbitrarily large.**

 1. **how quickly the runtime grows** - it's hard to actually determine processing speed of an algorithm, so we use Big O to express how `quickly it can grow`
 2. **relative to the input** - since we're not looking at an exact number, we say things like the runtime grows "on the order of the size of the input" O(n)
 3. **as input gets arbitrarily large** - some steps may seem expensive when n is small, but will be eclipsed by other steps as n gets huge.

---

> **The key aspects to determining the Big-O of a function is counting.** 
> 1. Enumerate the different operations your code does (be careful to understand what happens when you call out into another function!)
> 2. then determine how they relate to your inputs. 
> 3. From there, its just simplifying to the biggest term and dropping the multipliers.

**EXAMPLE:**
``` ruby
 def count_ones(a_list):
      total = 0
      for element in a_list:
          if element == 1:
              total += 1
      return total
```
i.   We're setting total to zero.
ii.  We loop through a_list.
iii. We check if element is equal to 1.
iv. We increment total by one a few times.

1. By **hardcoding the zero**, it happens in constant time. It is an `O(1)` operation.
2. Looping through the list, the **number of operations** performed depends on the input size. The time it takes to do something increases `linearly` with its input and is `O(n)`
3. Checking if an element is equal to 1 is an `O(1)` operation.
	4. To prove this, think about it is as a function `is_equal_to_one()`, it wouldn't take longer if we passed in more values b/c of the fixed number `1` in the comparison.
	5. **Binary comparisons are constant time** and that's what a comparison to 1 eventually is.
6. Increment total by 1 is like setting total to zero, but adding. So it is also constant time.

In calculating the Big O of this function, we have `O(1) + O(n) * ( O(1) + O(1) )`. One constant time operation at the beginning, then potentially two more constant time operations **for each item** in the list. 
Using Math, this reduces to `O(2n) + O(1)`. 

Now we look for the biggest term and drop multipliers, which is simply n. 


--- 

# Space complexity 

The memory cost (or "space complexity") is similar to talking about the time cost. This refers to  '**additional space**', so we don't include spade taken up by inputs.

This function takes O(1)
``` ruby
  def say_hi_n_times(n):
    for time in range(n):
        print "hi"
```

This function takes O(n)
``` ruby
  def array_of_hi_n_times(n):
    hi_array = []
    for time in range(n):
        hi_array.append("hi")
    return hi_array
```

--- 

Must find the balance between runtime, space, implementation time, maintainability, and readability.

If we only cared about solving problems of a fixed, limited size, time complexity would not be very important. The importance of scalability is baked into our adoption of time complexity as a measure of algorithm performance

---- 
# Key Terms

 1. `rate of growth` vs `type of growth`
	 2. rate of growth =  2n, 3n, 4n,
	 3. type of growth = 1, n, n^2, n log(n)
 4. Types of growth
	 5. Linear = simply just n
	 6. Quadratic growth = n^2, another way of saying 'squared' vs 'linear
		 7. Even with a high multiplier for a linear growth, quadratic growth will eventually beat linear growth as the upper bound increases.



---

# Complexities 

> In general, doing something with every item in one dimension is **linear**, doing something with every item in two dimensions is **quadratic**, and dividing the working area in half is **logarithmic**. 


### **O(1)**

> **EXAMPLE** : Checking if an element is equal to 1

Called `constant time`, no matter how big the input is, it always takes the same amount of times to compute.

> The best case scenario for an algorithm. 

### **O(n)**

> **EXAMPLES**:  
> Iterating over an array 
>  - Given a phone number, find the person or business with that number.

On a simple program whose complexity is `O(n)`, in graphing it, results correspond to number of items in the array, aka a `linear graph` (basically a straight line, a linear representation)


### **O(log N) and O(log n)**

> **EXAMPLES**
> 
> 1) **Binary search.**
	> For an array of 1000 elements, each pass (checking the middle value and then looking in the left half or the right half) cuts n in half. It is the cutting in half that makes binary search logarithmic.


**O(log N)** means that **time** goes up **linearly** while the `n` goes up exponentially. 

`log( a ) = b => a = 10^b  			`

 So if it takes `1` second to compute `10` elements, it will take `2` seconds to compute `100` elements, `3` seconds for `1000` elements, etc.

**O(log n)** is when we do a divide and conquer type of algorithm (binary search).

> log(x) refers to log2(x) in computer science and information theory
> log(x) refers to log10(x) in various engineering fields, logarithm tables, and handheld calculators.
> 
> **However**, they differ by a constant so the value of the base is irrelevant since it does not change the **type of growth**


![enter image description here](http://i49.tinypic.com/fqcmr.png)




## `O(n*log(n))`
any divide and conquer method - merge sort.
using sort automatically gives a lower bound of `O(n*log(n)`


merge sort is expensive for space complexity, creates more and more arrays.


### **O(n^2)**

> **EXAMPLES**
> 
> 1) **Bubble Sort**
>  Each element in the array, you potentially swap all the way up to the rest of the array (another `n` operations).
Every item in a list, (aka `n` for the input size), we have to do `n` more operations. So `n * n == n^2`

![enter image description her](https://justin.abrah.ms/static/images/runtime_comparison.png)




### **O(2^n)**

> For each additional input, the number of basic operations doubles.

----

# Tips

 

 - Linear time complexity is oftentimes the naive solution.
	 - If array is sorted, use **binary-search** which is `O(log(n))`.



---
# Things to think about:

When determining time complexity:

 1. What is the factor that can affect the number of questions asked (the "problem size")?
 2. In the worst case, how many questions will be asked?


 --- 

# Aside:

 
### **Best Case**
How many comparisons necessary in the case for an array of `n` values?
=> `O(1)`
**Reason:** As n, size of the array, grows larger, time to perform the comparison operation does not change. It is of **constant time**
![enter image description here](https://lh3.googleusercontent.com/-UdPEdSP89JU/VZbFpPq4k_I/AAAAAAAAAb8/W9LQ4QrAOJg/s0/Screen+Shot+2015-07-03+at+10.25.36+AM.png "Screen Shot 2015-07-03 at 10.25.36 AM.png")


### **Average Case**
How many comparisons are necessary in the average case for an array of n values (assuming the target is in the array)?


$ \frac{( 1 + 2 + ... + (n - 1) + n ) } n $

