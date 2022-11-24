# BlazorWebView
A [WebKitGtkSharp](https://github.com/GtkSharp/GtkSharp) WebView for running [Blazor Hybrid](https://learn.microsoft.com/en-us/aspnet/core/blazor/hybrid/) applications.

## Why?
GtkSharp's WebKit implementation is currently [incomplete](https://github.com/GtkSharp/GtkSharp/pull/274).  I don't understand how GtkSharp's codegen works, and GtkSharp doesn't to seem to get much frequent attention from its developers, so BlazorWebView provides an alternative.  It'd probably be best to move [GTKSharp's PR #274](https://github.com/GtkSharp/GtkSharp/pull/274) along, but this provides an alternative and a proof of concept until then.

## How?
BlazorWebView uses some of the same code as [Steve Sanderson's WebWindow](https://github.com/SteveSandersonMS/WebWindow) and leverages [Microsoft's WebView infrastructore](https://github.com/dotnet/aspnetcore/tree/main/src/Components/WebView) to get Blazor Hybrid working.  However, it differs from WebWindow in that it doesn't require one to compile a native shared library in C++, instead utilizing P/Invoke to call into the native libraries.   This has the benefit that, as long as the native libraries are installed on the Linux system, one only needs to use the `dotnet` CLI to build and run BlazorWebWindow.

## Usage
```
git clone https://github.com/JinShil/BlazorWebView.git
cd BlazorWebView/src
dotnet run
```

## Status
This poject was tested on the Windows Subsystem for Linux, Raspberry Pi Bullseye 64-bit, and Debian Bullseye 64-bit.  In the [src.vscode] directory the necessary configuration to build, deploy, and debug a Raspberry Pi from a Debian Bullseyse 64-bit workstation PC can be found.

BlazorWebView has only been tested the most basic Counter component, so it really only serves as a working proof of concept at this time.
