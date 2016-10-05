<p>This document assumes you are upgrading to NUnit 3.0 from NUnit 2.6 or
later. While it's possible to upgrade from an earlier version, you will
need to take into account many additional changes in NUnit, which are not
described here. If this is your situation, be sure to check the release
notes for earlier versions of NUnit as well.</p>

<h3>Review Breaking Changes</h3>

<p>The [[Breaking Changes]] page
lists missing and changed functionality in NUnit 3.0. You should review this
page to see which items are likely to affect your own tests.</p>

<h3>Update Your Code</h3>

<p>In many cases, the items being removed have been deprecated for some time
and an alternate approach may already be available in your current release
of NUnit. If that is the case, it will probably save you time and effort if
you modify the code in your current environment before switching to NUnit 3.0.</p>

<p>For example, NUnit 3.0 no longer supports <b>ExpectedExceptionAttribute</b>.
However, preferred alternatives <b>Assert.Throws</b> and the <b>ThrowsConstraint</b>
have been available for several years. If you remove the attribute from your
tests and use one of the alternatives instead, you can verify that they work
in your present environment and they will continue to work after conversion.</b>

<h3>Switch to NUnit 3.0</h3>

<p>Remove references to your old version of NUnit and replace them with references
to NUnit 3.0. In the case of NUnitLite executable tests, you will need to reference
both the nunit.framework and nunitlite assemblies. Compile your code. It's possible 
that you will find compiler errors due to breaking changes in NUnit 3.0, which you 
missed in the prior step. Make the necessary changes until it all works.</p>

<h3>Make the Tests Pass</h3>

<p>Hopefully, you aren't converting tests that were not passing when you started!
If all goes well, they will continue to pass under NUnit 3.0. If not, investigate
each case and make necessary changes. If something isn't working as advertised,
please let us know.

