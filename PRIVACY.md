# Privacy Policy

**Last Updated:** January 2026

## Overview

Lenses.io for VS Code ("the Extension") is committed to protecting your privacy. This Privacy Policy explains how we collect, use, and safeguard information when you use the Extension.

## Information We Collect

### Telemetry Data

When telemetry is enabled, the Extension collects anonymous usage data to help us improve the product. This includes:

- **Feature Usage**: Which commands and features are used
- **Performance Metrics**: Extension activation time, operation duration
- **Error Information**: Stack traces and error messages (with personally identifiable information removed)
- **Environment Information**: VS Code version, extension version, operating system type
- **Connection Events**: Authentication attempts, connection status (without credentials or API URLs)

### What We DO NOT Collect

- **Credentials**: Usernames, passwords, API tokens
- **Data Content**: Topic data, SQL queries, message content
- **Personal Information**: Names, email addresses, IP addresses
- **File Paths**: Your workspace or file system paths are sanitized before transmission

## How We Use Information

We use collected information to:

- Understand feature adoption and usage patterns
- Identify and diagnose technical issues
- Improve extension performance and reliability
- Plan future features based on user needs

## Data Transmission

Telemetry data is transmitted to:

1. **PostHog** (Organization Analytics) - For product insights
2. **Azure Application Insights** (VS Code Standard) - For error tracking

All data transmission uses encrypted HTTPS connections.

## Your Choices

### Opt-Out Options

You can disable telemetry collection in two ways:

1. **VS Code Global Setting**: Set `telemetry.telemetryLevel` to `"off"` in VS Code settings
2. **Extension-Specific Setting**: Set `lenses.telemetry.enabled` to `false` in settings

The Extension respects your choice immediately without requiring a restart.

### Default Behavior

- Telemetry is **enabled by default** but respects VS Code's global telemetry setting
- If VS Code telemetry is disabled, Extension telemetry is also disabled
- You can opt out at any time

## Data Retention

- Telemetry data is retained for a maximum of 90 days
- Error logs are retained for up to 1 year for debugging purposes
- All data is aggregated and anonymized for analysis

## Third-Party Services

The Extension connects to your Lenses.io API instance. All communication with your Lenses.io instance is:

- Encrypted via HTTPS
- Direct between the Extension and your API (no intermediary services)
- Subject to your organization's Lenses.io contract terms

## Children's Privacy

The Extension is not intended for use by children under 13. We do not knowingly collect information from children.

## Changes to This Policy

We may update this Privacy Policy from time to time. Significant changes will be communicated through:

- Extension release notes
- VS Code marketplace listing updates
- GitHub repository notifications

## Contact Us

If you have questions about this Privacy Policy or data practices:

- **Email**: info@lenses.io
- **GitHub Issues**: https://github.com/lensesio/lenses-vscode/issues

## Legal

This Privacy Policy is governed by the laws of the United Kingdom. By using the Extension, you agree to the collection and use of information as described in this policy.

---

© 2017-2026 Lenses.io LTD. All rights reserved.

