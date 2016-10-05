The **Assert.Ignore** method provides you with the ability to dynamically cause a
test or suite to be ignored at runtime. It may be called in a test, setup or
fixture setup method. We recommend that you use this only in isolated cases.
The category facility is provided for more extensive inclusion or exclusion of
tests or you may elect to simply divide tests run on different occasions into
different assemblies.

```C#
Assert.Ignore();
Assert.Ignore( string message, params object[] parms );
```

####See also...
 * [[Assert.Pass]]
 * [[Assert.Fail]]
 * [[Assert.Inconclusive]]
