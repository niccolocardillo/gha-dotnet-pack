# .NET Pack

Uses the .NET CLI `dotnet pack` [command](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-pack) to retrieve previously [build](https://github.com/codebeltnet/dotnet-build) projects and packs them into a NuGet package.

## Usage

To use this action in your GitHub repository, you can follow these steps:

```yaml
uses: niccolocardillo/dotnet-pack@v1
```

### Inputs

```yaml
with:
  # Defines the build configuration.
  configuration: 'Release'
  # Sets the verbosity level of the command. Allowed values are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].
  level: 'quiet'
  # When set, the package name will be automatically generated from the project name.
  packageNameAuto: false
  # Defines the name of the nuget package (the complete name is packageName.version).
  packageName: 'package'
  # The version of your project, e.g. 1.0.0.
  packageVersion: '1.0.0'
  #Optional path to the project(s).
  projects:
  # When set, current workspace will be overwritten with the content of the restore cache.
  restoreCacheKey: ''
  # Duration after which artifact will expire in days.Default is 1.
  retentionDaysArtifact: '1'
  # Upload the created NuGet packages.
  uploadPackedArtifact: 'false'
```

### Outputs

This action has no outputs.

## Examples

### Pack and Upload for Release configuration

```yaml
- name: Pack for Release
  uses: niccolocardillo/gha-dotnet-pack@v1
  with:
    configuration: Release
    uploadPackedArtifact: true
    packageVersion: ${{ needs.build.outputs.version }}
```

## Contributing to .NET Pack

Contributions are welcome! 
Feel free to submit issues, feature requests, or pull requests to help improve this action.

### License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.