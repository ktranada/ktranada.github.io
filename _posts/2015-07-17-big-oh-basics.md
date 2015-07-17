<blockquote>
  <p><strong>The time required by a method is proportional to the number of “basic operations” that it performs. </strong></p>
</blockquote>



<h1 id="big-o-notation-on">Big O Notation - O(n)</h1>

<p><code>Order of N</code>, O is also known as the <strong>Order function</strong>. </p>

<blockquote>
  <p>Big-O is about the approximate worst-case performance of doing something. AKA determining the upper bound.  <br>
  It is the language we use for articulating how long an algorithm takes to run, how we compare the efficiency of different approaches to a problem.</p>
</blockquote>

<ul>
<li>We’re dealing with an approximation, which deals in “<strong>orders of magnitude</strong>“. <br>
<ul><li>Orders of magnitude tells the <strong>difference between classes of numbers</strong>. 10 vs 100 vs 1000 etc</li>
<li>So long as you’re <code>within an order of magnitude, you're pretty close</code>.</li>
<li>n can be the <strong>actual</strong> input or the <strong>size</strong> of the input. <br>
<ul><li>N = 15 or N = array.length</li></ul></li></ul></li>
<li>In calculating Big-0, we’re <strong>only interested in the biggest term.</strong> <br>
<ul><li>term = “portion of algebraic statement”</li>
<li><strong>Drop constants</strong> of the (aka things multiplying) variables - 2 from <code>O(2n)</code>. <br>
<ul><li>Products only change the <code>rate of growth</code> not the <code>type of growth</code></li></ul></li></ul></li>
<li>Big-O is sometimes called “<strong>asymptotic analysis</strong>” <br>
<ul><li>an asymptote of a curve is a line such that the distance between the curve and the line approaches zero as they tend to infinity.</li></ul></li>
</ul>

<p>The <code>complexity</code> of a function is some derivation of <code>O(...)</code>. </p>

<p>In a graph, the y-axis would represent the <code>time</code> and the x-axis represents the input <code>size</code>. The higher the curve, the slower it takes.</p>

<hr>

<p>With big O notation, we <strong>express runtime in terms of how quickly it grows relative to the input, as the input gets arbitrarily large.</strong></p>

<ol>
<li><strong>how quickly the runtime grows</strong> - it’s hard to actually determine processing speed of an algorithm, so we use Big O to express how <code>quickly it can grow</code></li>
<li><strong>relative to the input</strong> - since we’re not looking at an exact number, we say things like the runtime grows “on the order of the size of the input” O(n)</li>
<li><strong>as input gets arbitrarily large</strong> - some steps may seem expensive when n is small, but will be eclipsed by other steps as n gets huge.</li>
</ol>

<hr>

<blockquote>
  <p><strong>The key aspects to determining the Big-O of a function is counting.</strong>  <br>
  1. Enumerate the different operations your code does (be careful to understand what happens when you call out into another function!) <br>
  2. then determine how they relate to your inputs.  <br>
  3. From there, its just simplifying to the biggest term and dropping the multipliers.</p>
</blockquote>

<p><strong>EXAMPLE:</strong></p>



<pre class="prettyprint"><code class="language-ruby hljs "> <span class="hljs-function"><span class="hljs-keyword">def</span> </span>count_ones(a_list)<span class="hljs-symbol">:</span>
      total = <span class="hljs-number">0</span>
      <span class="hljs-keyword">for</span> element <span class="hljs-keyword">in</span> <span class="hljs-symbol">a_list:</span>
          <span class="hljs-keyword">if</span> element == <span class="hljs-number">1</span><span class="hljs-symbol">:</span>
              total += <span class="hljs-number">1</span>
      <span class="hljs-keyword">return</span> total</code></pre>

<p>i.   We’re setting total to zero. <br>
ii.  We loop through a_list. <br>
iii. We check if element is equal to 1. <br>
iv. We increment total by one a few times.</p>

