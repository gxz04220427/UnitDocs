<p>The <b>PairwiseAttribute</b> is used on a test to specify that NUnit should
   generate test cases in such a way that all possible pairs of
   values are used. This is a well-known approach for combatting
   the combinatorial explosion of test cases when more than
   two features (parameters) are involved.
   
<h4>Example</h4>

<p>Using the Combinatorial attribute, the following test would be executed 12 (3x2x2) times.
   With <b>Pairwise</b> it is executed only enough times so that each possible pair is covered..

```C#
[Test, Pairwise]
public void MyTest(
    [Values("a", "b", "c")] string a,
    [Values("+", "-")] string b,
    [Values("x", "y")] string c)
{
    Console.WriteLine("{0} {1} {2}", a, b, c);
}
```

<p>For this test, NUnit currently calls the method six times, producing the following output:

```
	a + y
	a - x
	b - y
	b + x
	c - x
	c + y
```

<p>Note that this is not the optimal output. The pairs (-, x) and (+, y)
appear twice. NUnit uses a heuristic algorithm to reduce the number of test cases as much
as it can. Improvements may be made in the future.

<h4>Limitations</h4>

<p>When used on a generic method the programmer must ensure that all
   possible combinations of arguments are valid. When multiple parameters
   use the same generic type (e.g.: T) this may not be possible and the
   attribute may generate invalid test cases.
    
<h4>See also...</h4>
 * [[Sequential Attribute]]
 * [[Combinatorial Attribute]]
