# BlazorSpinner

BlazorSpinner is a loading spinner that can be included in Blazor applications. It has a simple service that can be called to "show" or "hide" the spinner.

# Setup

1. Install the library from Nuget: https://www.nuget.org/packages/BlazorSpinner/
2. Add "@using BlazorSpinner" in your _Imports.razor
3. Add "builder.Services.AddScoped<SpinnerService>();" in your Program.cs file
4. Add "<Spinner></Spinner>" to your MainLayout.razor file
5. On any page you want to call the spinner from, inject the SpinnerService into it: @inject BlazorSpinner.SpinnerService _spinnerService
(NOTE: You can also do this in other service to, just inject it via the constructor)
6. Call _spinnerService.Show() or _spinnerService.Hide() to "Show" or "Hide" the spinner.
  
Call the spinner on any long-running calls or processes (such as API calls).

The SpinnerDemo project (part of this repo/project) demonstrates how to this spinner works: https://github.com/dahln/blazorspinner/tree/master/SpinnerDemo

This spinner is also included in "depot" a free, open-source CRM: https://github.com/dahln/depot
