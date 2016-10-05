**ThrowsConstraint** is used to test that some code, represented as a delegate,
throws a particular exception. It may be used alone, to merely test the type
of constraint, or with an additional constraint to be applied to the exception
specified as an argument.

The related [[ThrowsNothingConstraint]] simply asserts that the delegate
does not throw an exception.

####Constructors

```C#
ThrowsConstraint(Type expectedType)
ThrowsConstraint<T>()
ThrowsConstraint(Type expectedType, Constraint constraint)
ThrowsConstraint<T>(Constraint constraint)
```

####Syntax

```C#
Throws.Exception
Throws.TargetInvocationException
Throws.ArgumentException
Throws.ArgumentNullException
Throws.InvalidOperationException
Throws.TypeOf(Type expectedType)
Throws.TypeOf<T>()
Throws.InstanceOf(Type expectedType)
Throws.InstanceOf<T>()
Throws.InnerException
```


###Examples of Use

```C#
Assert.That( SomeMethod, Throws.TypeOf<ArgumentException>());
Assert.That( SomeMethod, Throws.Exception.TypeOf<ArgumentException>());
Assert.That( SomeMethod, Throws.TypeOf<ArgumentException>()
                    .With.Property("Parameter").EqualTo("myParam"));
Assert.That( SomeMethod, Throws.ArgumentException );
Assert.That( SomeMethod, Throws.TargetInvocationException
                    .With.InnerException.TypeOf<ArgumentException>());
Assert.That(() => { throw new ArgumentException(); }, Throws.ArgumentException);
```

<h4>Notes</h4>
<ol>
    <li>
        <b>Throws.Exception</b> may be followed by further constraints,
        which are applied to the exception itself as shown in the last two
        examples above. It may also be used alone to verify that some
        exception has been thrown, without regard to type. This is
        not a recommended practice since you should normally know
        what exception you are expecting.
    </li>
    <li>
        <b>Throws.TypeOf</b> and <b>Throws.InstanceOf</b> are provided
        as a shorter syntax for this common test. They work exactly like
        the corresponding forms following <b>Throws.Exception</b>.
    </li>
    <li>
        <b>Throws.TargetInvocationException</b>, <b>Throws.ArgumentException</b>
        and <b>Throws.InvalidOperationException</b> provide a shortened form
        for some common exceptions.
    </li>
    <li>
        Used alone, <b>Throws.InnerException</b> simply tests the InnerException
        value of the thrown exception. More commonly, it will be used in
        combination with a test for the type of the outer exception as shown
        in the examples above.
    </li>
</ol>