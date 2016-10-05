<p>The <b>CombinatorialAttribute</b> is used on a test to specify that NUnit should
   generate test cases for all possible combinations of the individual
   data items provided for the parameters of a test. Since this is the
   default, use of this attribute is optional.
   
<h4>Example</h4>

<p>The following test will be executed six times:

```C#
[Test, Combinatorial]
public void MyTest(
    [Values(1,2,3)] int x,
    [Values("A","B")] string s)
{
    ...
}
```

MyTest is called six times, as follows:
```
	MyTest(1, "A")
	MyTest(1, "B")
	MyTest(2, "A")
	MyTest(2, "B")
	MyTest(3, "A")
	MyTest(3, "B")
```

<h4>Limitations</h4>

<p>When used on a generic method the programmer must ensure that all
   possible combinations of arguments are valid. When multiple parameters
   use the same generic type (e.g.: T) this may not be possible and the
   attribute may generate invalid test cases.
    
<h4>See also...</h4>
 * [[Sequential Attribute]]
 * [[Pairwise Attribute]]
