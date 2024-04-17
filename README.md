# ReactorObfuscation GitHub Action
The ReactorObfuscation GitHub Action allows you to automate the obfuscation of .NET assemblies using dotNET Reactor directly within your GitHub Actions workflows. This action supports running on Windows, Linux, and macOS, making it versatile for cross-platform .NET development environments.

## Features
- Cross-Platform Support: Run obfuscation on Windows, Linux, and macOS.
- Flexible Inputs: Specify custom paths to project files, input assemblies, and output locations.
- Easy Integration: Seamlessly integrates with existing .NET projects and GitHub Actions workflows.
## Current Version
The action uses dotNET Reactor version 6.9.8.0. Ensure that your project is compatible with this version of dotNET Reactor.

## Inputs
This action requires the following inputs:

- project_file: The path to the dotNET Reactor project file. This file contains the configuration for the obfuscation process.
- input_path: The path to the .NET assembly (.dll or .exe) that you want to obfuscate.
- output_path: The destination path where the obfuscated assembly will be saved.

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
```

## Support and Contributions
- Getting Support: If you encounter any issues while using this action, please open an issue in the GitHub repository.
- Contributions: Contributions are welcome! If you'd like to improve the ReactorObfuscation action, please make a pull request.
## License
- This project is licensed under the MIT Licence - see the LICENCE file in the repository for details.