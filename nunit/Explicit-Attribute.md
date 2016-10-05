The Explicit attribute causes a test or test fixture to be skipped unless it is 
explicitly selected for running. The test or fixture will be run if it is 
selected by name or if it is included by use of a filter. Note that a **not**
filter, which excludes certain tests, is not treated as an explicit selection
and never causes an explicit test to be run.

An optional string argument may be used to give the reason for marking
the test Explicit.

If a test or fixture with the Explicit attribute is encountered in the course of 
running tests, it is skipped unless it has been specifically selected by one
of the above means. The test does not affect the overall result of the test run.
Explicit tests are displayed in the gui as skipped.

> **Warning:** While the C# syntax allows you to place an Explicit attribute on a
SetUpFixture class, the attribute is ignored by NUnit and has no effect in current releases.
	
<h4>Test Fixture Syntax</h4>
#####C\# #####
```C#
namespace NUnit.Tests
{
  using System;
  using NUnit.Framework;

  [TestFixture, Explicit]
  public class ExplicitTests
  {
    // ...
  }
}
```

#####Visual Basic

```VB
Imports System
Imports Nunit.Framework

Namespace Nunit.Tests

  <TestFixture(), Explicit()>
  Public Class ExplicitTests
    ' ...
  End Class
End Namespace
```

#####C++
```C++
using namespace System;
using namespace NUnit::Framework;

namespace NUnitTests
{
  [TestFixture]
  [Explicit]
  public __gc class ExplicitTests
  {
    // ...
  };
}

#include "cppsample.h"

namespace NUnitTests {
  // ...
}
```

<h4>Test Syntax</h4>

#####C# #####
```C#
namespace NUnit.Tests
{
  using System;
  using NUnit.Framework;

  [TestFixture]
  public class SuccessTests
  {
    [Test, Explicit]
    public void ExplicitTest()
    { /* ... */ }
}
```

#####Visual Basic
```vb
Imports System
Imports Nunit.Framework

Namespace Nunit.Tests

  <TestFixture()> Public Class SuccessTests
    <Test(), Explicit()> Public Sub ExplicitTest()
      ' ...
    End Sub
  End Class
End Namespace
```

#####C++
```c++
#using <Nunit.Framework.dll>
using namespace System;
using namespace NUnit::Framework;

namespace NUnitTests
{
  [TestFixture]
  public __gc class SuccessTests
  {
    [Test][Explicit] void ExplicitTest();
  };
}

#include "cppsample.h"

namespace NUnitTests {
  // ...
}
```
