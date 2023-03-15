# GPT

## Version 1
```yaml
name: Build and Publish
on: [push]
jobs:
  build:
    runs-on: windows-latest
    steps:
    - uses: actions/checkout@v2
    - name: Setup MSBuild
      uses: microsoft/setup-msbuild@v1.0.2
    - name: Build
      run: |
        msbuild /p:Configuration=Release
    - name: Publish to GitHub Packages
      uses: actions/upload-artifact@v2
      with:
        name: MyApplication
        path: bin/Release/MyApplication.exe
```

## Version 2
```yaml
name: Build and Publish
on: [push]
jobs:
  build:
    runs-on: windows-latest
    steps:
    - uses: actions/checkout@v2
    - name: Setup MSBuild
      uses: microsoft/setup-msbuild@v1.0.2
      with:
        msbuild-version: '16.0'
    - name: Build
      run: |
        msbuild /p:Configuration=Release
    - name: Publish to GitHub Packages
      uses: actions/upload-artifact@v2
      with:
        name: MyApplication
        path: bin/Release/MyApplication.exe
```

## Version 3
```yaml
name: Build and Publish
on: [push]
jobs:
  build:
    runs-on: windows-latest
    steps:
    - uses: actions/checkout@v2
    - name: Setup MSBuild
      uses: microsoft/setup-msbuild@v1.0.2
      with:
        msbuild-version: '16.0'
    - name: Build
      run: |
        msbuild /p:Configuration=Release
    - name: Publish to GitHub Packages
      uses: actions/upload-artifact@v2
      with:
        name: MyApplication
        path: bin/Release/MyApplication.exe
```

## Version 4
```yaml
name: Build and Publish
on: [push]
jobs:
  build:
    runs-on: windows-latest
    steps:
    - uses: actions/checkout@v2
    - name: Setup MSBuild
      uses: microsoft/setup-msbuild@v1.0.2
      with:
        msbuild-version: '16.0'
    - name: Install .NET Framework 4.8
      run: |
        choco install dotnetfx
    - name: Build
      run: |
        msbuild /t:Restore
        msbuild /t:Build /p:Configuration=Release
    - name: Publish to GitHub Packages
      uses: actions/upload-artifact@v2
      with:
        name: MyLibrary
        path: bin/Release/MyLibrary.dll
```

## Version 5

```yaml
name: Build and Publish
on: [push]
jobs:
  build:
    runs-on: windows-latest
    steps:
    # Checkout the repository code
    - uses: actions/checkout@v2
    # Set up MSBuild with the appropriate version
    - name: Setup MSBuild
      uses: microsoft/setup-msbuild@v1.0.2
      with:
        msbuild-version: '16.0'
    # Install the .NET Framework 4.8 runtime
    - name: Install .NET Framework 4.8
      run: |
        choco install dotnetfx
    # Build the solution, restoring NuGet packages first
    - name: Build
      run: |
        msbuild /t:Restore
        msbuild /t:Build /p:Configuration=Release
    # Publish each built artifact to GitHub Packages
    - name: Publish to GitHub Packages
      uses: actions/upload-artifact@v2
      with:
        # Name the artifact based on the project name and configuration
        name: MyLibrary1-Release
        # Set the output path to the built DLL file for the project
        path: src/MyLibrary1/bin/Release/MyLibrary1.dll
    - name: Publish to GitHub Packages
      uses: actions/upload-artifact@v2
      with:
        # Name the artifact based on the project name and configuration
        name: MyLibrary2-Release
        # Set the output path to the built DLL file for the project
        path: src/MyLibrary2/bin/Release/MyLibrary2.dll
```

## Version 6

