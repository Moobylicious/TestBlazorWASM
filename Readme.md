# Overview
This project exists to demonstrate an apparent bug in the recently available 7.0.0-rc.1.22427.2
version of the Microsoft.AspNetCore.Components.WebAssembly nuget package.

This was done in Visual Studio 2022 Community Preview V17.4.0 Preview 2.

# Steps
1. Clone this repo
2. open the .sln
3. rebuild
4. run using the "https" debug profile
5. navigate in browser to https://localhost:7102/
6. observe the blazor WASM template app.
7. Close browser & stop debugging
8. Update Nuget package Microsoft.AspNetCore.Components.WebAssembly in `TestBlazorWasm.Client` project to 7.0.0-rc.1.22427.2
9. Repeat steps 3 - 5
10. observe browser stops with "loading." on screen

The error reported in the browser console is:
``` 
Uncaught (in promise) TypeError: Cannot set properties of undefined (setting 'Blazor')
    at postRun (blazor.webassembly.js:1:44187)
    at callRuntimeCallbacks (dotnet.7.0.0-preview.6.22324.4.yh2xxb8umm.js:12:17324)
    at postRun (dotnet.7.0.0-preview.6.22324.4.yh2xxb8umm.js:12:13235)
    at doRun (dotnet.7.0.0-preview.6.22324.4.yh2xxb8umm.js:12:145716)
    at run (dotnet.7.0.0-preview.6.22324.4.yh2xxb8umm.js:12:145873)
    at runCaller (dotnet.7.0.0-preview.6.22324.4.yh2xxb8umm.js:12:145353)
    at Object.removeRunDependency (dotnet.7.0.0-preview.6.22324.4.yh2xxb8umm.js:12:14027)
    at h (blazor.webassembly.js:1:40292)
```

You can then downgrade the nuget package back to 7.0.0-preview.7.22376.6 and it works again.