# hackintosh

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

### What does each bootflag mean?
- http://www.fitzweekly.com/2016/04/hackintosh-boot-flags.html
- http://osx86.transformnews.com/osx-boot-flags/

```
darkwake=0 
Disable wake up of certain parts of your Mac from sleep, while leaving other parts in sleep mode. This feature often messes up sleep on Hackintoshes. Enter  darkwake=1 to turn it on, if turning it off doesn’t do the trick). if your verbose boot is freezing  be sure to remove SleepEnabler.kext completely by deleting it from either /Extra/Extensions or /System/Library/Extensions in your hard drive.

debug=0x100 or debug=0x144
Turns on debug mode. If you get a kernel panic use either of these boot flags, and  you’ll see a debug screen full of code instead of a kernel panic message.

dart=0
If you can’t boot with OS X and VT-x/VT-d enabled in BIOS, use this flag (UEFI BIOS).

no-zp
Zone Postponing: (use if hanging)

http://www.insanelymac.com/forum/topic/296726-what-they-are-for-these-flagsarguments/
slide=0 is for boot.efi so it may be used only with Clover.
The flag mean an offset to load kernel and it is only way to boot by American Megatrend UEFI.
dart=0 in Chameleon may be replace by Clover's
		<key>DropTables</key>
		<array>
			<dict>
				<key>Signature</key>
				<string>DMAR</string>
			</dict>
for eliminate problem with vt-d 

```

### Which Mac Version to use?
Should probably use `iMac15,1` with Devil's Canyon. See [How To Setup The Config.plist](https://www.reddit.com/r/hackintosh/comments/68p1e2/ramblings_of_a_hackintosher_a_sorta_brief_vanilla/).

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
