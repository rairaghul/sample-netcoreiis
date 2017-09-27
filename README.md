# Sample WebAPI .NET Core application Running in IIS

The repository contains a basic .NET Core WebAPI template provided by Microsoft with the additional configuration required in order to run in IIS. Additionally, an Apprenda archive is provided if you wish to deploy to an Apprenda environment with .NET Core Web Server Hosting Bundled installed (https://aka.ms/dotnetcore.2.0.0-windowshosting).

NOTE: If your server does not have access to the Internet, you will need to first install manually the Microsoft Visual C++ 2015 Redistributable Update 3 from https://www.microsoft.com/en-us/download/details.aspx?id=53840

# Deploying to IIS

In order to deploy a .NET Core application to IIS, you simply need to add the following to your code:

1. Update the startup code in Program.cs to look as follows:

`var host = new WebHostBuilder()
    .UseKestrel()
    .UseContentRoot(Directory.GetCurrentDirectory())
    .UseIISIntegration()
    .UseStartup<Startup>()
    .Build();`

2. Add the following dependency, Microsoft.AspNetCore.Server.IISIntegration to your application csproj file as follows:

`<ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.All" Version="2.0.0" />
    <PackageReference Include="Microsoft.AspNetCore.Server.IISIntegration" Version="2.0.0"/>
</ItemGroup>`

3. You can then build and publish your application. 
4. In order to create an Apprenda archive, package the contents of the `bin\Debug\netcoreapp2.0\publish` directory into the root portion of your archive (under interfaces) and zip up the contents. For more information on manually building an archive, please refer to: http://docs.apprenda.com/7-0/creating-app-archives
5. Once you launch the application, navigate to *URL/api/values*

An archive is provided as part of this repository. 

