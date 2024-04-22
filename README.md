# ReactorObfuscation GitHub Action

This is a workflow to integrate [Eziriz .NET Reactor](https://www.eziriz.com/dotnet_reactor.htm) obfuscator into your build actions. 

This GitHub Action allows you to automate the obfuscation of .NET assemblies using .NET Reactor directly within your GitHub Actions workflows. This action supports running on Windows, Linux, and macOS, making it versatile for cross-platform .NET development environments.

## Features

- **Cross-Platform Support:** Run obfuscation on Windows, Linux, and macOS.
- **Flexible Inputs:** Specify custom paths to project files, input assemblies, output locations, and license files.
- **Easy Integration:** Seamlessly integrates with existing .NET projects and GitHub Actions workflows.

## Current Version

The action uses dotNET Reactor version 6.9.8.0. Ensure that your project is compatible with this version of .NET Reactor.

## Inputs

This action requires the following inputs:

- `project_file`: The path to the .NET Reactor project file. This file contains the configuration for the obfuscation process.
- `input_path`: The path to the .NET assembly (.dll or .exe) that you want to obfuscate.
- `output_path`: The destination path where the obfuscated assembly will be saved.
- `license_file`: (Optional) The path to the license file necessary for running .NET Reactor. If omitted, .NET Reactor will run without a license file.
- `version`: (Optional) Specifies the version of .NET Reactor to use. Defaults to "latest". Use specific version numbers to target a particular release.
- `additional_params`: (Optional) Additional command line parameters to pass to the .NET Reactor CLI. This can be used to customize the obfuscation process further.


## Usage

Here's how to use the ReactorObfuscation action in your workflow:

```yaml
name: .NET Build and Obfuscate
on:
  push:
    branches:
      - main
jobs:
  build_and_obfuscate:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3

    - name: Setup .NET Core
      uses: actions/setup-dotnet@v2
      with:
        dotnet-version: '8.0.x'

    - name: Build .NET Project
      run: dotnet build --configuration Release

    - name: Obfuscate .NET Assembly
      uses: DanielBunting/ReactorObfuscation@v0.0.1
      with:
        project_file: 'path/to/your/project.nrproj'
        input_path: 'path/to/your/output/assembly.dll'
        output_path: 'path/to/your/output/assembly.dll'
        license_file: 'path/to/your/license.license'

```

## Support and Contributions
- Getting Support: If you encounter any issues while using this action, please open an issue in the GitHub repository.
- Contributions: Contributions are welcome! If you'd like to improve this action, please make a pull request.
## License
- This project is licensed under the MIT Licence - see the LICENSE file in the repository for details.