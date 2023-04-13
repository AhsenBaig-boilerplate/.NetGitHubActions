# GitHub Actions - Nuget Info

## Directory.Build.props

[Directory.Build.props](https://github.com/restsharp/RestSharp/blob/bf247946ea4fdf70cc6fc2a454041854b146eb02/src/Directory.Build.props#L8)

```xml
<Project>
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildProjectDirectory), 'RestSharp.sln'))\props\Common.props"/>
    <PropertyGroup>
        <TargetFrameworks>netstandard2.0;net471;net6.0;net7.0</TargetFrameworks>
        <PackageIcon>restsharp.png</PackageIcon>
        <PackageLicenseExpression>Apache-2.0</PackageLicenseExpression>
        <PackageProjectUrl>https://restsharp.dev</PackageProjectUrl>
        <RepositoryUrl>https://github.com/restsharp/RestSharp.git</RepositoryUrl>
        <RepositoryType>git</RepositoryType>
        <Description>Simple REST and HTTP API Client</Description>
        <Authors>.NET Foundation and Contributors</Authors>
        <UpdateVersionProperties>true</UpdateVersionProperties>
        <PublishRepositoryUrl>true</PublishRepositoryUrl>
        <IncludeSymbols>true</IncludeSymbols>
        <SymbolPackageFormat>snupkg</SymbolPackageFormat>
        <GenerateDocumentationFile>true</GenerateDocumentationFile>
        <NoWarn>$(NoWarn);1591</NoWarn>
        <LangVersion>11</LangVersion>
    </PropertyGroup>

    <ItemGroup>
        <PackageReference Include="Microsoft.SourceLink.GitHub" Version="1.1.1" PrivateAssets="All"/>
        <PackageReference Include="MinVer" Version="4.3.0" PrivateAssets="All"/>
        <PackageReference Include="JetBrains.Annotations" Version="2022.3.1" PrivateAssets="All"/>
    </ItemGroup>
    <ItemGroup>
        <None Include="$(RepoRoot)\restsharp.png" Pack="true" PackagePath="\"/>
        <Using Include="JetBrains.Annotations"/>
    </ItemGroup>
    <Target Name="CustomVersion" AfterTargets="MinVer">
        <PropertyGroup>
            <FileVersion>$(MinVerMajor).$(MinVerMinor).$(MinVerPatch)</FileVersion>
            <AssemblyVersion>$(MinVerMajor).$(MinVerMinor).$(MinVerPatch)</AssemblyVersion>
        </PropertyGroup>
    </Target>
</Project>
```

## Source code link .csproj

### Example 1
[Introducing Source Code Link for NuGet packages
](https://devblogs.microsoft.com/nuget/introducing-source-code-link-for-nuget-packages/)

[Example 2 - ](https://github.com/dotnet/project-system/blob/main/Directory.Build.props)

```xml
<PropertyGroup>
    <!-- Optional: Publish the repository URL in the built .nupkg (in the NuSpec <Repository> element) -->
    <PublishRepositoryUrl>true</PublishRepositoryUrl>
</PropertyGroup>
<ItemGroup>
  <!-- For GitHub -->
  <PackageReference Include="Microsoft.SourceLink.GitHub" Version="1.0.0-beta-63127-02" PrivateAssets="All"/>
  <!-- For Visual Studio Team Services -->
  <PackageReference Include="Microsoft.SourceLink.Vsts.Git" Version="1.0.0-beta-63127-02" PrivateAssets="All"/>
  <!-- For Team Foundation Server -->
  <PackageReference Include="Microsoft.SourceLink.Tfs.Git" Version="1.0.0-beta-63127-02" PrivateAssets="All"/>
  <SourceLinkTfsGitHost Include="tfs-server-name" VirtualDirectory="tfs"/>
  <!-- For GitLab -->
  <PackageReference Include="Microsoft.SourceLink.GitLab" Version="1.0.0-beta-63127-02" PrivateAssets="All"/>
  <!-- For BitBucket -->
  <PackageReference Include="Microsoft.SourceLink.Bitbucket.Git" Version="1.0.0-beta-63127-02" PrivateAssets="All"/>
</ItemGroup>
```

### Example 2

[PropertyGroup - Example](https://github.com/Taiizor/ReaLTaiizor/blob/develop/src/ReaLTaiizor/ReaLTaiizor.csproj)

[Example 2](https://github.com/rajanadar/VaultSharp/blob/master/src/VaultSharp/VaultSharp.csproj)
```xml
<PropertyGroup>
        <UseWindowsForms>true</UseWindowsForms>
        <ApplicationIcon>Resources\Taiizor.ico</ApplicationIcon>
        <Version>3.7.9.3</Version>
        <AssemblyVersion>$(Version)</AssemblyVersion>
        <GeneratePackageOnBuild>true</GeneratePackageOnBuild>
        <Title>ReaLTaiizor</Title>
        <PackageId>ReaLTaiizor</PackageId>
        <Authors>Taiizor</Authors>
        <Copyright>Copyright © $([System.DateTime]::Today.ToString(yyyy)) $(Authors)</Copyright>
        <Summary>ReaLTaiizor is a .NET WinForms control library that offers a wide range of components and is user-friendly and design-focused.</Summary>
        <Description>ReaLTaiizor is a user-friendly and design-focused control library for .NET WinForms projects, containing a wide range of components. You can personalize your projects with different theme options and customize user controls to make your applications more professional.</Description>
        <PackageLicenseFile>LICENSE</PackageLicenseFile>
        <PackageLicenseExpression></PackageLicenseExpression>
        <PackageRequireLicenseAcceptance>false</PackageRequireLicenseAcceptance>
        <PackageReleaseNotes>Major changes have been made.
Changes are detailed at https://github.com/Taiizor/ReaLTaiizor/releases</PackageReleaseNotes>
        <PackageTags>ReaL Taiizor Soferity Vegalya ReaLTaiizor C# CSharp VBC VB VisualBasic GUI UI UX Design Theme Forms WinForm WinForms DotNET .NET NET Component Fluent</PackageTags>
        <GenerateDocumentationFile>true</GenerateDocumentationFile>
        <!--<DocumentationFile>..\$(PackageId)\bin$(OutputPath)\$(Configuration)\$(TargetFramework)\$(PackageId).xml</DocumentationFile>-->
        <PackageProjectUrl>https://github.com/Taiizor/ReaLTaiizor</PackageProjectUrl>
        <RepositoryType>git</RepositoryType>
        <RepositoryUrl>git://github.com/Taiizor/ReaLTaiizor</RepositoryUrl>
        <PackageDescription>$(Description)</PackageDescription>
        <PackageIcon>Taiizor.png</PackageIcon>
        <Company>$(Authors)</Company>
        <Owners>$(Authors)</Owners>
        <AnalysisLevel>preview</AnalysisLevel>
        <LangVersion>preview</LangVersion>
        <NeutralLanguage>en-GB</NeutralLanguage>
        <FileVersion>$(Version)</FileVersion>
        <PublishRepositoryUrl>true</PublishRepositoryUrl>
        <EmbedUntrackedSources>true</EmbedUntrackedSources>
        <ContinuousIntegrationBuild>true</ContinuousIntegrationBuild>
        <IncludeSymbols>true</IncludeSymbols>
        <SymbolPackageFormat>snupkg</SymbolPackageFormat>
        <Configurations>Debug;GitHub;Release</Configurations>
        <NoWarn>1587,1591</NoWarn>
    </PropertyGroup>
```
## Topic
- GitHub
    - [RollerKnobster/SS-Actions-Auto-Version: SS-Actions-Auto-Version (github.com)](https://github.com/RollerKnobster/SS-Actions-Auto-Version)
    - [Connecting a repository to a package - GitHub Docs](https://docs.github.com/en/packages/learn-github-packages/connecting-a-repository-to-a-package)
    - [AhsenBaig-boilerplate/.NetGitHubActions](https://github.com/AhsenBaig-boilerplate/.NetGitHubActions/tree/main)
- .Net
    - [Customize your build - MSBuild | Microsoft Learn](https://learn.microsoft.com/en-us/visualstudio/msbuild/customize-your-build?view=vs-2022#directorybuildprops-and-directorybuildtargets)
    - [Producing Packages with Source Link - .NET Blog (microsoft.com)](https://devblogs.microsoft.com/dotnet/producing-packages-with-source-link/)
    - [Create .NET Standard and .NET Framework NuGet Packages with Visual Studio 2015 | Microsoft Learn](https://learn.microsoft.com/en-us/nuget/guides/create-net-standard-packages-vs2015)

- Sub-topic
    - [Conventional Commits: A Better Way | by Michael Collins | Neudesic Innovation | Medium](https://medium.com/neudesic-innovation/conventional-commits-a-better-way-78d6785c2e08)
    - [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/#specification)

## :star: Resources

- https://yonatankra.com/7-github-actions-tricks-i-wish-i-knew-before-i-started/
- https://garywoodfine.com/what-is-this-directory-build-props-file-all-about/
- https://docs.github.com/en/actions/learn-github-actions/contexts#inputs-context
- https://medium.com/jobtome-engineering/how-to-generate-changelog-using-conventional-commits-10be40f5826c
- https://gist.github.com/qoomon/5dfcdf8eec66a051ecd85625518cfd13
- https://github.com/github/platform-samples/tree/master/pre-receive-hooks
