<p>Normally, a configuration file used to provide settings or to control the environment 
in which tests are run, should be given the name as the assembly file with the
suffix ".config" added. For example, the configuration file used to run nunit.tests.dll must
be named nunit.tests.dll.config and located in the same directory as the dll.

<p>For multiple assemblies specified by a project, such as an NUnit or Visual Studio
project, the same rule is used unless command-line options are used to load the project
assemblies into a common AppDomain. In that case, the name of the project file is used,
with ".config" added. For example, the command

```
    nunit-console MyProject.nunit /process:Separate /domain:Single
```

would make use of the config file MyProject.nunit.config.

