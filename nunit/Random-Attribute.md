<p>The <b>RandomAttribute</b> is used to specify a set of random values to be provided
   for an individual parameter of a parameterized test method. Since
   NUnit combines the data provided for each parameter into a set of
   test cases, data must be provided for all parameters if it is
   provided for any of them.
   
<p>By default, NUnit creates test cases from all possible combinations
   of the datapoints provided on parameters - the combinatorial approach.
   This default may be modified by use of specific attributes on the
   test method itself.
   
<p>RandomAttribute supports the following constructors:

```C#
public Random( int count );
public Random( int min, int max, int count );
public Random( uint min, uint max, int count );
public Random( long min, long max, int count );
public Random( ulong min, ulong max, int count );
public Random( short min, short max, int count );
public Random( ushort min, ushort max, int count );
public Random( byte min, byte max, int count );
public Random( sbyte min, sbyte max, int count );
public Random( double min, double max, int count );
public Random( float min, float max, int count );
```

In the first form, without minimum and maximum values, the attribute automatically generates values of the appropriate type for the argument, provided that using the `Randomizer` object associated with the current context. See [[Randomizer Methods]] for details.

In general, the forms that specify a minimum and maximum should be used on arguments of the same type. However, the following exceptions are supported:

* You may use an int range on arguments of type short, ushort, byte, sbyte and decimal.

* You may use a double range on arguments of type decimal.

Note that there is no constructor taking decimal values for min and max. This is because .NET does not support use of decimal in an attribute constructor.
   
<h4>Example</h4>

<p>The following test will be executed fifteen times, three times
for each value of x, each combined with 5 random doubles from -1.0 to +1.0.

```C#
[Test]
public void MyTest(
    [Values(1,2,3)] int x,
    [Random(-1.0, 1.0, 5)] double d)
{
    ...
}
```

<h4>See also...</h4>
 * [[Values Attribute]]
 * [[Range Attribute]]
 * [[Sequential Attribute]]
 * [[Combinatorial Attribute]]
 * [[Pairwise Attribute]]