```yaml
name: Build and Publish
on: [push]
jobs:
  build:
    runs-on: windows-latest
    steps:
    # Checkout the repository code
    - uses: actions/checkout@v2
    # Set up MSBuild with the appropriate version
    - name: Setup MSBuild
      uses: microsoft/setup-msbuild@v1.0.2
      with:
        msbuild-version: '16.0'
    # Install the .NET Framework 4.8 runtime
    - name: Install .NET Framework 4.8
      run: |
        choco install dotnetfx
    # Build the solution, restoring NuGet packages first
    - name: Build
      run: |
        msbuild /t:Restore
        msbuild /t:Build /p:Configuration=Release
    # Publish each built artifact to GitHub Packages  
    - name: Publish to GitHub Packages
      uses: actions/upload-artifact@v2
      with:
        # Name the artifact based on the project name and configuration
        name: MyLibrary1-Release
        # Set the output path to the built DLL file for the project
        path: src/MyLibrary1/bin/Release/MyLibrary1.dll
        # Include the PDB file in the package
        if: success()
        continue-on-error: true
        with:
          name: MyLibrary1-Release-Symbols
          path: src/MyLibrary1/bin/Release/MyLibrary1.pdb
    - name: Publish to GitHub Packages
      uses: actions/upload-artifact@v2
      with:
        # Name the artifact based on the project name and configuration
        name: MyLibrary2-Release
        # Set the output path to the built DLL file for the project
        path: src/MyLibrary2/bin/Release/MyLibrary2.dll
        # Include the PDB file in the package
        if: success()
        continue-on-error: true
        with:
          name: MyLibrary2-Release-Symbols
          path: src/MyLibrary2/bin/Release/MyLibrary2.pdb
```

## Version 7

```yaml
name: Build and Publish
on: [push]
jobs:
  build:
    runs-on: windows-latest
    steps:
    # Checkout the repository code
    - uses: actions/checkout@v2
    # Set up MSBuild with the appropriate version
    - name: Setup MSBuild
      uses: microsoft/setup-msbuild@v1.0.2
      with:
        msbuild-version: '16.0'
    # Install the .NET Framework 4.8 runtime
    - name: Install .NET Framework 4.8
      run: |
        choco install dotnetfx
    # Build the solution, restoring NuGet packages first
    - name: Build
      run: |
        msbuild /t:Restore
        msbuild /t:Build /p:Configuration=Release /p:DebugSymbols=true /p:DebugType=full
    # Publish each built artifact to GitHub Packages
    - name: Publish to GitHub Packages
      uses: actions/upload-artifact@v2
      with:
        # Name the artifact based on the project name and configuration
        name: MyLibrary1-Release
        # Set the output path to the built DLL file for the project
        path: src/MyLibrary1/bin/Release/MyLibrary1.dll
        # Include the PDB file in the package
        if: success()
        continue-on-error: true
        with:
          name: MyLibrary1-Release-Symbols
          path: src/MyLibrary1/bin/Release/MyLibrary1.pdb
    - name: Publish to GitHub Packages
      uses: actions/upload-artifact@v2
      with:
        # Name the artifact based on the project name and configuration
        name: MyLibrary1-Debug
        # Set the output path to the built DLL file for the project
        path: src/MyLibrary1/bin/Debug/MyLibrary1.dll
        # Include the PDB file in the package
        if: success()
        continue-on-error: true
        with:
          name: MyLibrary1-Debug-Symbols
          path: src/MyLibrary1/bin/Debug/MyLibrary1.pdb
    - name: Publish to GitHub Packages
      uses: actions/upload-artifact@v2
      with:
        # Name the artifact based on the project name and configuration
        name: MyLibrary2-Release
        # Set the output path to the built DLL file for the project
        path: src/MyLibrary2/bin/Release/MyLibrary2.dll
        # Include the PDB file in the package
        if: success()
        continue-on-error: true
        with:
          name: MyLibrary2-Release-Symbols
          path: src/MyLibrary2/bin/Release/MyLibrary2.pdb
    - name: Publish to GitHub Packages
      uses: actions/upload-artifact@v2
      with:
        # Name the artifact based on the project name and configuration
        name: MyLibrary2-Debug
        # Set the output path to the built DLL file for the project
        path: src/MyLibrary2/bin/Debug/MyLibrary2.dll
        # Include the PDB file in the package
        if: success()
        continue-on-error: true
        with:
          name: MyLibrary2-Debug-Symbols
          path: src/MyLibrary2/bin/Debug/MyLibrary2.pdb          
```
