[![.NET CI/CD Nuget](https://github.com/dahln/blazorspinner/actions/workflows/dotnet-nuget.yml/badge.svg)](https://github.com/dahln/blazorspinner/actions/workflows/dotnet-nuget.yml)
[![Azure Static Web Apps CI/CD](https://github.com/dahln/blazorspinner/actions/workflows/azure-static-web-apps-red-bay-06d0ccf10.yml/badge.svg)](https://github.com/dahln/blazorspinner/actions/workflows/azure-static-web-apps-red-bay-06d0ccf10.yml)

# BlazorSpinner

BlazorSpinner is a loading spinner that can be included in Blazor applications. It has a simple service that can be called to "show" or "hide" the spinner.

[![NuGet](https://img.shields.io/nuget/v/BlazorSpinner.svg)](https://www.nuget.org/packages/BlazorSpinner/)
[![NuGet Downloads](https://img.shields.io/nuget/dt/BlazorSpinner.svg)](https://www.nuget.org/packages/BlazorSpinner/)

# Demo

Demo link: https://red-bay-06d0ccf10.1.azurestaticapps.net

This is a screen shot of the spinner 
![Screen Shot](https://raw.githubusercontent.com/dahln/BlazorSpinner/master/BlazorSpinnerScreenShot.png)

# Basic Setup
Review the demo project for details on how to implement the spinner.

1. Install the library from Nuget: https://www.nuget.org/packages/BlazorSpinner/
2. Add "```@using BlazorSpinner```" in your _Imports.razor
3. Add "```builder.Services.AddScoped<SpinnerService>();```" in your Program.cs file
4. Add "```<Spinner></Spinner>```" to your MainLayout.razor file
5. On any page you want to call the spinner from, inject the SpinnerService into it: ```@inject BlazorSpinner.SpinnerService _spinnerService```
6. Call ```_spinnerService.Show()``` or ```_spinnerService.Hide()``` to "Show" or "Hide" the spinner.
  
Call the spinner on any long-running calls or processes (such as API calls).

# Customizing Loading Icon
You can use your own SVG for the loading icon, instead of the default spinner. 
1. Copy your SVG file into the 'wwwroot' of your application. 
2. In the MainLayout.razor, set the 'Type' parameter to 'SpinnerType.Icon' for the Spinner component.
3. In the MainLayout.razor, set the 'Icon' parameter to the path to your SVG file.
4. Example: 
    ```
    <Spinner Type="@SpinnerType.Icon" Icon="loading.svg"></Spinner>
    ```


# Customizing Loading Text
You can use your own SVG for the loading icon, instead of the default spinner. 
1. In the MainLayout.razor, set the 'Type' parameter to 'SpinnerType.Text' for the Spinner component.
3. In the MainLayout.razor, set the 'Text' parameter to the text you want
4. Example: 
    ```
    <Spinner Type="@SpinnerType.Text" Text="Processing...""></Spinner>
    ```

# v4
v4 targets .NET 10. If your application uses previous versions of .NET then use previous version of the spinner - previous versions are still available on NuGet.

# v2 => v3 Breaking Changes
The 'Loading' component and service have been merged with the 'Spinner' componet and service. Applications that have previously used the 'Loading' component and service need to be updated to use the 'Spinner' component and service. 


# Icon Source
- https://loading.io/ 
