# .NET 10.0 Upgrade Plan

## Execution Steps

Execute steps below sequentially one by one in the order they are listed.

1. Validate that a .NET 10.0 SDK required for this upgrade is installed on the machine and if not, help to get it installed.
2. Ensure that the SDK version specified in global.json files is compatible with the .NET 10.0 upgrade.
3. Upgrade BlazorSpinner\BlazorSpinner.csproj
4. Update or create .github\workflows\dotnet-nuget.yml for NuGet package CI/CD
5. Update or create .github\workflows\azure-static-web-apps.yml to only trigger on Demo changes

## Settings

This section contains settings and data used by execution steps.

### Excluded projects

Table below contains projects that belong to the dependency graph for selected projects and should not be included in the upgrade.

| Project name                                   | Description                                        |
|:-----------------------------------------------|:--------------------------------------------------:|
| Demo\Demo.csproj                               | Azure Static Web App - doesn't support .NET 10 yet |

### Aggregate NuGet packages modifications across all projects

NuGet packages used across all selected projects or their dependencies that need version update in projects that reference them.

| Package Name                                | Current Version | New Version | Description                                   |
|:--------------------------------------------|:---------------:|:-----------:|:----------------------------------------------|
| Microsoft.AspNetCore.Components             | 8.0.1;9.0.1     | 10.0.0      | Upgrade to .NET 10.0                          |
| Microsoft.AspNetCore.Components.Web         | 8.0.1;9.0.1     | 10.0.0      | Upgrade to .NET 10.0                          |
| Microsoft.SourceLink.GitHub                 |                 | 8.0.0       | Add for enhanced debugging support            |

### Project upgrade details

This section contains details about each project upgrade and modifications that need to be done in the project.

#### BlazorSpinner\BlazorSpinner.csproj modifications

Project properties changes:
  - Target framework should be changed from `net8.0;net9.0` to `net10.0` (removing .NET 8 and 9 support - breaking change)
  - Version should be updated to `4.0.0` (major version bump due to breaking change)
  - PackageReleaseNotes should be updated to reflect .NET 10 upgrade and removal of .NET 8/9 support

NuGet packages changes:
  - Microsoft.AspNetCore.Components should be updated to `10.0.0` (remove conditional versions for net8.0/net9.0)
  - Microsoft.AspNetCore.Components.Web should be updated to `10.0.0` (remove conditional versions for net8.0/net9.0)
  - Add Microsoft.SourceLink.GitHub `8.0.0` for source linking support

Enhanced NuGet package metadata:
  - Add PackageReadmeFile pointing to README.md
  - Change PackageLicenseExpression to `MIT` (replace PackageLicense URL)
  - Add IncludeSymbols set to `true`
  - Add SymbolPackageFormat set to `snupkg`
  - Add PublishRepositoryUrl set to `true`
  - Add EmbedUntrackedSources set to `true`
  - Add ItemGroup to include README.md in package

GitHub Actions changes:
  - Create or update `.github\workflows\dotnet-nuget.yml` with:
    - Setup .NET for both 9.0.x and 10.0.x
    - Trigger on master branch pushes to BlazorSpinner/** and workflow file paths
    - Trigger on version tags (v*.*.*)
    - Include restore, build, test, pack, and publish steps
    - Create GitHub releases on publish
  - Update or create `.github\workflows\azure-static-web-apps.yml` to only trigger when:
    - Demo/** files change
    - Associated workflow file changes
