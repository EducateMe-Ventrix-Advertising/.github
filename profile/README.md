# Ventrix Advertising
### Development Environment Setup

> [!NOTE]
> This document assumes the developer is on a Windows desktop machine, version 10 or newer, and is not applicable to Mac or Linux users.

### Contents
1. [Enable Virtualization in BIOS](#enable-virtualization-in-bios)
2. [Install Windows Subsystem for Linux (WSL)](#install-windows-subsystem-for-linux-wsl)
3. [Git Installation](#git-installation)
4. [Creating SSH Key](#creating-ssh-key)
5. [Purchasing PhpStorm](#purchasing-phpstorm)
6. [Installing PhpStorm](#installing-phpstorm)
7. [Activating PhpStorm](#activating-phpstorm)
8. [Create PhpStorm Project](#create-phpstorm-project)
9. [Pulling PhpStorm Settings from VCS](#pulling-phpstorm-settings-from-vcs)
11. [Installing Docker](#installing-docker)
12. [Clone Docker Repository](#clone-docker-repository)
13. [Install Docker Development Environment](#install-docker-development-environment)
14. [Export Production Databases](#export-production-databases)
15. [Import Databases into Docker](#import-databases-into-docker)
16. [Access PHPMyAdmin from localhost](#access-phpmyadmin-from-localhost)
17. [Configuring PhpStorm Scopes](#configuring-phpstorm-scopes)
18. [Using PhpStorm Scopes](#using-phpstorm-scopes)
19. [Making File Changes in PhpStorm](#making-file-changes-in-phpstorm)
20. [Committing and Pushing Files](#committing-and-pushing-files)
21. [Correctly Interacting with Git](#correctly-interacting-with-git)


> [!IMPORTANT]
> DOCS ARE COMPLETE BUT MISSING PRETTY PHOTOS

## Enable Virtualization in BIOS
Virtualization in BIOS needs to be enabled for our development environment to function. This is a key step as you will not be able to run local version of our websites without it. There are too many motherboards and BIOS configurations for us to cover in this documentation, so we can only provide you with one step:

1. Refer to your motherboard’s documentation to enable virtualization.


## Install Windows Subsystem for Linux (WSL)
1. Open the Windows Store app from the Windows Start menu.
2. Search for “Ubuntu WSL” by Canonical Group Limited:
https://www.microsoft.com/store/productId/9PN20MSR04DW?ocid=pdpshare
3. Click “Install” and follow prompts.
4. Restart computer.
5. Ensure that WSL is running by opening up command prompt and entering command: `wsl -l -v`


## GIT Installation
1. Navigate to https://gitforwindows.org/
2. Click “Download”
3. Run Installer and follow prompts.
5. Upon completion of installation, open Command Line or PowerShell.
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


## Purchasing PhpStorm
1. PhpStorm may be purchased from the JetBrains website. It is required to use the paid version of PhpStorm, as the free version lacks essential features which are critical to our pipeline.
**Product overview**: https://www.jetbrains.com/phpstorm/
**Pricing page**: https://www.jetbrains.com/phpstorm/buy/#personal
2. On the Pricing page, select “For Individual Use”, then select either “Yearly billing” or “Monthly billing”. It is recommended that you select “Yearly billing,” as this is the most cost-effective choice.
3. On the eStore Identification page, enter the email address to attach licenses. This will also be the email address used to authenticate your license within the application. Use an email address you have access to and access often.


## Installing PhpStorm
1. Download the installer from your Licenses page or using this link:
https://www.jetbrains.com/phpstorm/download/#section=windows
2. Run the installer and follow wizard steps.
3. Create file associations as needed. It is recommended that you set associations for `.php`, `.js`, `.css`, and `.html` files, as this is your primary IDE at Ventrix.
4. Complete installation
5. Open PhpStorm and navigate to File -> Settings.
6. Select “Appearance & Behavior”, then select “New UI,” and uncheck “Enable new UI” if enabled.


## Create PhpStorm Project
1. Open PhpStorm
2. Go to File -> New Project
3. Select PHP Empty Project
4. Set Location to C:\repositories
> [!IMPORTANT]
> It is important to set the file location to C:\repositories, as our development environment requires that location to be set. Ensure that “repositories” is lowercase.
6. Click “Create”


## Configure PhpStorm VCS
1. Open PhpStorm settings.
2. Select Version Control.
3. Select “GitHub”.
4. Click the “+” icon and select “Login via Github”.
5. Follow prompts in web browser to log into GitHub and authorize JetBrains.
6. You may close browser/tab when finished.
7. Click “OK”.


## Pulling PhpStorm Settings from VCS
1. Open File -> Manage IDE Settings -> Settings Sync…
2. Click “Enable Settings Sync…”
3. Check all settings.
4. Click “OK”.
6. You should see UI refresh. If not, restart PhpStorm. If you do not notice any changes, contact a team member for assistance.


## Installing Docker
1. Download Docker for Windows from https://www.docker.com/products/docker-desktop/
2. Run installer and follow prompts.
3. After installation completes, open Command Prompt (CMD) or PowerShell to verify that Docker and WSL are running:  
`docker ps`  
`wsl -l -v`


## Clone Docker Repository
> [!IMPORTANT]
> This step requires that you have [configured your PhpStorm VCS](#configure-phpstorm-vcs).

1. Using a web browser, navigate to repository https://github.com/EducateMe-Ventrix-Advertising/Docker
2. Copy SSH address.
3. Open PhpStorm.
4. Ensure that the PhpStorm project is set to `C:\repositories`.
5. Open a Terminal window in PhpStorm.
6. Ensure that the current directory is set to `C:\repositories`.  
Command to set: `cd C:\repositories`.
7. Enter command: `git clone replaceMeWithSSHAddress`
8. Run command.
9. Verify that the Docker folder exists in the Project panel.


## Install Docker Development Environment
1. Open Docker.
2. In Windows Explorer, navigate to `C:\repositories\Docker\scripts`
3. Run `installLocalhost.bat` – This script will also clone repositories.
4. After running, a command prompt window will open and prompt for permissions for local root CA.  
Follow prompt to grant permissions.
5. When prompted to choose a location for `secrets.sh`, place file at: `C:\repositories\docker\secrets.sh`
6. Press any key to continue.
7. When prompted for the database dump, press any key to continue. Databases will be imported later.
8. Wait for installation to finish. The last step, `composer install`, will take a long time to run.
9. After installation is finished, navigate to `C:\repositories` and rename non-Docker repositories to lowercase.  
Example: `C:\repositories\CEI` should be `C:\repositories\cei`
10. Run `updateLocalhost.bat`.


## Export Production Databases
> [!CAUTION]
> **It is EXTREMELY important that you take extra precautions when interacting with and downloading databases from production. ALWAYS create a backup whenever you are performing ANY operation within the database.   
NEVER drop databases or tables for any reason and be cognizant about which tables you export, as some of them are extremely large.**

1. If you do not have permissions to access PHPMyAdmin, contact a team member for assistance. Otherwise continue.
2. Log in to PHPMyAdmin on production. This assumes you already have the link.
3. Select the database you wish to export.
5. Click “Export”
5. Under Export Method, select the “Custom” option.
6. Find the Request and Error tables in the Tables list and uncheck the right-most checkbox. We will export these tables with Structure only. Do this for all databases.
7. Scroll down to Object creation options and toggle:  
`Add DROP TABLE / VIEW / PROCEDURE / FUNCTION / EVENT / TRIGGER statement`
8. Click “Export”.
9. If saving a file, save file to `C:\repositories\Docker\databases`


## Import Databases into Docker
> [!WARNING]
> Only utilize these instructions if you need to fully install or reinstall databases into Docker. This script will remove or overwrite existing databases.

1. Ensure that SQL files exist in `C:\repositories\Docker\databases` and their file names match their respective repositories. See [Export Production Databases](#export-production-databases) for information on how to export databases.
2. Run importDatabases.bat from `C:\repositories\Docker\scripts`.
3. Wait for batch script to finish.


## Access PHPMyAdmin from localhost
1. Ensure that Docker is running and that `dev_container` is running.
2. Ensure that the database volume exists.
3. Navigate to https://localhost/phpmyadmin.
4. Log in with your production credentials.
5. Use PHPMyAdmin as you would on production.
> [!NOTE]
> Changes on local host will NOT reflect on production, even after pushing code changes to the server from PhpStorm.


## Configuring PhpStorm Scopes
Scopes are a valuable tool which allows you to search more efficiently within our repositories. They are typically the preferred option when searching within the entire project.

1. Contact a team member to get the most up to date scopes.
2. Open PhpStorm settings.
3. Navigate to Appearance & Behavior -> Scopes.
4. In the left panel, select the “**+**” icon to create a new scope.
5. Select “Local”.
6. Name the scope.
7. Select the scope from the scopes list.
8. Copy and paste the desired scope value into the Pattern field.
9. Click “OK.”


## Using PhpStorm Scopes
1. Open a Project search dialog box by entering shortcut `Ctrl + Shift + F `.
2. Select “Scope” from the search options.
3. Select desired scope from the scopes drop-down menu.
4. Type desired search into search input.
> [!NOTE]
> Please note that PhpStorm may not default the search to using Scopes. You may need to reselect that option when opening PhpStorm.


## Making File Changes in PhpStorm
> [!IMPORTANT]
> All code should be committed to a branch and code reviewed before being merged into Master, except in the case of emergencies.

1. Open PhpStorm.
2. Pull changes. Always pull changes before making edits to files.
3. Ensure that the correct branch is selected.
     - Select the Git Branch popup on the far bottom right of PhpStorm.
     - Select the desired repository.
     - Check out a new branch or select an existing branch from the remote dropdown menu.
4. Expand the desired repository from the Project panel.
5. Locate and double click the file you wish to edit.
6. Ensure that line endings are set to LF.
> [!TIP]
> You may locate the line ending settings on the bottom right of the PhpStorm window.
8. Make desired changes to file.
9. Ensure that file formatting is run by using Ctrl+S.
     - If the file is not formatted after using Ctrl+S, try `Ctrl + Alt + L`.
     - If the file is still not formatted, try using `Ctrl + Alt + Shift + L`.
     - If the file is still not formatted, proceed with caution as your PhpStorm settings may be functioning as intended. **Do not commit files which have been drastically altered and contact a team member for assistance**.


## Committing and Pushing Files
1. Locate the Git staging panel in PhpStorm.
2. Select the files you wish to commit and enter a commit message.
3. Double click the selected files to review changes.
     - Confirm that the existing changes are ones you intended to make and there are no issues like syntax errors, typos, etc.
     - Remove unnecessary changes if any exist.
     - Close comparison popup when finished.
4. Click either “Commit” or “Commit and Push…”.
     - “Commit” will save changes to the local repository.
     - “Commit and Push…” saves changes to the local and remote repositories.
5. If “Commit and Push…” selected, select the files you wish to push to server in the Push dialog popup.
6. Click “Push”.
7. If “Commit” selected, when you need to push changes to server, select the Push icon in the Git toolbar and follow same instructions for interacting with the Push dialog.


## Correctly Interacting with Git
> [!IMPORTANT]
> We all develop in the same environment. It is critical that we all operate in a predictable manner.

- Take extra care when committing files to the server. Make sure that the changes you are committing are changes you intended to make.  
- Do not commit files with broken formatting.  
- Do NOT commit files to master, unless it is an emergency.  
- If working in someone else’s branch, make sure they are informed of what changes you intend to make.  
- Do not allow your repo hashes to be out of date or to unexpectedly diverge. This *will* cause hell in the long run.  
- When in doubt, ask for help. Falling a couple hours behind to get assistance is always a more preferable option than the consequences of committing poor code to production.  
- Do not make unauthorized settings changes to PhpStorm. Inform your team members of your intent to suggest or implement changes so we may all pull from the settings repo ASAP.  


<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->
