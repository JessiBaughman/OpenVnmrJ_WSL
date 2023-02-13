<p align="center">
  <img alt="A splash image for installation script." width="480px" height="182px" src="https://user-images.githubusercontent.com/52927689/218594750-e8f8009f-d60e-4e51-872a-eb274e0709a1.png">
</p>

# OpenVnmrJ_WSL
A Powershell script to install and configure Windows Subsystem for Linux and <a href="https://github.com/OpenVnmrJ/OpenVnmrJ">OpenVnmrJ</a> on Windows 10+

## Prerequisites

### Administer Privileges
Some parts of the script will require administrator privileges to install, configure, or update. You will be prompted on the secure desktop each time. 

### Windows version
To find your version of Windows, open the Settings panel (`Windows + I`) and navigate to System->About.

* **Windows 10** : Version 2004 (aka 20H1, Build 19041, released Spring 2020) or later
  
* **Windows 11** : Version 21H2 (Build 22000, released Fall 2021) or later

###  BIOS
You will need to enable virtualization in your system BIOS. Entering the BIOS configuration at boot and the label of the virtualization setting itself varies between motherboard manufacturers. You may be able to find detailed instructions by searching your computer model number or manufacturer's name.

### Windows Features
<p align="center">
  <img alt="The Windows Features panel" width="415px" height="368px" src="https://user-images.githubusercontent.com/52927689/218584527-d098fb02-ded6-4171-98bf-a67fd5db776a.png">
</p>
Two features need to be installed and activated within Windows. These are the "Virtual Machine Platform" and "Windows Subsystem for Linux" features. You can access this panel by searching, "Turn Windows features on or off" from the Start Menu. You will need to reboot your computer after enabling these features.

## Installation / Running the script

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

