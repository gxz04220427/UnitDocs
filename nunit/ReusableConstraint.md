Normally constraints just work. However, attempting to reuse the 
same constraint in several places can lead to unexpected results.

Consider the following code as an example:

```C#
    Constraint myConstraint = Is.Not.Null;
    Assert.That("not a null", myConstraint); // Passes, of course
    Assert.That("not a null", myConstraint); // Fails! What's that about?
```

We'll save the technical explanation for later and show the
solution first:

```C#
    ReusableConstraint myConstraint = Is.Not.Null;
    Assert.That("not a null", myConstraint); // Passes
    Assert.That("not a null", myConstraint); // Passes
```

Or alternatively..

```C#
    var myConstraint = new ReusableConstraint(Is.Not.Null);
    Assert.That("not a null", myConstraint); // Passes
    Assert.That("not a null", myConstraint); // Passes
```

###Technical Explanation

In the original example, the value assigned to myConstraint is
known as an <b>unresolved</b> constraint. In fact, it's an
unresolved NullConstraint, because that was the last constraint 
encountered in the expression. It's associated with a <b>Not</b>
operator that has not yet been applied.

That's OK for use with Assert.That(), because the method
knows how to resolve a constraint before using it. Assert.That()
resolves this constraint to a NotConstraint referencing the
original NullConstraint.

Of course, the original reference in myConstraint is left
unchanged in all of this. But the EqualConstraint it points
to has now been resolved. It is now a <b>resolved</b> constraint
and can't be resolved again by the second Assert.That(), which
only sees the NullConstraint and not the NotConstraint.

So, for reusability, what we want to save is the result
of resolving the constraint, in this case

```C#
    NotConstraint => NullConstraint
```

That's what <b>ReusableConstraint</b> does for us. It resolves
the full expression and saves the result. Then it passes all
operations on to that saved result.

<h3>When to Use It</h3>

Use this constraint any time you want to reuse a constraint
expression and you'll be safe.

If you like to take chances, you'll find that you can
avoid using it in the following cases...

<ol>
<li> With a simple constraint involving no operators, like...

```C#
    Constraint myConstraint = Is.Null;
    Constraint myConstraint = Is.EqualTo(42);
```

<li> With any constraint you construct using new, without
using the "dotted" constraint syntax...

```C#
    Constraint myConstraint = new NotConstraint(new NullConstraint());
    Constraint myConstraint = new AndConstraint(
        new GreaterThanConstraint(0), 
        new LessThanConstraint(100));
```

However, there is no significant penalty to using <b>ReusableConstraint</b>.
It makes your intent much clearer and the exceptions listed are accidents of
the internal implementation and could disappear in future releases.

