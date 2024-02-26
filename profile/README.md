# Ventrix Advertising
### Development Environment Setup

> [!NOTE]
> This document assumes the developer is on a Windows desktop machine, version 10 or newer, and is not applicable to Mac or Linux users.

### Contents
1. Enable Virtualization in BIOS
2. Install Windows Subsystem for Linux (WSL)
3. Git Installation
4. Creating SSH Key
5. Purchasing PhpStorm
6. Installing PhpStorm
7. Activating PhpStorm
8. Configure PhpStorm Project
9. Connecting PhpStorm to VCS
10. Pulling PhpStorm Settings from VCS 
11. Installing Docker
12. Clone Docker Repository
13. Configure Docker Development Environment
14. Export Production Databases
15. Import Databases into Docker
16. Access PHPMyAdmin from localhost
17. Configuring PhpStorm Scopes
18. Using PhpStorm Scopes
19. Making File Changes in PhpStorm
20. Committing and Pushing Files
21. Requirements for interacting with Git


# THESE DOCS ARE NOT COMPLETE YET I AM MOVING THEM OVER FROM WORD

## Enable Virtualization in BIOS
Virtualization in BIOS needs to be enabled for our development environment to function. This is a key step as you will not be able to run local version of our websites without it. There are too many motherboards and BIOS configurations for us to cover in this documentation, so we can only provide you with one step:

1. Refer to your motherboard’s documentation to enable virtualization.


## Install Windows Subsystem for Linux (WSL)
1. Open the Windows Store app from the Windows Start menu.
2. Search for “Ubuntu WSL” by Canonical Group Limited:
https://www.microsoft.com/store/productId/9PN20MSR04DW?ocid=pdpshare
3. Click “Install” and follow prompts.
4. Ensure that WSL is running by opening up command prompt and entering command: `wsl -l -v`


## GIT Installation
1. Navigate to https://gitforwindows.org/
2. Click “Download”
3. Run Installer and follow prompts.
4. Upon completion of installation, open Command Line or PowerShell.
6. Enter command `git version` to verify that GIT installed correctly.


## Creating SSH Key
1. Open Command Line (cmd) or Git Bash.
2. Input the following line, replacing the email address within quotations with your GitHub email address:
`ssh-keygen -t ed25519 -C “your_email@example.com”`

*Example*: `ssh-keygen -t ed25519 -C “developer@ventrixadvertising.com”`

3. When prompted to “Enter a file in which to save the key”, press Enter to accept the default file location.
4. Enter a passphrase to bind to the SSH key. An empty passphrase is permissible but not recommended.
5. On your Windows machine, navigate to `C:\Users\<<YOU>>\.ssh`
6. Open the contents of `id_rsa.pub` into Notepad or Notepad++
7. Copy the contents of `id_rsa.pub` to your clipboard.
8. Log into your https://github.com/ account.
9. Click user portrait and select “Settings” or navigate to https://github.com/settings/profile.
10. Click “SSH and GPG keys”.
11. Click “New SSH key”.
12. Give the SSH key a title. Any title is fine, as SSH keys are NOT repository specific.
13. Paste the contents of `id_rsa.pub` into the Key field.
14. Click “Add SSH key”.

<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->
