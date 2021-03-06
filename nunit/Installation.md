To get a copy of the NUnit 3, you can use various installation approaches.

1.  Zip file download.
2.  Full NUnit install via NuGet.
3.  NUnitLite install via NuGet.
4.  Combined Approach

### Downloading the Zip File

Download the latest binary zip from our [Download](http://nunit.org/index.php?p=download) page or from [GitHub](https://github.com/nunit/nunit/releases). Unzip the file into any convenient directory.

If you would like be able to run nunit3-console from the command line, put the bin directory, containing nunit3-console.exe on your path.

In your test assemblies, add a reference to nunit.framework.dll, using the copy in the subdirectory for the appropriate runtime version. For example, if you are targeting .NET 4.0, you should reference the framework assembly in the net-4.0 subdirectory.

Run nunit3-console from the command line, giving it the path to your test assembly. To run NUnit's own framework tests from within the NUnit bin directory, enter:

```
     nunit3-console net-2.0/nunit.framework.tests.dll
```

### Using NuGet Packages

In Visual Studio, from the Tools menu, select NuGet Package Manager | Manage NuGet packages for solution...

Scroll or use search to locate the **NUnit** and **NUnit.Console** packages. Install both packages. The **NUnit** package should be referenced by each of your test assemblies, but not by any others.

Locate nunit3-console in the **packages\NUnit.3.X.X\tools** directory under your solution. This is the location from which you must run nunit3-console when using this approach. We recommend you only use this approach when running under the control of a script on your build server.

### Using NuGet NUnitLite Package

The NUnitLite approach provides a way to run NUnit tests without a full install of the NUnit runner and test engine assemblies. Only the framework and a small runner program are installed. Note that this is currently the only way to run tests under Silverlight 5.0 or the compact framework.

In Visual Studio, from the Tools menu, select NuGet Package Manager | Manage NuGet packages for solution...

Scroll or use search to locate the **NUnitLite Version 3** and install it. The package should be referenced by each of your test assemblies, but not by any others.

As a result of your installation, a file named "Program.cs" will have been copied into each of your test projects. NUnitLite test projects are console applications and this file contains the Main() program for your tests. If you already have a Main() in some other class, you may delete the file. This file also contains comments describing how the main should call the NUnitLite runner.

To run your tests, simply run your executable test assembly. No other runner is needed.

### Combined Approach

This approach is useful if you would like to use a single copy of nunit3-console with individual copies of the framework in each project.

Simply follow the zip file procedure to get a central copy of NUnit on your system. Then install the **NUnit Version 3** NuGet package in each of your test assemblies. For desktop use by developers, this approach may give you the best of both worlds.