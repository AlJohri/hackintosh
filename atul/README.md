# atul

Latest Benchmark: https://browser.geekbench.com/v4/cpu/3336071

### Hardware
- [Intel(R) Core(TM) i7-4790K CPU (Haswell Refresh, Devil's Canyon)](http://ark.intel.com/products/80807/Intel-Core-i7-4790K-Processor-8M-Cache-up-to-4_40-GHz)
- [Samsung SSD 840 EVO 250GB](http://www.samsung.com/global/business/semiconductor/minisite/SSD/global/html/ssd840evo/overview.html)
- [NVIDIA GeForce GTX 760 2048 MB (Kepler?)](http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-760)
- [Gigabyte Z97X-UD5H-BK](http://www.gigabyte.com/products/product-page.aspx?pid=5378#ov)
  - [ALC1150](http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=28&Level=5&Conn=4&ProdID=328)
  - Marvell 88SE9172 Controller GSATA3 6~7
  - Qualcomm® Atheros Killer E2201 LAN
  - Intel® GbE LAN (Intel 82580 ?, AppleIGB or AppleIntelE1000e ?)

### Required Drivers
See kexts folder for complete list. Put them all in the `Other` folder for Clover.
https://www.tonymacx86.com/resources/categories/kexts.11/
- [AppleALC.kext](https://github.com/vit9696/AppleALC) with [Lilu.kext](https://github.com/vit9696/Lilu)
- HFSPlus.efi (alternative to VBoxHfs-64.efi): https://github.com/JrCs/CloverGrowerPro/blob/master/Files/HFSPlus/X64/HFSPlus.efi
- [VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC) with [Lilu.kext](https://github.com/vit9696/Lilu). This supercedes FakeSMC.kext
- GenericUSBXHCI

### Setup

1. Manully format USB partition at HFS. If you don't do this, the next step will create a read only partition. See: [Building the USB Installer](https://www.reddit.com/r/hackintosh/comments/68p1e2/ramblings_of_a_hackintosher_a_sorta_brief_vanilla/)

Replace `disk#` with the disk number from `diskutil list`. For example, `disk2`.

```
diskutil partitionDisk /dev/disk# GPT JHFS+ "USB" 100%
```

2. Use `createinstallmedia`.
```
sudo /Applications/Install\ macOS\ Mojave.app/Contents/Resources/createinstallmedia --volume /Volumes/USB
```

3. Install clover on to the USB. See configuration options from [Installing Clover](https://hackintosh.gitbook.io/-r-hackintosh-vanilla-desktop-guide/).

6. Copy bunch of other texts... They are all stored in the kexts folder in this repo.

7. Create / modify config.plist.

...

1. https://github.com/Piker-Alpha/ssdtPRGen.sh

### Similar Builds
	- https://github.com/reynardfox/z97x-ud5h
	- https://www.tonymacx86.com/threads/success-build-macos-sierra-on-gigabyte-z97x-ud5h-i7-4770k-16gb-ram-gtx-760.215548/
