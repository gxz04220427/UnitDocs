<p>The <b>SequentialAttribute</b> is used on a test to specify that NUnit should
   generate test cases by selecting individual data items provided
   for the parameters of the test, without generating additional
   combinations.
   
<p><b>Note:</b> If parameter data is provided by multiple attributes,
the order in which NUnit uses the data items is not guaranteed. However,
it can be expected to remain constant for a given runtime and operating
system. For best results with <b>SequentialAttribute</b> use only one
data attribute on each parameter.
   
<h4>Example</h4>

<p>The following test will be executed three times.

```C#
[Test, Sequential]
public void MyTest(
    [Values(1,2,3)] int x,
    [Values("A","B")] string s)
{
    ...
}
```

<p>MyTest is called three times, as follows:

```
	MyTest(1, "A")
	MyTest(2, "B")
	MyTest(3, null)
```

<h4>See also...</h4>
 * [[Combinatorial Attribute]]
 * [[Pairwise Attribute]]