<ol>
<li>By <strong>hardcoding the zero</strong>, it happens in constant time. It is an <code>O(1)</code> operation.</li>
<li>Looping through the list, the <strong>number of operations</strong> performed depends on the input size. The time it takes to do something increases <code>linearly</code> with its input and is <code>O(n)</code></li>
<li>Checking if an element is equal to 1 is an <code>O(1)</code> operation. <br>
<ol><li>To prove this, think about it is as a function <code>is_equal_to_one()</code>, it wouldn’t take longer if we passed in more values b/c of the fixed number <code>1</code> in the comparison.</li>
<li><strong>Binary comparisons are constant time</strong> and that’s what a comparison to 1 eventually is.</li></ol></li>
<li>Increment total by 1 is like setting total to zero, but adding. So it is also constant time.</li>
</ol>

<p>In calculating the Big O of this function, we have <code>O(1) + O(n) * ( O(1) + O(1) )</code>. One constant time operation at the beginning, then potentially two more constant time operations <strong>for each item</strong> in the list.  <br>
Using Math, this reduces to <code>O(2n) + O(1)</code>. </p>

<p>Now we look for the biggest term and drop multipliers, which is simply n. </p>

<hr>



<h1 id="space-complexity">Space complexity</h1>

<p>The memory cost (or “space complexity”) is similar to talking about the time cost. This refers to  ‘<strong>additional space</strong>‘, so we don’t include spade taken up by inputs.</p>

<p>This function takes O(1)</p>



<pre class="prettyprint"><code class="language-ruby hljs ">  <span class="hljs-function"><span class="hljs-keyword">def</span> </span>say_hi_n_times(n)<span class="hljs-symbol">:</span>
    <span class="hljs-keyword">for</span> time <span class="hljs-keyword">in</span> range(n)<span class="hljs-symbol">:</span>
        print <span class="hljs-string">"hi"</span></code></pre>

<p>This function takes O(n)</p>



<pre class="prettyprint"><code class="language-ruby hljs ">  <span class="hljs-function"><span class="hljs-keyword">def</span> </span>array_of_hi_n_times(n)<span class="hljs-symbol">:</span>
    hi_array = []
    <span class="hljs-keyword">for</span> time <span class="hljs-keyword">in</span> range(n)<span class="hljs-symbol">:</span>
        hi_array.append(<span class="hljs-string">"hi"</span>)
    <span class="hljs-keyword">return</span> hi_array</code></pre>

<hr>

<p>Must find the balance between runtime, space, implementation time, maintainability, and readability.</p>

<p>If we only cared about solving problems of a fixed, limited size, time complexity would not be very important. The importance of scalability is baked into our adoption of time complexity as a measure of algorithm performance</p>

<hr>



<h1 id="key-terms">Key Terms</h1>

<ol>
<li><code>rate of growth</code> vs <code>type of growth</code> <br>
<ol><li>rate of growth =  2n, 3n, 4n,</li>
<li>type of growth = 1, n, n^2, n log(n)</li></ol></li>
<li>Types of growth <br>
<ol><li>Linear = simply just n</li>
<li>Quadratic growth = n^2, another way of saying ‘squared’ vs ‘linear <br>
<ol><li>Even with a high multiplier for a linear growth, quadratic growth will eventually beat linear growth as the upper bound increases.</li></ol></li></ol></li>
</ol>

<hr>



<h1 id="complexities">Complexities</h1>

<blockquote>
  <p>In general, doing something with every item in one dimension is <strong>linear</strong>, doing something with every item in two dimensions is <strong>quadratic</strong>, and dividing the working area in half is <strong>logarithmic</strong>. </p>
</blockquote>



<h3 id="o1"><strong>O(1)</strong></h3>

<blockquote>
  <p><strong>EXAMPLE</strong> : Checking if an element is equal to 1</p>
</blockquote>

<p>Called <code>constant time</code>, no matter how big the input is, it always takes the same amount of times to compute.</p>

<blockquote>
  <p>The best case scenario for an algorithm. </p>
</blockquote>



<h3 id="on"><strong>O(n)</strong></h3>

<blockquote>
  <p><strong>EXAMPLES</strong>: <br>
  Iterating over an array  <br>
   - Given a phone number, find the person or business with that number.</p>
</blockquote>

