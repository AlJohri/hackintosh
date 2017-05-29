# hackintosh

### Hardware
- Intel(R) Core(TM) i7-4790K CPU @ 4.00GHz
- [Samsung SSD 840 EVO 250GB](http://www.samsung.com/global/business/semiconductor/minisite/SSD/global/html/ssd840evo/overview.html)
- [NVIDIA GeForce GTX 760 2048 MB](http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-760)
- [Gigabyte Z97X-UD5H-BK](http://www.gigabyte.com/products/product-page.aspx?pid=5378#ov)
  - [ALC1150](http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=28&Level=5&Conn=4&ProdID=328)
  - Marvell 88SE9172 Controller GSATA3 6~7
  - Qualcomm® Atheros Killer E2201 LAN
  - Intel® GbE LAN (Intel 82580 ?, AppleIGB or AppleIntelE1000e ?)

### Required Drivers
https://www.tonymacx86.com/resources/categories/kexts.11/
- ALC1150: https://github.com/toleda/audio_CloverALC
- HFSPlus.efi (alternative to VBoxHfs-64.efi): https://github.com/JrCs/CloverGrowerPro/blob/master/Files/HFSPlus/X64/HFSPlus.efi
- FakeSMC.kext
- NullCPUPowerManagement.kext

### Which motherboard am I using?
```
ioreg -arw0 -d1 -c FakeSMCKeyStore | xpath "concat(//key[text() = 'manufacturer']/following-sibling::string[1], ' ', //key[text() = 'product-name']/following-sibling::string[1])" 2>/dev/null
```

### Which CPU am I using?
```
sysctl -n machdep.cpu.brand_string
```

### How do I create a vanilla bootable USB for macOS?
Use the [createinstallmedia](https://support.apple.com/en-us/HT201372) tool. Assuming you're on Sierra and your USB is called "Untitled":

```
sudo /Applications/Install\ macOS\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/Untitled --applicationpath /Applications/Install\ macOS\ Sierra.app
```

### How do I see which kexts are currently loaded?
```
kextstat
```

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
- https://github.com/theracermaster
	- https://github.com/theracermaster/MacGen
- https://github.com/RehabMan
- https://sourceforge.net/u/slice2009/profile/
- https://sourceforge.net/u/apianti/profile/
- https://www.tonymacx86.com/members/macman.209/
- https://www.tonymacx86.com/members/tonymacx86.3/

### Guides
- Clover
	- https://www.tonymacx86.com/threads/how-to-install-os-x-yosemite-using-clover.144426/
- iMessage
	- https://www.tonymacx86.com/threads/how-to-fix-imessage.110471/
	- https://www.tonymacx86.com/threads/an-idiots-guide-to-imessage.196827/

### Tools
- EveryMac Lookup
	- http://www.everymac.com/ultimate-mac-lookup/
