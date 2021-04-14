## macOS Big Sur with OpenCore for Gigabyte B460M D2V

In this repository, I've included all things that I used to build my small Hackintosh.

#### Build Configuration
| Components           | Model                   | Working?      |
| -------------------- | ----------------------- | :-----------: |
| Motherboard          | Gigabyte B460M D2V      | Yes           |
| CPU                  | Intel i4-10400          | Yes           |
| GPU (Integrated)     | Intel® UHD Graphics 630 | Yes           |
| GPU (External)       | -                       | -             |
| RAM                  | 2x8GB DDR-4             | Yes           |
| NVMe (Boot Drive)    | 128GB                   | Yes           |
| SSD                  | -                       | -             |
| HDD                  | -                       | -             |
| Audio                | ALC887                  | Yes           |
| Ethernet             | Realtek® GbE LAN        | Yes           |
| Wireless (WiFi & BT) | BCM94352HMB             | Yes (Both)    |
| USB                  | -                       | Yes, All      |


#### System & Tools
| Name             | Version                | Comments     |
| ---------------- | ---------------------- | ------------ |
| OpenCore         | 0.6.6                  | -            |
| VirtualSMC       | 1.2.0                  | -            |
| Lilu             | 1.5.1                  | -            |
| WhateverGreen    | 1.4.7                  | -            |
| AppleALC         | 1.5.7                  | -            |
| IntelMausi       | 1.0.5                  | Note: 1      |
| RealtekRTL8111   | 2.4.0                  | Note: 1      |
| USBInjectAll     | -                      | -            |
| XHCI-unsupported | -                      | -            |

**Notes**
1. Maybe this is not required, I forget to delete. I will check it later.
2. You need to setup: Network -> Ethernet -> Advanced -> Hardware (Configure: Manually, Speed: 100baseTX, Duplex: full-duplex, MTU: Standard (1500))


#### BIOS Setup
| Name             | Status                 | Comments     |
| ---------------- | ---------------------- | ------------ |
| VT-D             | Disabled               | -            |


## Create Bootable USB Disk
Download the latest version of macOS Big Sur from the App Store. You will need a USB flash drive with at least 16GB. You will need to format the disk using `Disk Utility` with **Format** `Mac OS Extended (Journaled)` and **Scheme** `GUID Partition Map`. After the disk is formatted run the command below to prepare the disk. Please replace `YOUR_FLASH_DRIVE_NAME_HERE` with your newly formatted flash drive name.

````
sudo /Applications/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia --volume /Volumes/YOUR_FLASH_DRIVE_NAME_HERE
````

## Copy EFI
You will need to mount the `EFI` partition to make copy `EFI` files from this repository. To Mount `EFI` partition you may use [Mount EFI](https://github.com/corpnewt/MountEFI) tool.

After mounting the `EFI` drive, Please copy all files from `EFI` to your newly mounted `EFI` drive. Now you can configure the `EFI/OC/config.plist` file with your own/fake `PlatformInfo`. To generate `PlatformInfo` you can use [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS).

Do all BIOS setup things listed above and boot the flash drive.


Now, I can say "Best Of Luck!" only.


Happy Hacking!
