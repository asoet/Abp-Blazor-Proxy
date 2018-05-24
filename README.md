# Blazor-Proxy-generator
With this project you can create a proxy file for your blazor application using the ASP.NET with or without the [ABP framework ](https://aspnetboilerplate.com/). 
# Use


1. Add ```<DotNetCliToolReference Include="DotnetBlazorProxy" Version="0.1.2" />``` in your .csproj.
2. Add the generateBlazorProxies project as post build in your server project:
```
<Target Name="PostBuild" AfterTargets="PostBuildEvent">
    <Exec Condition=" '$(Configuration)'=='Debug' " Command="dotnet blazorproxy -ta $(TargetPath) -tbp $(SolutionDir) -od $(SolutionDir)\Shared\ -oa $(SolutionDir)\Shared\bin\Debug\netstandard2.0\Shared.dll -n ASO" />
    </Target>
 ```
 
arguments:
* -ta target assembly path. In this assembly is the startup file. path to dll.
* -tbp target base path. This is the path of all the return and parameter types to find and copy to the output dir.
* -n all the namespaces (or part of) of the return and parameter types to find and copy
* -od output path. All the files will be copied to this path. For example the shared library.
* -oa this is the assembly (dll) of the output project, to check if the return/parameter type already exists. 

When .NET core 2.1 is released I will release a global tool.

