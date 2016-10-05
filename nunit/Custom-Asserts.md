##DRAFT - Out of Date

Experienced developers using NUnit generally end up with a library of custom
setup, teardown, test and support methods. Custom Asserts provide one way to
re-package such methods, allowing the normal NUnit syntax to be used to
invoke them and providing error messages that match the style and layout
of standard NUnit messages.

The standard NUnit Asserts create an object known as an <b>asserter</b> and
pass it to the <b>DoAssert</b> method, which includes code similar to this...

<pre class="prettyprint">
	if ( !asserter.Test() )
		throw new AssertionException( asserter.Message );
</pre></p>

<p><b>Asserters</b> encapsulate the comparison to be performed as well as the
objects being compared. They implement the <b>IAsserter</b> interface, 
defined as follows:

<pre class="prettyprint">
	public interface IAsserter
	{
		// Test the condition for the assertion.
		bool Test();

		// Return the message giving the failure reason.
		string Message { get; }
	}
</pre></p>

<p>When implementing an <b>asserter</b>, you will have to decide on an approach
for creating the message. For complex tests, it may be necessary to create
and cache the message - or info used to create it - while the test is
being performed. For example, when NUnit compares arrays, it notes the
point of failure for use in the message. Otherwise, it would have to 
pass the entire array a second time.</p>

<p>Generally, the constructor for the <b>asserter</b> will include any required
parameters, the actual value and an optional user message. You may invoke
the asserter directly, using <b>Assert.DoAssert</b>, but it is generally more 
convenient and readable to create an class similar to NUnit's <b>Assert</b> class,
which contains static methods that wrap the object creation. For an example of 
how to do this, see the <b>StringAssert</b> class in the NUnit source.</p>
