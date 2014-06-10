---
layout: lesson
root: ../..
---

## Making Choices


<div class="">
<p>Our previous lessons have shown us how to manipulate data,
define our own functions,
and repeat things.
However,
the programs we have written so far always do the same things,
regardless of what data they&#39;re given.
We want programs to make choices based on the values they are manipulating.
To help us see what decisions they&#39;re making,
we&#39;ll start by looking at how computers manipulate images.</p>
</div>


<div class="objectives">
<h4 id="objectives">Objectives</h4>
<ul>
<li>Explain the similarities and differences between tuples and lists.</li>
<li>Write conditional statements including <code>if</code>, <code>elif</code>, and <code>else</code> branches.</li>
<li>Correctly evaluate expressions containing <code>and</code> and <code>or</code>.</li>
<li>Correctly write and interpret code containing nested loops and conditionals.</li>
<li>Explain the advantages of putting frequently-modified code in a function.</li>
</ul>
</div>

### Conditionals


<div class="">
<p>The other thing we need in order to create a heat map of our own
is a way to pick a color based on a data value.
The tool Python gives us for doing this is called a <a href="../../gloss.html#conditional-statement">conditional statement</a>,
and looks like this:</p>
</div>


<div class="in">
<pre>num = 37
if num &gt; 100:
    print &#39;greater&#39;
else:
    print &#39;not greater&#39;
print &#39;done&#39;</pre>
</div>

<div class="out">
<pre>not greater
done
</pre>
</div>


<div class="">
<p>The second line of this code uses the keyword <code>if</code> to tell Python that we want to make a choice.
If the test that follows it is true,
the body of the <code>if</code>
(i.e., the lines indented underneath it) are executed.
If the test is false,
the body of the <code>else</code> is executed instead.
Only one or the other is ever executed:</p>
</div>


<div class="">
<p><img src="img/python-flowchart-conditional.svg" alt="Executing a Conditional" /></p>
</div>


<div class="">
<p>Conditional statements don&#39;t have to include an <code>else</code>.
If there isn&#39;t one,
Python simply does nothing if the test is false:</p>
</div>


<div class="in">
<pre>num = 53
print &#39;before conditional...&#39;
if num &gt; 100:
    print &#39;53 is greater than 100&#39;
print &#39;...after conditional&#39;</pre>
</div>

<div class="out">
<pre>before conditional...
...after conditional
</pre>
</div>


<div>
<h4 id="challenges">Challenges</h4>
<ol>
<li>Define a variable <code>x</code> and set it to some number.<br>Write a statement that prints &quot;X is even&quot; or &quot;X is odd&quot; depending on the value of the variable <code>x</code>.</li>
</ol>
</div>


<div class="in">
<pre># Hint: There is an operator called &#34;modulo&#34; that is expressed as a % 
# sign that evaluates to the remainder after integer division.

print 0 % 2
print 1 % 2
print 2 % 2
print 3 % 2  # See where this is going?</pre>
</div>


<div class="in">
<pre></pre>
</div>


<div class="">
<p>We can also chain several tests together using <code>elif</code>,
which is short for &quot;else if&quot;.
This makes it simple to write a function that returns the sign of a number:</p>
</div>


<div class="in">
<pre>def sign(num):
    if num &gt; 0:
        return 1
    elif num == 0:
        return 0
    else:
        return -1

print &#39;sign of -3:&#39;, sign(-3)</pre>
</div>

<div class="out">
<pre>sign of -3: -1
</pre>
</div>


<div class="">
<p>One important thing to notice the code above is that we use a double equals sign <code>==</code> to test for equality
rather than a single equals sign
because the latter is used to mean assignment.
This convention was inherited from C,
and while many other programming languages work the same way,
it does take a bit of getting used to...</p>
<p>We can also combine tests using <code>and</code> and <code>or</code>.
<code>and</code> is only true if both parts are true:</p>
</div>


<div class="in">
<pre>if (1 &gt; 0) and (-1 &gt; 0):
    print &#39;both parts are true&#39;
else:
    print &#39;one part is not true&#39;</pre>
</div>

<div class="out">
<pre>one part is not true
</pre>
</div>


<div class="">
<p>while <code>or</code> is true if either part is true:</p>
</div>


