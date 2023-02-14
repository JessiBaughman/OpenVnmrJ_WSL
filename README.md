<h1 align="center">
    <a href="https://github.com/JessiBaughman/OpenVnmrJ_WSL">
    <img alt="A splash image for installation script." width="640px" height="240px" src="https://user-images.githubusercontent.com/52927689/218879398-e6befea4-01cf-439a-aa2a-3937209f552b.png">
    </a>
</h1>

<div align="center">
  <a href="https://github.com/JessiBaughman/OpenVnmrJ_WSL/issues/new?assignees=&labels=bug&template=01_BUG_REPORT.md&title=bug%3A+">Report a Bug</a>
</div>

[![license](https://img.shields.io/github/license/JessiBaughman/OpenVnmrJ_WSL.svg)](LICENSE) ![GitHub last commit](https://img.shields.io/github/last-commit/JessiBaughman/OpenVnmrJ_WSL)
<details open="open">
<summary>Table of Contents</summary>

- [About](#about)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
    - [Administer Privileges](#administer-privileges)
    - [Windows version](#windows-version)
    - [BIOS](#bios)
    - [Windows Features](#windows-features)
  - [Usage / Running the script](#usage--running-the-script)
- [Running OpenVnmrJ](#running-openvnmrj)
  - [Launching OpenVnmrJ](#launching-openvnmrj)
  - [Printing / Plotting](#printing--plotting)
  - [Closing OpenVnmrJ](#closing-openvnmrj)
- [License](#license)

</details>

## About
<a href="https://github.com/OpenVnmrJ/OpenVnmrJ">OpenVnmrJ</a> is free and open-source software for processing NMR spectroscopy data. It runs on Ubuntu 20.04 and Red Hat 7/8 based Linux ditributions as well as macOS 10.13+. This Powershell script is used to install and configure Windows Subsystem for Linux and OpenVnmrJ on Windows 10+ as an alternative to installing within a virtual machine. WSL provides a native application experience and can result in a smaller installation footprint and faster application startup times.

<p>
  <br />
</p>

## Getting Started

### Prerequisites

#### Administer Privileges
Some parts of the script will require administrator privileges to install, configure, or update. You will be prompted on the secure desktop each time. 

#### Windows version
To find your version of Windows, open the Settings panel (`Windows + I`) and navigate to System->About.

* **Windows 10** : Version 2004 (aka 20H1, Build 19041, released Spring 2020) or later
  
* **Windows 11** : Version 21H2 (Build 22000, released Fall 2021) or later

####  BIOS
You will need to enable virtualization in your system BIOS. Entering the BIOS configuration at boot and the label of the virtualization setting itself varies between motherboard manufacturers. You may be able to find detailed instructions by searching your computer model number or manufacturer's name.

#### Windows Features
<p align="center">
  <img alt="The Windows Features panel" width="415px" height="368px" src="https://user-images.githubusercontent.com/52927689/218584527-d098fb02-ded6-4171-98bf-a67fd5db776a.png">
</p>
Two features need to be installed and activated within Windows. These are the "Virtual Machine Platform" and "Windows Subsystem for Linux" features. You can access this panel by searching, "Turn Windows features on or off" from the Start Menu. You will need to reboot your computer after enabling these features.

<p>
  <br />
</p>

### Usage / Running the script

1. **Unlock the script**
   - Right-click on the .ps1 file and click Properties. Check to see if there is a section at the bottom that reads, "Security: This file came from another computer and might be blocked to help protect this computer." If so, click the Unblock checkbox and click OK.
2. **Start the script**
   - Right-click the .ps1 file and click "Run with Powershell".
      - If the script fails to run, you may need to bypass the Powershell execution policy.
        - One time bypass:  
          - Open Run  (right-click the Start Menu and select Run or `Windows+R`)
          - Type: `powershell -ExecutionPolicy Bypass -File C:\path\to\script.ps1` with the correct path to the script.
        - Permanent bypass for current user:
          - Open Powershell and enter: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`
          - Enter `y` at the prompt.
          - Rerun the script.
<p align="center">
  <img alt="The initial installation dialog panel" width="324px" height="482px" src="https://user-images.githubusercontent.com/52927689/218590309-2bedf3de-5b0a-4447-bf98-4ae476e1b1cb.png">
</p>

3. **Fill out the form and click Install**
    - Install from file supports .zip, .tar, and .tar.gz archive files. Archives should decompress to a directory named dvdimageOVJ.
    - The Ubuntu username can differ from your Windows username. However, if Ubuntu-20.04 is already installed, you should enter the default username for that installation.
    - Password is a minimum of 6 characters. If Ubuntu-20.04 is already installed, this should be the default user's password.
    - This script will install a PDF printer for OpenVnmrJ so that all prints/plots from the program are saved as PDF files to the Windows directory specified. The entered directory must exist. The Browse button will allow you to create folders as needed.
    - Checkbox selections dictate which, if any, shortcuts to run OpenVnmrJ are created. At least one location is recommended.
4. **Windows 10 only: Install VcXsrv**
    - The first step will install the <a href="https://sourceforge.net/projects/vcxsrv/">VcXsrv display server</a> if not already present on your system. 
    - This will require elevated privileges first for the install, which will prompt immediately following installer download
    - After installation, you will be notified of an additional elevated prompt request to create a firewall rule for VcXsrv
5. Main installation
    - The script will proceed unattended until the OpenVnmrJ graphical installer runs, as pictured below.
<p align="center">
  <img alt="The initial OpenVnmrJ installation dialog panel" width="406px" height="383px" src="https://user-images.githubusercontent.com/52927689/218595655-22c3e756-c0b8-4a83-b472-3acc2ec68925.png">
  <img alt="The OpenVnmrJ installation dialog panel after clicking the DDR2 tab" width="406px" height="383px" src="https://user-images.githubusercontent.com/52927689/218596465-86bf968c-90ec-474b-9133-fa0ec991c82b.png">
</p>

6. **Install OpenVnmrJ**
    - Select one of the tabs at the top. For datastations, the selection doesn't matter.
    - Select any additional options if desired.
    -  Click Install. 
    - Note: The dialog may appear slightly off screen. Clicking the window's edge, or resizing the window, will snap it back within the visible desktop space.
    - A second popup will appear with the installation status followed by the OpenVnmrJ Admin panel.
<p align="center">
  <img alt="The OpenVnmrJ Admin panel" width="586px" height="395px" src="https://user-images.githubusercontent.com/52927689/218596656-a21a3d4c-62bb-4836-a860-eb539e791916.png">
</p>

7. **Close the OpenVnmrJ Admin window**
    - You do not need to follow the instructions. Just close the window and everything will be setup automatically later in the script.
<p align="center">
  <img alt="The completed OpenVnmrJ installation status panel" width="491px" height="425px" src="https://user-images.githubusercontent.com/52927689/218597143-e394f498-05ea-430d-84e6-c901151451ad.png">
</p>

8. **Click Done**
9. **Answer the 5 prompts within the Powershell window**
     - There are five options to select after installing OpenVnmrJ: walkup and service accounts, NMRPipe, manuals, fidlib (sample data), and spectrometer configuration. Enter `n` for the first (accounts) and last (spectrometer) prompt. Enter `y` for any of the middle 3 prompts that you wish installed.
     - The rest of the installation is breif and requires no further interaction.
10. **Press Enter to close the Powershell window**
     - An installation log is not automatically saved. If you wish to save a log, copy the Powershell contents before pressing Enter.

<p>
  <br />
</p>

## Running OpenVnmrJ
![Running_small](https://user-images.githubusercontent.com/52927689/218871609-11f6ac0e-ff1c-4c80-aa66-1d46d0e87ce6.png)
### Launching OpenVnmrJ
* The easiest way to launch OpenVnmrJ is to used the created shortcuts. To launch manually:
  * Windows 10: Launch VcXsrv using the "VcXsrv with Xauthority" shortcut in the Start Menu or Run: 
    * `%ProgramFiles%\VcXsrv\vcxsrv.exe -multiwindow -clipboard -wgl -auth "%UserProfile%\.Xauthority"`
  * Open WSL (Ubuntu-20.04) and type `vnmrj`

### Printing / Plotting
* Print to file commmands will work as expected. File paths are within Ubuntu, so to save to Windows, navigate to `/mnt/c` to access the `C:` drive. 
* Output created using the `plot` command will be sent to the PDF printer and saved to the directory selected during install.
<p align="center">
  <img alt="Printer selection within the Plot panel of OpenVnmrJ" width="373px" height="248px" src="https://user-images.githubusercontent.com/52927689/218859889-5975e8e9-df79-45da-8329-e5b5aa3340c4.png">
</p>

* You can toggle between color and grayscale plots by selecting the corresponding version of the PDF printer either from the File->Printers... window or the "Send to" drop-down menu within the Processing->Plot panel.

### Closing OpenVnmrJ
* OpenVnmrJ can be exited in the standard methods
  * File->Exit VnmrJ, close the window, or type `exit` on the command line
* **Windows 10:** Once closed, you will need to manually exit VcXsrv from the taskbar if desired.

## Support

- [Report a bug](https://github.com/JessiBaughman/OpenVnmrJ_WSL/issues/new?assignees=&labels=bug&template=01_BUG_REPORT.md&title=bug%3A+) with the script

- For help with OpenVnmrJ
    - Visit the [OpenVnmrJ GitHub page](https://github.com/OpenVnmrJ/OpenVnmrJ)
    - Join the [IVAN SpinSights](https://ivanmr.com) NMR support group

## License

This project is licensed under the **MIT license**. Feel free to edit and distribute this template as you like.

See [LICENSE](LICENSE) for more information.
