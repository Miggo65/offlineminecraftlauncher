# Building Offline Minecraft Launcher from Source

This guide will help you build the Offline Minecraft Launcher from source code. Building from source ensures you can verify the code yourself and have full control over what you're running.

## Prerequisites

### Required Software

1. **Windows Operating System**
   - Windows 7 or later
   - This is a Windows-only application due to Windows Forms dependency

2. **.NET 9.0 SDK**
   - Download from: https://dotnet.microsoft.com/download/dotnet/9.0
   - Make sure to install the SDK, not just the runtime

3. **Visual Studio 2022** (Recommended) or **Visual Studio Build Tools**
   - **Option A: Visual Studio 2022 Community Edition** (Free)
     - Download from: https://visualstudio.microsoft.com/downloads/
     - During installation, select the ".NET desktop development" workload
     - Optional: Select "Visual Studio Installer Projects" extension for building MSI installer
   
   - **Option B: Build Tools for Visual Studio 2022** (Command-line only)
     - Download from: https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2022
     - Select ".NET desktop build tools" workload

### Optional (For Creating MSI Installer)

4. **Microsoft Visual Studio Installer Projects Extension**
   - Only needed if you want to create the MSI installer package
   - Install from Visual Studio: Extensions → Manage Extensions → Search for "Installer Projects"
   - Or download from: https://marketplace.visualstudio.com/items?itemName=VisualStudioClient.MicrosoftVisualStudio2022InstallerProjects

## Building the Application

### Method 1: Using Visual Studio (GUI)

1. **Clone the Repository**
   ```bash
   git clone https://github.com/Miggo65/offlineminecraftlauncher.git
   cd offlineminecraftlauncher
   ```

2. **Open the Solution**
   - Double-click `OfflineMinecraftLauncher.sln` to open in Visual Studio

3. **Restore NuGet Packages**
   - Visual Studio should automatically restore packages
   - If not, right-click the solution → "Restore NuGet Packages"

4. **Build the Application**
   - Select "Release" configuration from the dropdown (not "Debug")
   - Click Build → Build Solution (or press Ctrl+Shift+B)
   - The executable will be created in: `bin/Release/net9.0-windows7.0/`

5. **Run the Application**
   - Navigate to `bin/Release/net9.0-windows7.0/`
   - Run `OfflineMinecraftLauncher.exe`

### Method 2: Using Command Line (dotnet CLI)

1. **Clone the Repository**
   ```bash
   git clone https://github.com/Miggo65/offlineminecraftlauncher.git
   cd offlineminecraftlauncher
   ```

2. **Restore Dependencies**
   ```bash
   dotnet restore
   ```

3. **Build the Application**
   ```bash
   dotnet build -c Release
   ```

4. **Publish the Application** (Recommended for distribution)
   ```bash
   dotnet publish -c Release -r win-x64 --self-contained false
   ```
   
   Or for a self-contained build (includes .NET runtime):
   ```bash
   dotnet publish -c Release -r win-x64 --self-contained true
   ```

5. **Run the Application**
   - Navigate to `bin/Release/net9.0-windows7.0/publish/` (or the publish folder)
   - Run `OfflineMinecraftLauncher.exe`

### Method 3: Creating an MSI Installer (Advanced)

**Note:** This requires Visual Studio 2022 with the Installer Projects extension installed.

1. **Complete Steps 1-4 from Method 1**

2. **Build the Installer Project**
   - In Solution Explorer, right-click `OfflineMinecraftLauncherSetup` project
   - Select "Build"
   - The MSI installer will be created in: `OfflineMinecraftLauncherSetup/Release/OfflineMinecraftLauncherSetup.msi`

3. **Install the Application**
   - Run the generated MSI file
   - Follow the installation wizard

## Verifying Your Build

After building, you can verify the application:

1. **Check the executable exists**
   - Look in `bin/Release/net9.0-windows7.0/` for `OfflineMinecraftLauncher.exe`

2. **Run the application**
   - Launch the executable
   - You should see the Minecraft launcher interface

3. **Review dependencies**
   - The main dependency is CmlLib.Core (version 4.0.5)
   - This is automatically downloaded during build from NuGet

## Troubleshooting

### "Project targets Windows" Error

If you see an error about targeting Windows on a non-Windows OS:
- This application can only be built on Windows due to Windows Forms
- Use a Windows machine or Windows VM to build

### Missing .NET SDK

If `dotnet` command is not recognized:
- Download and install .NET 9.0 SDK from https://dotnet.microsoft.com/download
- Restart your terminal/command prompt after installation

### NuGet Package Restore Fails

If NuGet packages fail to restore:
```bash
dotnet nuget locals all --clear
dotnet restore
```

### Visual Studio Installer Projects Missing

If you can't build the MSI installer:
- Install the "Microsoft Visual Studio Installer Projects" extension
- Extensions → Manage Extensions → Search for "Installer Projects"
- Restart Visual Studio after installation

### Build Configuration Issues

Always use "Release" configuration for production builds:
- "Debug" builds include debugging symbols and are larger
- "Release" builds are optimized and smaller

## Security Considerations

### Why Build from Source?

Building from source provides several security benefits:
- **Transparency**: You can inspect all code before running
- **Verification**: You know exactly what's being compiled
- **Trust**: No need to trust pre-built binaries from unknown sources
- **Customization**: You can modify the code if needed

### Code Verification

Before building, you can:
1. Review the source code in this repository
2. Check the [Security Audit Report](SECURITY_AUDIT.md)
3. Inspect dependencies (mainly CmlLib.Core)

### Safe Build Practices

- Only clone from the official repository: https://github.com/Miggo65/offlineminecraftlauncher
- Verify NuGet packages are downloaded from official NuGet.org
- Build in a clean environment
- Use official Microsoft tools (Visual Studio, .NET SDK)

## Additional Resources

- **CmlLib.Core Documentation**: https://github.com/CmlLib/CmlLib.Core
- **.NET Documentation**: https://docs.microsoft.com/dotnet/
- **Windows Forms Documentation**: https://docs.microsoft.com/dotnet/desktop/winforms/

## Getting Help

If you encounter issues building from source:
1. Check this troubleshooting section
2. Review existing GitHub Issues
3. Open a new issue with:
   - Your Windows version
   - .NET SDK version (`dotnet --version`)
   - Visual Studio version (if applicable)
   - Complete error message

## License

This project is licensed under the GNU General Public License v3.0. See [LICENSE](LICENSE) for details.
