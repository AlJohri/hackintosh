# hackintosh

### Components
- Intel(R) Core(TM) i7-4790K CPU @ 4.00GHz
- [Samsung SSD 840 EVO 250GB](http://www.samsung.com/global/business/semiconductor/minisite/SSD/global/html/ssd840evo/overview.html)
- [NVIDIA GeForce GTX 760 2048 MB](http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-760)
- [Gigabyte Z97X-UD5H-BK](http://www.gigabyte.com/products/product-page.aspx?pid=5378#ov)
  - [ALC1150](http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=28&Level=5&Conn=4&ProdID=328)
  - Marvell 88SE9172 Controller GSATA3 6~7
  - Qualcomm® Atheros Killer E2201 LAN
  - Intel® GbE LAN (Intel 82580 ?, AppleIGB or AppleIntelE1000e ?)

### Which motherboard am I using?
```
ioreg -arw0 -d1 -c FakeSMCKeyStore | xpath "concat(//key[text() = 'manufacturer']/following-sibling::string[1], ' ', //key[text() = 'product-name']/following-sibling::string[1])" 2>/dev/null
```

### Which CPU am I using?
```
sysctl -n machdep.cpu.brand_string
```

### Benchmarks Tools
- Geekbench
- Unigine Heaven
- LuxMark v2
- Blackmagic Speed Test
- Cinebench
- HWMonitor

### Software
- Clover Bootloader
	- Wiki: https://clover-wiki.zetam.org/Home
	- Source: https://sourceforge.net/projects/cloverefiboot/
	- Related Software:
		- EDK2
			- Website: http://www.tianocore.org/edk2/
			- Source: https://github.com/tianocore/edk2
		- DUET
			- Clover is based on this software and its related to / might be part of EDK2. I think its also created by the tianocore team.
			- This software seems to be dead now and superceeded by Clover. It used to support only Linux and Windows where as Clover supports all three.
		- rEFInd
			- Website: http://www.rodsbooks.com/refind/index.html
			- Source: https://sourceforge.net/p/refind/code/ci/master/tree/
- [createinstallmedia](https://support.apple.com/en-us/HT201372)
	```
	sudo /Applications/Install\ macOS\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/Untitled --applicationpath /Applications/Install\ macOS\ Sierra.app
	```
- 
