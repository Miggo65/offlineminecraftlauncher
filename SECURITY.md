# Security Policy

## Supported Versions

We release patches for security vulnerabilities for the following versions:

| Version | Supported          |
| ------- | ------------------ |
| Latest  | :white_check_mark: |
| < Latest| :x:                |

## Reporting a Vulnerability

The security of Offline Minecraft Launcher is important to us. If you discover a security vulnerability, please follow these steps:

### How to Report

1. **DO NOT** open a public GitHub issue for security vulnerabilities
2. Send an email to the repository maintainers through GitHub
3. Include the following information:
   - Description of the vulnerability
   - Steps to reproduce the issue
   - Potential impact
   - Suggested fix (if available)

### What to Expect

- **Response Time**: We aim to acknowledge receipt within 48 hours
- **Assessment**: We will assess the vulnerability and determine severity
- **Fix Timeline**: Critical vulnerabilities will be addressed within 7 days
- **Disclosure**: We will coordinate disclosure timing with you

### Security Best Practices for Users

1. **Download from Official Sources Only**
   - Only download releases from official GitHub repositories:
     - Original project: `https://github.com/antunnitraj/OfflineMinecraftLauncher`
     - This fork: `https://github.com/Miggo65/offlineminecraftlauncher`

2. **Keep Software Updated**
   - Always use the latest version
   - Check for updates regularly

3. **System Security**
   - Keep your operating system and antivirus software up to date
   - Run the launcher with standard user privileges (not administrator)

4. **Verify Downloads**
   - Check file hashes when provided
   - Scan downloads with antivirus software

### Known Security Considerations

1. **Offline Mode Authentication**
   - This launcher uses Minecraft's offline mode
   - No Microsoft authentication is performed
   - UUIDs are generated locally using the offline player standard

2. **Third-Party Dependencies**
   - The launcher uses CmlLib.Core for Minecraft management
   - This is a well-established, open-source library
   - Downloads are from official Mojang servers

3. **Data Storage**
   - Only username and version preferences are stored locally
   - No passwords or sensitive credentials are collected or stored

### Security Features

- ✅ No telemetry or data collection
- ✅ No network connections except through CmlLib.Core for game downloads
- ✅ Open source code for full transparency
- ✅ Minimal permissions required
- ✅ No code obfuscation

## Security Audit

A comprehensive security audit is available in [SECURITY_AUDIT.md](SECURITY_AUDIT.md).

## Responsible Disclosure

We believe in responsible disclosure. If you report a vulnerability:
- We will work with you to understand and fix the issue
- We will credit you for the discovery (unless you prefer to remain anonymous)
- We will coordinate the disclosure timeline with you

Thank you for helping keep Offline Minecraft Launcher secure!