<p>On a simple program whose complexity is <code>O(n)</code>, in graphing it, results correspond to number of items in the array, aka a <code>linear graph</code> (basically a straight line, a linear representation)</p>



<h3 id="olog-n-and-olog-n"><strong>O(log N) and O(log n)</strong></h3>

<blockquote>
  <p><strong>EXAMPLES</strong></p>

  <p>1) <strong>Binary search.</strong> <br>
  For an array of 1000 elements, each pass (checking the middle value and then looking in the left half or the right half) cuts n in half. It is the cutting in half that makes binary search logarithmic.</p>
</blockquote>

<p><strong>O(log N)</strong> means that <strong>time</strong> goes up <strong>linearly</strong> while the <code>n</code> goes up exponentially. </p>

<p><code>log( a ) = b =&gt; a = 10^b</code></p>

<p>So if it takes <code>1</code> second to compute <code>10</code> elements, it will take <code>2</code> seconds to compute <code>100</code> elements, <code>3</code> seconds for <code>1000</code> elements, etc.</p>

<p><strong>O(log n)</strong> is when we do a divide and conquer type of algorithm (binary search).</p>

<blockquote>
  <p>log(x) refers to log2(x) in computer science and information theory <br>
  log(x) refers to log10(x) in various engineering fields, logarithm tables, and handheld calculators.</p>

  <p><strong>However</strong>, they differ by a constant so the value of the base is irrelevant since it does not change the <strong>type of growth</strong></p>
</blockquote>

<p><img src="http://i49.tinypic.com/fqcmr.png" alt="enter image description here" title=""></p>



<h2 id="onlogn"><code>O(n*log(n))</code></h2>

<p>any divide and conquer method - merge sort. <br>
using sort automatically gives a lower bound of <code>O(n*log(n)</code></p>

<p>merge sort is expensive for space complexity, creates more and more arrays.</p>



<h3 id="on2"><strong>O(n^2)</strong></h3>

<blockquote>
  <p><strong>EXAMPLES</strong></p>

  <p>1) <strong>Bubble Sort</strong> <br>
   Each element in the array, you potentially swap all the way up to the rest of the array (another <code>n</code> operations). <br>
  Every item in a list, (aka <code>n</code> for the input size), we have to do <code>n</code> more operations. So <code>n * n == n^2</code></p>
</blockquote>

<p><img src="https://justin.abrah.ms/static/images/runtime_comparison.png" alt="enter image description her" title=""></p>



<h3 id="o2n"><strong>O(2^n)</strong></h3>

<blockquote>
  <p>For each additional input, the number of basic operations doubles.</p>
</blockquote>

<hr>



<h1 id="tips">Tips</h1>

<ul>
<li>Linear time complexity is oftentimes the naive solution. <br>
<ul><li>If array is sorted, use <strong>binary-search</strong> which is <code>O(log(n))</code>.</li></ul></li>
</ul>

<hr>



<h1 id="things-to-think-about">Things to think about:</h1>

<p>When determining time complexity:</p>

<ol>
<li>What is the factor that can affect the number of questions asked (the “problem size”)?</li>
<li>In the worst case, how many questions will be asked?</li>
</ol>

<hr>



<h1 id="aside">Aside:</h1>



<h3 id="best-case"><strong>Best Case</strong></h3>

<p>How many comparisons necessary in the case for an array of <code>n</code> values? <br>
=&gt; <code>O(1)</code> <br>
<strong>Reason:</strong> As n, size of the array, grows larger, time to perform the comparison operation does not change. It is of <strong>constant time</strong> <br>
<img src="https://lh3.googleusercontent.com/-UdPEdSP89JU/VZbFpPq4k_I/AAAAAAAAAb8/W9LQ4QrAOJg/s0/Screen+Shot+2015-07-03+at+10.25.36+AM.png" alt="enter image description here" title="Screen Shot 2015-07-03 at 10.25.36 AM.png"></p>



<h3 id="average-case"><strong>Average Case</strong></h3>

<p>How many comparisons are necessary in the average case for an array of n values (assuming the target is in the array)?</p>

<p><script type="math/tex" id="MathJax-Element-1"> \frac{( 1 + 2 + ... + (n - 1) + n ) } n </script></p>
