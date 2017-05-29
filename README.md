# hackintosh

### Hardware
- [Intel(R) Core(TM) i7-4790K CPU (Devil's Canyon)](http://ark.intel.com/products/80807/Intel-Core-i7-4790K-Processor-8M-Cache-up-to-4_40-GHz)
- [Samsung SSD 840 EVO 250GB](http://www.samsung.com/global/business/semiconductor/minisite/SSD/global/html/ssd840evo/overview.html)
- [NVIDIA GeForce GTX 760 2048 MB (Kepler?)](http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-760)
- [Gigabyte Z97X-UD5H-BK](http://www.gigabyte.com/products/product-page.aspx?pid=5378#ov)
  - [ALC1150](http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=28&Level=5&Conn=4&ProdID=328)
  - Marvell 88SE9172 Controller GSATA3 6~7
  - Qualcomm® Atheros Killer E2201 LAN
  - Intel® GbE LAN (Intel 82580 ?, AppleIGB or AppleIntelE1000e ?)

### Required Drivers
https://www.tonymacx86.com/resources/categories/kexts.11/
- [AppleALC.kext](https://github.com/vit9696/AppleALC) with [Lilu.kext](https://github.com/vit9696/Lilu)
- HFSPlus.efi (alternative to VBoxHfs-64.efi): https://github.com/JrCs/CloverGrowerPro/blob/master/Files/HFSPlus/X64/HFSPlus.efi
- FakeSMC.kext (from HWSensors)
- GenericUSBXHCI

### Which motherboard am I using?
```
ioreg -arw0 -d1 -c FakeSMCKeyStore | xpath "concat(//key[text() = 'manufacturer']/following-sibling::string[1], ' ', //key[text() = 'product-name']/following-sibling::string[1])" 2>/dev/null
```

### Which CPU am I using?
```
sysctl -n machdep.cpu.brand_string
```

### How do I see which kexts are currently loaded?
```
kextstat
```

### Which Mac Version to use?
Should probably use `iMac15,1` with Devil's Canyon. See [How To Setup The Config.plist](https://www.reddit.com/r/hackintosh/comments/68p1e2/ramblings_of_a_hackintosher_a_sorta_brief_vanilla/).

### Setup

1. Manully format USB partition at HFS. If you don't do this, the next step will create a read only partition. See: [Building the USB Installer](https://www.reddit.com/r/hackintosh/comments/68p1e2/ramblings_of_a_hackintosher_a_sorta_brief_vanilla/)

Replace `disk#` with the disk number from `diskutil list`. For example, `disk2`.

```
diskutil partitionDisk /dev/disk# GPT JHFS+ "USB" 100%
```

2. Use `createinstallmedia`.
```
sudo /Applications/Install\ macOS\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/USB --applicationpath /Applications/Install\ macOS\ Sierra.app
```

3. Install clover on to the USB. See configuration options from [Installing Clover](https://www.reddit.com/r/hackintosh/comments/68p1e2/ramblings_of_a_hackintosher_a_sorta_brief_vanilla/).

4. Replace VBoxHfs-64.efi with HFSPlus.efi on USB.
```
rm EFI/CLOVER/drivers64UEFI/VBoxHfs-64.efi
wget "https://github.com/JrCs/CloverGrowerPro/raw/master/Files/HFSPlus/X64/HFSPlus.efi" -P EFI/CLOVER/drivers64UEFI
```

5. Download FakeSMC.kext from hwsensors.
```
cd ~/Downloads
wget http://www.hwsensors.com/content/01-releases/45-release-1426/HWSensors.6.25.1426.Binaries.dmg
hdiutil attach ~/Downloads/HWSensors.6.25.1426.Binaries.dmg
mv "/Volumes/HWSensors Binaries v6.25.1426/FakeSMC.kext/" 
```

6. Download a bunch of other texts... They are all stored in the kexts folder in this repo.

7. Create / modify config.plist.

...

1. https://github.com/Piker-Alpha/ssdtPRGen.sh


### Benchmarks Tools
https://www.tonymacx86.com/threads/os-x-configuration-tuning-utility-tools.138280/

- Geekbench
- Unigine Heaven
- LuxMark v2
- Blackmagic Speed Test
- Cinebench
- HWMonitor

### Software
- [clover](./software/clover)
- [efi-mounter](./software/efi-mounter)
- [imessage-debug](./software/imessage-debug)

### People
- https://github.com/toleda
	- https://github.com/toleda/audio_CloverALC
- https://github.com/Mieze
	- https://github.com/Mieze/AtherosE2200Ethernet
- https://github.com/kozlek
	- https://github.com/kozlek/HWSensors
	- http://www.hwsensors.com/releases
- https://github.com/theracermaster
	- https://github.com/theracermaster/MacGen
- https://github.com/RehabMan
- https://sourceforge.net/u/slice2009/profile/
- https://sourceforge.net/u/apianti/profile/
- https://www.tonymacx86.com/members/macman.209/
- https://www.tonymacx86.com/members/tonymacx86.3/

### Guides
- (May 2, 2017) Close to Vanilla Install
	- https://www.reddit.com/r/hackintosh/comments/68p1e2/ramblings_of_a_hackintosher_a_sorta_brief_vanilla/
- Clover
	- https://www.tonymacx86.com/threads/how-to-install-os-x-yosemite-using-clover.144426/
- iMessage
	- https://www.reddit.com/r/hackintosh/comments/525dsb/getting_imessage_working_on_el_capitan_and_sierra/
	- http://www.fitzweekly.com/2016/02/hackintosh-imessage-tutorial.html?m=1
	- https://www.tonymacx86.com/threads/how-to-fix-imessage.110471/
	- https://www.tonymacx86.com/threads/an-idiots-guide-to-imessage.196827/

### Tools
- EveryMac Lookup
	- http://www.everymac.com/ultimate-mac-lookup/

### Similar Builds
	- https://github.com/reynardfox/z97x-ud5h
	- https://www.tonymacx86.com/threads/success-build-macos-sierra-on-gigabyte-z97x-ud5h-i7-4770k-16gb-ram-gtx-760.215548/
