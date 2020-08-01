# Windows-Drivers-Backup
Backup and Restore Device Drivers in Windows Using Command Prompt Or Windows PowerShell
How to Backup and Restore Device Drivers in Any Windows OS


If you clean install Windows, you will need to install drivers for each device in the system. Some of these device drivers may no longer be available from the manufacturer, or you misplaced a backup of the driver installation file from the manufacturer.

It would be a good idea to back up your device drivers before doing a clean install to make it easy to restore any of these drivers as needed afterwards.

This tutorial will show you how to back up and restore all 3rd party device drivers on your Windows PC.

# You must be signed in as an administrator to be able to backup and restore drivers.
# Contents

Option One   : To Back Up All Device Drivers in Command Prompt/
Option Two   : To Back Up All Device Drivers in PowerShell/
Option Three : To Restore a Device Driver Backup in Device Manager/
Option Four  : To Restore All Device Drivers in Command Prompt/


# OPTION ONE
To Back Up All Device Drivers in Command Prompt

For more usage details about the dism /export-driver command, see: DISM Driver Servicing (.inf) Command-Line Options - Microsoft Hardware Dev Center

For more usage details about the PnPUtil command, see: PnPUtil Command Syntax - Microsoft Hardware Dev Center


1 Open an elevated command prompt.

2 Type either command below you want to use into the elevated command prompt, and press Enter.

# dism /online /export-driver /destination:"full path of folder"

OR

# pnputil /export-driver * "full path of folder"

Substitute full path of folder in the command above with the actual full path of the already existing folder (ex: "F:\Drivers Backup") you want to export all 3rd party device drivers into. If this folder doesn't currently exist, you will need to create it first before running the command.

# For example: dism /online /export-driver /destination:"F:\Drivers Backup"

3 When exporting has finished, you can close the elevated command prompt if you like.

4 The device drivers will now be exported into the specified folder location (ex: "F:\Drivers Backup") as your backup.


# OPTION TWO
To Back Up All Device Drivers in PowerShell

For more usage details about the Export-WindowsDriver command, see: Export-WindowsDriver - Microsoft Windows IT Pro Center


1 Open an elevated PowerShell.

2 Enter the command below into the elevated PowerShell, and press Enter. (see screenshots below)

# Export-WindowsDriver -Online -Destination "full path of folder"

Substitute full path of folder in the command above with the actual full path of the already existing folder (ex: "F:\Drivers Backup") you want to export all 3rd party device drivers into. If this folder doesn't currently exist, you will need to create it first before running the command.

# For example: Export-WindowsDriver -Online -Destination "F:\Drivers Backup"


3 When exporting has finished, you can close the elevated PowerShell if you like.

4 The device drivers will now be exported into the specified folder location (ex: "F:\Drivers Backup") as your backup.

# OPTION THREE
To Restore a Device Driver Backup in Device Manager

1 Open Device Manager.

2 Right click or press and hold on the device (ex: "Intel(R) RealSense(TM) 3D Camera (Front F200) Depth") you want to restore a driver backup for, and click/tap on Update driver.

3 Click/tap on Manually install a driver.

4 Follow the steps below to select the folder (ex: "F:\Drivers Backup") containing the backup of your device drivers from Option One or Option Two above. (see screenshots below)

  1) Click/tap on the Browse button.

  2) Navigate to and select the folder (ex: "F:\Drivers Backup") containing the backup of device drivers.

  3) Click/tap on OK.

  4) Check the Include subfolders box.

  5) Click/tap on Next.
  
5 Device Manager will now search for and install the device driver if it's newer than what is currently installed.

6 When you have finished restoring driver backups, you can close Device Manager if you like.

# OPTION FOUR
To Restore All Device Drivers in Command Prompt

For more usage details about the PnPUtil command, see: PnPUtil Command Syntax - Microsoft Hardware Dev Center


1 Open an elevated command prompt.

2 Type the command below into the elevated command prompt, and press Enter.

# pnputil /add-driver "full path of folder\*.inf" /subdirs /install /reboot

Substitute full path of folder in the command above with the actual full path of the folder (ex: "E:\Drivers Backup") you exported all 3rd party device drivers into.

# For example: pnputil /add-driver "E:\Drivers Backup\*.inf" /subdirs /install /reboot


The /reboot option in the command will automatically restart the computer if needed to complete the operation of importing the drivers.

Be sure you save and close anything open before running this command.

3 When importing has finished, you can close the elevated command prompt if you like.
