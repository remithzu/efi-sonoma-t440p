# EFI OpenCore - Lenovo ThinkPad T440p
[![License](https://img.shields.io/badge/license-MIT-purple)](/LICENSE)
[![macOS](https://img.shields.io/badge/macOS-Sonoma-brightblue?logo=apple&color=%2300a8ff
)](https://developer.apple.com/documentation/macos-release-notes/macos-14_6-release-notes)
[![OpenCore](https://img.shields.io/badge/OpenCore-1.0.1-brightblue?color=%230097e6
)](https://github.com/acidanthera/OpenCorePkg)

## ⚠️ Disclaimer
This guide provides instructions for setting up OpenCore EFI specifically on a Lenovo ThinkPad T440p. By following this guidance, you acknowledge and accept the following:

* <b>Data Loss Risk:</b> Modifying system firmware and EFI configurations can lead to data loss. It is strongly recommended to back up all important data before proceeding.

* <b>System Instability:</b>  Customizing the EFI settings may result in system instability or compatibility issues with hardware and software. Proceed at your own risk.

* <b>Legal Considerations:</b>  Utilizing OpenCore may violate the terms of service of your operating system or other software. Ensure you are aware of any legal implications before proceeding.

* <b>No Guarantees:</b>  The author of this guide does not guarantee successful setup or optimal performance. Results may vary based on individual configurations and existing hardware conditions.

* <b>Technical Knowledge Required:</b> This process may require a level of technical expertise. If you are unfamiliar with BIOS settings, EFI configurations, or related technologies, consider seeking assistance from knowledgeable individuals.

By continuing with the setup process, you accept these terms and proceed at your own discretion.

## 🧰 Setup Tools Required
Setting Up OpenCore EFI on Lenovo ThinkPad T440p
* [Python](): to run some script.
* [OpenCore](https://github.com/acidanthera/OpenCorePkg): Base EFI.
* [ProperTree](https://github.com/corpnewt/ProperTree): For editing plist files.
* [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS): To generate SMBIOS information.
* [Balena Etcher](https://www.balena.io/etcher): To flash a USB drive.
* Disks/gParted: For formatting and mounting the EFI partition (Linux).
* Partition Wizard: For formatting and mounting the EFI partition (Windows).

## 🗜️ Preparation
1. Install Python to your computer.
2. Downloading image:

    <b>Using recovery image:</b>

    Enter OpenCore directory and Enter Utilities and macrecovery
    ```bash
    cd OpenCorePkg/Utilities/macrecovery/
    ```
    Open recovery_urls.txt to select recovery image you need, and run the script to download.

    ```bash
    ./macrecovery.py -b Mac-C3EC7CD22292981F -m 00000000000F0HM00 download
    ```

    <b>Using vanila image:</b>
    
    download vanila image from [olarila](https://olarila.com) site.
## 🎛️ Setup Instructions
<b>Step 1: Clone the EFI Repository</b>
1. Clone the Repository:

    Open a terminal (Linux/macOS) or Command Prompt (Windows).
Run the following command to clone the EFI files:
    ```bash
    git clone https://github.com/remithzu/efi-sonoma-t440p.git
    ```
    Rename the folder efi-sonoma-t440p to EFI
2. Generate SMBIOS with GenSMBIOS:

    In this step i use SMBIOS `MacBookPro16,1`, Open a terminal or Command Prompt
    ```bash
    cd GenSMBIOS
    ./GenSMBIOS.command
    ```
    Select ` 1 ` to update OpenCore and than ` 2 ` to select config.plist file on the EFI > OC directory and the final select ` 3 ` to generate SMBIOS and than ` Q ` to exit.

3. Edit config.plist if needed.

4. Create USB bootable.

    <b>Balena Etcher</b>

    Run Balena Etcher and select disk image of Hackintosh, than select USB drive and Flash.

    <b>Manual</b>

    Format USB Drive to EFI bootloader using disk or gParted (Linux) or Partition Wizard (Windows).

5. CopyPaste the EFI Folder to the EFI Partition

    Open the mounted EFI partition (e.g., /mnt/EFI on Linux or the assigned drive letter on Windows). Navigate to the EFI folder you renamed earlier. Paste the copied EFI folder into the root of the EFI partition.

## 🏁 Final Steps
After copying the EFI folder, ensure your configuration is set correctly in the config.plist. Boot from the USB drive and follow any additional setup instructions specific to your system.

For complete instruction read the [wiki](https://github.com/remithzu/efi-sonoma-t440p/wiki).
---

## 📜 License

This repo is licensed under the [MIT License](https://github.com/valnoxy/t440p-oc/blob/main/LICENSE).

The following files are licensed under the [MIT License](https://github.com/valnoxy/t440p-oc/blob/main/LICENSE):
- SSDT-ADPT ```(Power Resources for Wake)```
- SSDT-ALS0 ```(Fake ambient light sensor)```
- SSDT-BATX ```(Battery driver)```
- SSDT-DEHCI ```(Disable EHCI controller)```
- SSDT-ECRW ```(ACPI driver for OEM hardware (YogaSMC))```
- SSDT-HPET ```(IRQ Conflicts fix (Needs _CRS to XCRS Rename))```
- SSDT-KBD ```(Brightness patch)```
- SSDT-LED ```(LED and Power Button blink patch)```
- SSDT-MCHC ```(AppleSMBus fix)```
- SSDT-PLUG ```(Plugin type to 1 for CPU0/PR00)```
- SSDT-PNLF ```(PNLF device for WhateverGreen)```
- SSDT-PWRB ```(Power button)```
- SSDT-SMBUS ```(Injects missing DVL0 device)```
- SSDT-THINK ```(ThinkVPC (YogaSMC))```

OpenCore is licensed under the [BSD 3-Clause License](https://github.com/acidanthera/OpenCorePkg/blob/master/LICENSE.txt).

---
```Copyright (c) 2024. By remithzu <remithzu@proton.me>```