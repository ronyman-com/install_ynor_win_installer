Ynor Windows Installer
Professional File Processing and Automation Tool for Windows

https://img.shields.io/badge/Platform-Windows-blue
https://img.shields.io/badge/Version-1.0.0-green
https://img.shields.io/badge/Installer-NSIS-orange
https://img.shields.io/badge/License-Proprietary-lightgrey

Ynor is a professional-grade command-line file processing and automation tool designed specifically for Windows systems with enterprise-level branding capabilities.

📥 Download & Installation
Latest Version
Download the latest installer: ynor_installer.exe

All Versions
Browse all available releases: Releases Page

Quick Installation (Windows)
bash
# Download and install with PowerShell
Invoke-WebRequest -Uri "https://github.com/ronyman-com/install_ynor_win_installer/releases/latest/download/ynor_installer.exe" -OutFile "ynor_installer.exe"
.\ynor_installer.exe
Silent Installation (IT Deployment)
bash
# Silent installation for enterprise deployment
ynor_installer.exe /S

# Silent installation with custom directory
ynor_installer.exe /S /D=C:\Program Files\Ynor
✨ Features
🚀 Core Capabilities
Multi-format File Processing: Supports TXT, JSON, CSV, XML, YAML, and more

Batch Processing: Process multiple files simultaneously

Encoding Detection: Automatic character encoding detection

Validation: Built-in file validation and error checking

🏢 Enterprise Features
Custom Branding: Complete control over installer appearance and branding

Silent Deployment: Support for IT mass deployment (SCCM, Intune, GPO)

MSI Compatibility: Generates standard Windows installer packages

Administrator Privileges: Proper UAC handling and elevation

Control Panel Integration: Appears in Windows Programs and Features

🔧 Technical Excellence
Professional NSIS Installer: Industry-standard installation framework

Global Command Access: ynor command available from any Command Prompt

Desktop & Start Menu Shortcuts: Professional application shortcuts

Automatic PATH Management: No manual configuration required

Clean Uninstallation: Complete removal including registry entries

📊 File Format Support
Format	Features	Status
TXT	Encoding detection, line processing	✅ Full Support
JSON	Validation, pretty printing, schema checking	✅ Full Support
CSV	Delimiter detection, header processing	✅ Full Support
XML	Validation, XPath queries, transformation	✅ Full Support
YAML	Validation, structured processing	✅ Full Support
Markdown	Link validation, formatting	🟡 Basic Support
🚀 Getting Started
After Installation
Once installed, Ynor is immediately available from any Command Prompt:

bash
# Verify installation
ynor --version

# Show help information
ynor --help

# Process a file
ynor document.txt

# Process multiple files
ynor *.txt

# Process with specific options
ynor data.csv --format json --output results.json
Quick Examples
bash
# 1. Check version
ynor --version

# 2. Get help
ynor --help

# 3. Process a text file
echo "Sample content" > test.txt
ynor test.txt

# 4. Convert CSV to JSON
ynor data.csv --format json

# 5. Validate XML against schema
ynor config.xml --validate --schema=schema.xsd

# 6. Batch process all JSON files
ynor *.json --output processed/
🛠 Advanced Usage
Command Line Options
bash
ynor [options] <file> [file2 ...]

Options:
  --version            Show version information
  --help               Show help message
  --format FORMAT      Output format (txt, json, csv, xml, yaml)
  --output FILE        Output file name
  --validate           Validate file structure
  --pretty             Pretty print output
  --encoding ENC       Specify file encoding
  --verbose            Show detailed processing information
  --silent             Suppress all output except errors
Batch Processing
Create a batch file for automated processing:

```batch
@echo off
REM Process all CSV files in directory
for %%f in (*.csv) do (
    echo Processing %%f...
    ynor "%%f" --format json --output "processed\%%~nf.json"
)
PowerShell Integration
powershell
# Process files using PowerShell
Get-ChildItem -Filter *.json | ForEach-Object {
    ynor $_.FullName --validate
}
```

# Create a processing pipeline
"data.csv" | ynor --format json | Select-String "pattern"
🏢 Enterprise Deployment
Silent Installation
powershell
# Download and install silently
$installer = "ynor_installer.exe"
Invoke-WebRequest -Uri "https://github.com/ronyman-com/install_ynor_win_installer/releases/latest/download/$installer" -OutFile $installer
Start-Process -FilePath $installer -ArgumentList "/S" -Wait
Group Policy Deployment
Download ynor_installer.exe

Create a new GPO for software installation

Add as a startup script or use Software Installation policy

Use silent install parameters: /S /D=C:\Program Files\Ynor

Microsoft Intune / SCCM
xml
```
<!-- Configuration.xml for Intune -->
<Configuration>
    <Program>
        <Command>ynor_installer.exe</Command>
        <Arguments>/S</Arguments>
        <DetectionMethod>Registry</DetectionMethod>
        <DetectionRule>
            <Key>HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Ynor Windows Installer</Key>
            <Value>DisplayVersion</Value>
        </DetectionRule>
    </Program>
</Configuration>
```
🎨 Custom Branding
Branding Configuration
Edit installer/config.json to customize:

json
```
{
  "product_name": "Your Company File Processor",
  "version": "1.0.0",
  "company_name": "Your Company",
  "branding": {
    "logo": "branding/custom/logo.ico",
    "banner": "branding/custom/banner.bmp",
    "license": "branding/custom/license.txt"
  }
}
```
Rebuilding with Custom Branding
bash
# 1. Update branding files
cp your_logo.ico installer/branding/custom/logo.ico
cp your_banner.bmp installer/branding/custom/banner.bmp

# 2. Update configuration
# Edit installer/config.json

# 3. Rebuild installer
python installer/build.py
🔧 Troubleshooting
Common Issues & Solutions
Issue	Solution
'ynor' command not found	Reopen Command Prompt or restart computer
Installation requires admin	Right-click installer → "Run as administrator"
File processing errors	Check file encoding with ynor --encoding auto file.txt
Silent install not working	Ensure you're using correct syntax: ynor_installer.exe /S
Uninstall leaves files	Run fix_installation.bat from Output folder
Diagnostic Commands
bash
# Check if ynor is in PATH
where ynor

# Test installation
ynor --version

# View installation directory
reg query "HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Ynor Windows Installer" /v InstallLocation

# Check installer logs
type "%TEMP%\ynor_install.log"
Reinstallation Guide
If experiencing issues:

Uninstall via Control Panel

Delete C:\Program Files\Ynor Windows Installer (if exists)

Restart computer

Reinstall with latest ynor_installer.exe

📁 File Structure
text

```
ynor-win-installer/
├── installer/                    # Installer build system
│   ├── build.py                 # Main build script
│   ├── config.json              # Configuration
│   ├── branding/                # Branding assets
│   │   ├── default/             # Default branding
│   │   └── custom/              # Custom branding template
│   └── nsis/                    # NSIS installer scripts
├── src/                         # Source code
│   └── ynor/                    # Main application
├── Output/                      # Built installers
│   ├── ynor_installer.exe       # Main installer
│   ├── ynor_portable.exe        # Portable version
│   └── test_installer.bat       # Test script
├── requirements.txt             # Python dependencies
├── setup.py                     # Package configuration
└── README.md                    # This file

```
🔄 Building from Source
Prerequisites
bash
# Install Python 3.8+
python --version

# Install NSIS (Nullsoft Scriptable Install System)
# Download from: https://nsis.sourceforge.io/Download

# Install Python dependencies
pip install -r requirements.txt
Build Process
bash
# Clone repository
git clone https://github.com/ronyman-com/install_ynor_win_installer.git
cd ynor-win-installer

# Build the installer
python installer/build.py

# Output will be in ./Output/
# - ynor_installer.exe (Professional installer)
# - ynor_portable.exe (Portable version)
# - Various test and support scripts
Custom Build Options
python
# Edit installer/config.json for custom builds:
```
{
  "product_name": "Your Product Name",
  "version": "2.0.0",
  "company_name": "Your Company Inc.",
  "install_dir": "C:\\Program Files\\YourProduct",
  "features": {
    "add_to_path": true,
    "desktop_shortcut": true,
    "start_menu": true,
    "file_associations": [".txt", ".json"]
  }
}

```
🤝 Contributing
We welcome contributions! Please see our Contributing Guidelines for details.

Development Setup
bash
# 1. Fork and clone the repository
git clone https://github.com/ronyman-com/install_ynor_win_installer.git

# 2. Create virtual environment
python -m venv venv
venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt
pip install -r requirements-dev.txt

# 4. Make changes and test
python installer/build.py

# 5. Run tests
python -m pytest tests/
📄 License
This software is proprietary and confidential. All rights reserved.

© 2024 Ynor Software by Amatak Holdings Pty Ltd.

📞 Support
Documentation
User Guide

API Reference

Troubleshooting

Community & Support
GitHub Issues: Report bugs or request features

Email: support@ynor.app

Website: https://ynor.app

Professional Support
For enterprise support, custom implementations, or licensing inquiries:

Email: enterprise@ynor.app

Phone: Contact through website

Service Level Agreements: Available for enterprise customers

📊 Performance & Benchmarks
Processing Speed
File Size	Processing Time	Memory Usage
1 MB	< 100ms	< 10 MB
10 MB	< 500ms	< 50 MB
100 MB	< 3s	< 200 MB
1 GB	< 30s	< 500 MB
System Requirements
OS: Windows 10/11, Windows Server 2016+

RAM: 2 GB minimum (4 GB recommended)

Storage: 50 MB free space

Permissions: Administrator for installation

Ready to streamline your file processing? Download the latest installer now and experience professional-grade file automation on Windows.

📥 Download Latest Version

Last Updated: November 2025 | Version: 1.0.0
