[![.NET CI/CD Nuget](https://github.com/shadowlings/BlazorSpinner/actions/workflows/dotnet-nuget.yml/badge.svg)](https://github.com/shadowlings/BlazorSpinner/actions/workflows/dotnet-nuget.yml)
[![Azure Static Web Apps CI/CD](https://github.com/shadowlings/BlazorSpinner/actions/workflows/azure-static-web-apps-red-bay-06d0ccf10.yml/badge.svg)](https://github.com/shadowlings/BlazorSpinner/actions/workflows/azure-static-web-apps-red-bay-06d0ccf10.yml)

# BlazorSpinner

BlazorSpinner is a loading spinner that can be included in Blazor applications. It has a simple service that can be called to "show" or "hide" the spinner.

# Demo

Demo link: https://red-bay-06d0ccf10.1.azurestaticapps.net

This is a screen shot of the spinner 
![Screen Shot](https://github.com/dahln/blazorspinner/blob/master/BlazorSpinnerScreenShot.png)

# Setup

1. Install the library from Nuget: https://www.nuget.org/packages/BlazorSpinner/
2. Add "```@using BlazorSpinner```" in your _Imports.razor
3. Add "```builder.Services.AddScoped<SpinnerService>();```" in your Program.cs file
    - Or Add "```builder.Services.AddScoped<LoadingService>();```" in your Program.cs file
4. Add "```<Spinner></Spinner>```" to your MainLayout.razor file
    - Or Add "```<Loading></Loading>```" to your MainLayout.razor file
5. On any page you want to call the spinner from, inject the SpinnerService into it: ```@inject BlazorSpinner.SpinnerService _spinnerService```
    - Or Add  ```@inject BlazorSpinner.LoadingService _loadingService```
    - (NOTE: You can also do this in other service to, just inject it via the constructor)
6. Call ```_spinnerService.Show()``` or ```_spinnerService.Hide()``` to "Show" or "Hide" the spinner.
    - If you are using the text loading spinner, adjust this call to use the _loadingService.
  
Call the spinner on any long-running calls or processes (such as API calls).

# Credit
BlazorSpinner uses an icon (https://fontawesome.com/icons/circle-notch?style=solid) from FontAwesome. SVG is directly embedded in this library. Height, Width, Color are modified. For more details, please refer to the license at FontAwesome: https://fontawesome.com/license 
