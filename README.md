﻿![NuGet logo](https://raw.githubusercontent.com/NuGet/Home/dev/resources/nuget.png)

-----

# NuGet Client Tools

This repo contains the following clients:
  * [NuGet CLI](https://docs.nuget.org/ndocs/tools/nuget.exe-cli-reference)
  * [NuGet Package Manager for Visual Studio 2017](https://docs.nuget.org/ndocs/tools/package-manager-ui)
  * [PowerShell CmdLets](https://docs.nuget.org/ndocs/tools/powershell-reference)

## Open Source Code of Conduct

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## How to build NuGet client tools

### Prerequisites
- [Visual Studio 2017](https://www.visualstudio.com)
  with following workloads:
    - .NET desktop development
    - Desktop development with C++
    - Visual Studio extension development.
- [Windows 10 SDK](https://dev.windows.com/en-US/downloads/windows-10-sdk)
- Git
- Windows Powershell v3.0+
- [.NET Core SDK 1.0.5](https://github.com/dotnet/core/blob/master/release-notes/download-archives/1.0.4-sdk-download.md)

### Steps to build NuGet client tools

1. Clone [NuGet/NuGet.Client](https://github.com/nuget/nuget.client) repository

    `git clone https://github.com/NuGet/NuGet.Client`

2. Start PowerShell. CD into the cloned repository directory.

3. Run configuration script

    `.\configure.ps1`

4. Build with

    `.\build.ps1 -SkipUnitTest`
    
   Or Build and Unit test with 
   
   `.\build.ps1`

6. Run all test-suites if inside Microsoft corpnet

    `.\runTests.ps1`



> In case you have build issues try cleaning the local repository using `git clean -xdf` and retry steps 3 and 4.

#### Notable `build.ps1` switches
- `-SkipVS15` - skips building binaries targeting Visual Studio "15" (released as Visual Studio 2017)
- `-SkipUnitTest` - skips running unit tests.
- `-Fast` - runs minimal incremental build. Skips end-to-end packaging step.

> Reveal all script parameters and switches by running
  ```posh
  Get-Help .\build.ps1 -detailed
  ```

### Build artifacts location
- `$(NuGetClientRoot)\Artifacts\VS15` - this folder will contain the Package Manager extension (`NuGet.Tools.vsix`) and NuGet command-line client application (`nuget.exe`)
- `$(NuGetClientRoot)\Artifacts\nupkgs` - this folder will contain all our projects packages

## License

Unless explicitly stated otherwise all files in this repository are licensed under the License in the root repository
