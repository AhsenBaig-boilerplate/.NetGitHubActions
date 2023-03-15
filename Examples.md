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