<div class="in">
<pre>if (1 &lt; 0) or (&#39;left&#39; &lt; &#39;right&#39;):
    print &#39;at least one test is true&#39;</pre>
</div>

<div class="out">
<pre>at least one test is true
</pre>
</div>


<div class="">
<p>In this case,
&quot;either&quot; means &quot;either or both&quot;, not &quot;either one or the other but not both&quot;.</p>
</div>


<div class="challenges">
<h4 id="challenges">Challenges</h4>
<ol>
<li><p><code>True</code> and <code>False</code> aren&#39;t the only values in Python that are true and false.
In fact, <em>any</em> value can be used in an <code>if</code> or <code>elif</code>.
After reading and running the code below,
explain what the rule is for which values are considered true and which are considered false.
(Note that if the body of a conditional is a single statement, we can write it on the same line as the <code>if</code>.)</p>
<pre><code class="language-python"><span class="keyword">if</span> <span class="string">''</span>: <span class="keyword">print</span> <span class="string">'empty string is true'</span>
<span class="keyword">if</span> <span class="string">'word'</span>: <span class="keyword">print</span> <span class="string">'word is true'</span>
<span class="keyword">if</span> []: <span class="keyword">print</span> <span class="string">'empty list is true'</span>
<span class="keyword">if</span> [<span class="number">1</span>, <span class="number">2</span>, <span class="number">3</span>]: <span class="keyword">print</span> <span class="string">'non-empty list is true'</span>
<span class="keyword">if</span> <span class="number">0</span>: <span class="keyword">print</span> <span class="string">'zero is true'</span>
<span class="keyword">if</span> <span class="number">1</span>: <span class="keyword">print</span> <span class="string">'one is true'</span>
</code></pre>
</li>
<li><p>Write a function called <code>near</code> that returns <code>True</code> if its first parameter is within 10% of its second
and <code>False</code> otherwise.
Compare your implementation with your partner&#39;s:
do you return the same answer for all possible pairs of numbers?</p>
</li>
</ol>
</div>


<div>
<p>Working with data</p>
</div>


<div>
<p>Python has some basic data structures that allow storage of more than one variable.<br>The list is one of these.  We can create a list using square brackets [] and commas.</p>
</div>


<div class="in">
<pre>numbers = [-5, 3, 2, -1, 9, 6]</pre>
</div>


<div>
<p>We can use a for loop to give us each of these items one at a time.</p>
</div>


<div class="in">
<pre>for n in numbers:
    print n</pre>
</div>


<div>
<p>Challenge:  see if you can write a for loop to find the sum of all the numbers in the 
list <code>numbers</code>.</p>
</div>

### Nesting


<div class="">
<p>Another thing to realize is that <code>if</code> statements can be combined with loops
just as easily as they can be combined with functions.
For example,
if we want to sum the positive numbers in a list,
we can write this:</p>
</div>


<div class="in">
<pre>numbers = [-5, 3, 2, -1, 9, 6]
total = 0
for n in numbers:
    if n &gt;= 0:
        total = total + n
print &#39;sum of positive values:&#39;, total</pre>
</div>

<div class="out">
<pre>sum of positive values: 20
</pre>
</div>


<div class="">
<p>We could equally well calculate the positive and negative sums in a single loop:</p>
</div>


<div class="in">
<pre>pos_total = 0
neg_total = 0
for n in numbers:
    if n &gt;= 0:
        pos_total = pos_total + n
    else:
        neg_total = neg_total + n
print &#39;negative and positive sums are:&#39;, neg_total, pos_total</pre>
</div>

<div class="out">
<pre>negative and positive sums are: -6 20
</pre>
</div>


<div class="">
<p>We can even put one loop inside another:</p>
</div>


<div class="in">
<pre>for consonant in &#39;bcd&#39;:
    for vowel in &#39;ae&#39;:
        print consonant + vowel</pre>
</div>

<div class="out">
<pre>ba
be
ca
ce
da
de
</pre>
</div>


<div class="">
<p>As the diagram below shows,
the <a href="../../gloss.html#inner-loop">inner loop</a> runs from start to finish
each time the <a href="../../gloss.html#outer-loop">outer loop</a> runs once:</p>
</div>


<div class="">
<p><img src="img/python-flowchart-nested-loops.svg" alt="Execution of Nested Loops" /></p>
</div>


<div>
<h4 id="parsing-a-datafile">Parsing a datafile</h4>
</div>


<div>
<p><code>for</code> loops have a few essential parts:</p>
<ol>
<li>The keyword for</li>
<li>a <em>dummy variable</em> that is assigned at the start of each iteration</li>
<li>the keyword in</li>
<li>a python object that is iterable--it must know how to give the first item and the following item.</li>
<li>a colon and a newline</li>
<li>an indented block
If any of these are missing, python will report a SyntaxError.</li>
</ol>
<p>Many python data structures in addition to strings, files, and lists are iterable, and for loops have the same structure.</p>
</div>


<div class="in">
<pre>#  This code snippet opens a file and prints the lines on at a time.
datafile = open(&#39;small-01.csv&#39;)
for line in datafile:
    print line</pre>
</div>

<div class="out">
<pre>0,0,1

0,1,2

</pre>
</div>


<div class="">

</div>


<div class="">
<p>Suppose we want to add all the numbers in all the columns of every line of the file.   Our <code>line</code> variable, unfortuately, is a string, not a list of numbers.  We can convert it to a slist of numbers like this:</p>
</div>


<div class="">
<p>line.strip().split(&quot;,&quot;)</p>
</div>


<div class="">
<h4 id="challenge-">Challenge:</h4>
<p>find out what <code>strip()</code> did just here.</p>
</div>


<div class="in">
<pre>#  This code snippet opens a file and prints the lines on at a time.
datafile = open(&#39;small-01.csv&#39;)
for line in datafile:
    print line.strip.split()
</pre>
</div>


<div class="in">
<pre>#### Challenge:  
write a function that takes a comma-separated filename as an argument and 
returns the sum of all the numbers in the file.</pre>
</div>


<div class="keypoints">
<h4 id="key-points">Key Points</h4>
<ul>
<li>Use <code>if condition</code> to start a conditional statement, <code>elif condition</code> to provide additional tests, and <code>else</code> to provide a default.</li>
<li>The bodies of the branches of conditional statements must be indented.</li>
<li>Use <code>==</code> to test for equality.</li>
<li><code>X and Y</code> is only true if both X and Y are true.</li>
<li><code>X or Y</code> is true if either X or Y, or both, are true.</li>
<li>Zero, the empty string, and the empty list are considered false; all other numbers, strings, and lists are considered true.</li>
<li>Nest loops to operate on multi-dimensional data.</li>
<li>Put code whose parameters change frequently in a function, then call it with different parameter values to customize its behavior.</li>
</ul>
</div>


<div class="">
<h4 id="next-steps">Next Steps</h4>
<p>As the functions we write get longer, the chances that we&#39;ve done everything correctly go to zero.
Before we go any further,
we need to learn how to test whether our code is doing what we want it to do,
and that will be the subject of the next lesson.</p>
</div>
