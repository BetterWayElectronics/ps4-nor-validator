# Better Way Electronics - PS4 NOR Validator & Syscon Patcher
 
![BwE](https://i.imgur.com/thU4Rxn.png)

## Introduction ##

I am BwE of betterwayelectronics.com.au and I have been creating software to validate the PlayStation's flash since 2008 with the help of psdevwiki.com :)
I also repair consoles locally in Australia and have been doing that since 2008 also. I am only recently slowing that down due to commitments with a PhD I am undertaking.

## FAQ ##

### So what is this program exactly and why should you use it? ###
This program is for those with the BLOD or 'blue light of death' or any other weird issue with their PS4. Using my program can help you determine if its a software or hardware issue.
It might sound a bit basic to say that my program just checks what the problem is, but ultimately without it you could be repairing things for no reason and wondering why it isn't working.
This program is designed and catered to other console repair professionals, this is why it is simple and straightforward. If you cannot desolder/reflash your PS4 then you're doomed.
I am happy to say that my program will check every single byte of the flash, either individually as a value or as an area (such as encrypted/filled). Nothing is skipped.

### What if my problem is indeed software? Your program is spitting out WARNING and DANGER everywhere! ###
Depending on where in the flash there's corruption also depends if it can be fixed. The flash is semi-encrypted with per-console data as well as universal data.
You can for example easily patch a corrupt WiFi/BT module on the PS4, I even have a separate program to do just that. This is because that data is NOT unique to anybody's console.
Other areas such as the CoreOS can be patched for common corruptions, but the patches are generic and technically do NOT match your console as your CoreOS is entirely UNIQUE.
The rest of the console is a bit of a hit and miss. I may be able to help by using existing data from the 1000's of dumps I have, but your specific corruption may be unfixable.

### What is this UART thing I hear about? ###
Well this is the debugging system Sony uses. I added an ability to patch your dump to enable it, both before and after validation.
Have a look at https://repair.wiki/w/PS4_UART_Guide for a guide on how to do this.
Once you start outputting a log, the last thing it ends on is generally the error thats stopping your console from booting (or what's causing it to crash).
Since I don't work for Sony I cannot tell you what every single error code means, but I or others can surely help (check my discord for example).
My program will fix a majority of issues that UART outputs, some issues like IDPS error and SAMU Enter/Leave cannot be fixed at this time.


### What else can your program do? ###
I have bundled in my comparison program as well as my patching, flagging and extraction tools. Some of these are on my Github (https://github.com/BetterWayElectronics/) as individual apps.
I have designed it to read dumps from either the same directory you run the program from or a /dumps/ directory. It also accepts different file formats beyond .bin. 
You can have 1000's of dumps in the one folder, it will simply ask which one you want to validate.
There is also the ability to upload dumps to me after the validation is complete (or before) - this is how I keep updating my program, with your new/interesting dumps :)
I have lots of patches for corruption and for various flags, this will fix and or enable lots of new interesting features on your PS4.


### Syscon? ###
As of 1.9.2 I added Syscon Scanning & Patching. Use in conjunction with my provided CoreOS patching to downgrade and repair LoadBIOS errors. Do not use separately, you will brick.
	Add your 512kb .bin file in the same folder as this program :)
	
What can you do with the Syscon?

	- Downgrade (CoreOS Swap)
	- Repair LoadBios -8 Error
	- Repair sceSblSlLoadSelf -8 Error
	- Repair checkUpdVersion Error 
	- Repair BlStorageHeader Error

More Information/Guide: https://betterwayelectronics.com.au/syscon.html or https://betterwayelectronics.com.au/sce_syscon.html or https://www.youtube.com/watch?v=hcmMSYmwSUQ


### Why is your software no longer free? ###
I would like to say the lack of donations, but ultimately I am very busy and working on this project has become difficult, I started in 2008 and since then it has been free. 
However, I am now spending time I shouldn't be spending developing PS5 software and continued innovations for the PS4.
Finally, the majority of endusers for this program are businesses (and that is the target market) so while they profit off my program, I do not.

If you enjoy my program visit https://betterwayelectronics.com.au/bweps4norvalidator to purchase a key!

Note: My software and future software will still run at least once as a trial. This is suitable for regular consumers who need to fix their personal console. Business use must require payment for an unlimited license.
Each licence allows once PC and is locked to your HWID. You can change your HD and format your PC and the licence will work, but you cannot use it on another PC.
	
### Your program is a VIRUS! ### 
I protect my program with Themida. The problem with this is that heuristically some AV software see it as a threat.
This is because people who make or redistribute old malware also use Themida to help make themselves undetected.
Ultimately, it is up to you to trust the program and me. I encourage you to upload to a malware sandbox or virustotal to see for yourself.
This is why there is a password on the RAR file (that being 'BwE')

### Whats up with the image that pops up when the program starts? ###
Hey, I am allowed some creativity aren't I? I have no GUI so this is all I can do design wise. Older versions of my program had chiptunes, be happy they're gone!

### What are those files you put on Github? ###
I have added a few old and unidentifiable dumps for your perusal. This is for people who have no actual PS4 or personal dumps but still wish to see the functionality of my program. They have had their serial numbers and MAC addresses removed. They were originally taken from psdevwiki and or colleagues. I have also added a more modern example output html file that my program produces, for those wishing to skip the downloading process.

### Your program is crashing!? ###
It is either because of the newer protections I have added since adding licencing, or your antivirus is having an issue with the program. Contact me and provide what AV, OS and whether you had issues with older versions.

## TLDR ##
* TLDR; Will this fix my BLOD? Well yes and no, if there are sections that are corrupt it is possible to patch it with valid data from another PS4 (or from a different section) - but NOT perconsole data (maybe)!
* TLDR; Will this prove my BLOD is software based? Yes, if the dump comes up 100% valid then it is likely a hardware issue - I recommend enabling UART and seeing its output.
* TLDR; Will this fix my corrupt CoreOS? Yeah with a patched Syscon.
* TLDR; Will this fix my loadBios -8 Error? Yeah with a patched Syscon.
* TLDR; OK = OK, Warning = Weird but MIGHT be okay, DANGER = Bad


## Syscon Menu Options: ##
	
	Syscon Menu:

		1. Auto Patch
			Will automatically grab the last 080B and replace it with the first in the current active slot or blank out the latest, depending on your Syscon.
		2. Manual Patch
			If it cannot automatically patch, or if you decide to manually patch you may do the above yourself.
			You must then replace the last active 080B with an earlier one, or with an empty slot/space. Sizing is automatic so if you go over it will auto-trim.

## NOR Menu Options: ##

	1 - Comparison

		Launches the comparison app, used for the bulk diagnosis and comparison of dumps (Put multiple .bin files in the same directory). FFeatures multiple output and filter options.
		
			1. Compare Specific Version Only
			2. Compare Specific SKU Only
			3. Compare Specific Version & SKU Only
			4. Compare All Dumps

			1. Compare Offsets (Hex)
			2. Compare Offsets (ASCII)
			3. Compare Offsets MD5
			4. Compare Offsets Entropy
			5. Double Offset Comparison
			6. Dynamic MD5 Calculation
			7. Compare File MD5
			8. Compare File Entropy & Byte Count

	2 - Patch (/Patches/)

		Designed to load .bin patches from the /patches/ directory. It will interpret and auto locate patch offsets if they've been extracted by my program. If not it will ask for a start address.

	3 - Patch Corrupt CoreOS (SU-30631-3 Error)

		Basically an automated version of what Andrew Paul suggests (https://youtu.be/35DFGCim_WY). It will scan the CoreOS and patch the corrupt sections within about 1 second.
		If you have this error (or SU-37553-3) but my program tells you that there is no corruption, you need to replace the actual NOR IC itself and reflash it.
		Another option is to wipe the flash entirely with FF or 00 and re-read it and THEN reflash your original valid dump. Do not just use the default wipe+flash option in your software.
		
	4 - Patch Corrupt EAP Key (Panic EAP Key Not Available Error)
	
		Compare both EAP keys against eachother, if one is corrupt or blank it will copy it over. If both are blank it will generate a new one for both slots. If patch fails, there is a reverse patch option.
		Repairs BLOD related to EAP Key panic.
		
	5 - Patch & Switch CoreOS + Southbridge Slots (LoadBios & Downgrade)

		Allows for switching of the CoreOS and or Southbridge slots to aid in either downgrading or repairing LoadBios/No Beep errors. Must not be used without first backing up Syscon chip.
		Header patches are provided but you can also insert your own. This is because some patches may not work, you may need to apply multiple until it works.
		
		Apply in sequence until BLOD with checkUpdVersion 0xfffffff AND secure loader version lower than standby version.

			1. Patch Southbridge Flag & CoreOS Header
			2. CoreOS Header Only
			3. Southbridge Header Only

		See Guide/s:
		https://betterwayelectronics.com.au/sce_syscon.html
		https://betterwayelectronics.com.au/syscon.html
		https://www.youtube.com/watch?v=hcmMSYmwSUQ

	6 - Enable/Disable/Toggle 8 System Flags

		These flags will work without the need to jailbreak. 

			1. Enable/Disable UART
			2. Enable/Disable IDU Mode
			3. Toggle Boot Parameter Modes
			4. Toggle Memory Budget Mode
			5. Toggle Slow HDD Mode
			6. Enable/Disable Update Mode (Fixes CE-35888-2/SU-35888-2)
			7. Enable/Disable Registry Recover Mode
			8. Enable/Disable Arcade Mode
			9. Enable/Disable MANU Mode
			10. Enable/Disable Safe Mode Boot
			11. Enable/Disable Memory Test
			12. Enable/Disable RNG/Keystorage Test
			13. Enable/Disable UART + Memory & RNG/Keystorange Test
			14. Swap X and O Buttons

		UART is well vetted, the others are not so use at own risk.
		I recommend the following UART guide: https://repair.wiki/w/PS4_UART_Guide It includes drivers and programming software you may need.

		Memory Test mode tests the memory within UART.

		Update mode will fix CE-35888-2/SU-35888-2 errors.

		MANU Mode will enable Service Mode on older firmwares.

		Info on IDU Mode: https://youtube.com/watch?v=HlpjWLbL67Y

	7 - Extract (BwE Style)

		Extract based on literal files and does so dynamically based on their size.

	8 - Extract (Zecoxao Style)

		Extracting file sections pursuant to Sony's file blocks.

	9 - Upload Only

		If this appears, you have a good connection to my server and you can upload without validating - good if you forgot to do it earlier. Does not appear if offline.

	9/10 - Validate

		Will scan the entire dump from start to finish and produce a readable validation output in HTML format. Remember, you can put multiple dumps in the same directory. Becomes option 7 if offline.


## File Information: ##
	File MD5: 401ECB4F60A5D81B7D07DD7A6D14EAEB 
	Technical Support: bwe_is_1337@betterwayelectronics.com.au

	System Requirements:
	Minimum 4 CPU Threads
	Windows XP, 7, 8 or 10 (64bit) 
	9mb+ Storage Space

	Archive Password:
	BwE

## Stats: ##
	22,762 Lines of Code
	845KB of Code
	2981+ Offsets Read
	3047 Possible Results/Outputs
	
## Version History: ##
	2.0.2 (4/2/23) Vital Update to Southbridge & CoreOS Patching (For FAT Models), New Update Handling Process, Other Mild Fixes
	2.0.1 (31/1/23) Updated Syscon Patcher (Less Manual Patching (Still Beta)), Significant Updates to UNK, CID, Naming Schemes and Flags, Added MANU (Manufacturer Mode (Service Mode (Old FW Only)) Mode, Safe Mode, Memory Test, RNG/Keystorage Test, X and O Button Swap & Multi Patches, Added EAP Reverse Patch (Use If First Fails), Better File Handling & Messages.
	2.0.0 (20/1/23) Added UART Patching To CoreOS/Southbridge Patcher, Added Bulk CoreOS/SB Patching (1-4 or 1-2), Added Per File Entropy Pursuant To Sony's File Structure, Improved Syscon File Handling, Bundled Serial Reader Application (Auto Detects COM Port then Reads & Auto-saves Serial as ASCII (.txt) or Hex (.bin)).
	1.9.9 (8/1/23) Added Syscon Firmware Validation, Better EAP Key Validations, Better UNK Validations, Added EAP Key Repair (Panic EAP Key Not Available Error/Corrupt UNK Section), Fixed v1.xx Version Errors.
	1.9.8 (5/1/23) Update to CoreOS/SB Patching, Added Unlisted Results, Added New Validations, Updated Internal Comparator
	1.9.7 (28/12/22) Serious Bug Fix In Syscon Patching.
	1.9.6 (28/12/22) Significant Changes To Syscon Patching (Still Beta - Expect More Updates) - Some Manual Patching Explicitly Required (Soon To Be Auto).
	1.9.5 (26/12/22) Reworking of CoreOS/Southbridge Patching (Avoids BlStorageHeader Errors), Improved Auto-Patching Syscon (If You Still Have CheckUpdVersion Errors Let Me Know!)
	1.9.4 (24/12/22) Bugfix in Syscon Scanning (<= 0 Length Slot1 Crashing App), Bundled External HWID Generator App (Auto Copies HWID to Clipboard!)
	1.9.3 (22/12/22) Updated Syscon Scanning & Patching (Still Considered Beta)
	1.9.2 (20/12/22) Added Syscon Auto & Manual Patching (Beta), Added Syscon Service Mode Patch Scanning (No Auto-Patching Yet), Massive Changes to Syscon Scanning, Updated Extractor, Added Unlisted/New Validations (FW 10+), UNK Changes, Added New SKU (OMG! 7218C From THAILAND!), Added Mercy For Trial Users (No Files? Try Again!), New Boot Logo & HTML Graphics, Fixed Failure Message
	1.9.1 (24/11/22) Added Syscon Patch Scanning (No Auto-Patching Yet - 1.9.2+) Includes: Syscon Slot Discovery, Syscon Active Slot Discovery, Syscon Patchable Area & Slot Discovery, Syscon Upload. Also: Improved Validations, Improved Code Structure
	1.9.0 (16/11/22) Added Licensing (Trial Executions = 1 (Suitable For Non-Business Use), Improved Licensing Handling, New Min Version 1.9,0, Improved Result Handling, Fixed Crashing & Incompatibility, Added CoreOS Swapping + Southbridge Flag Patching (Added Bespoke, Predetermined Patching), Added Secondary Methodology For CoreOS Swap, Added Improved CoreOS Interpretation/Validation, Added UserIDs, Improved File Handling including the /Dumps/ Sub-directory Traversal, Improved Validation of PerConsole Areas, Updated Comparator (Filter by SKU/Version/Both).
	1.8.8 (5/6/22) Updated Readme, Fixed Offsets MD5 Comparison, Added Highlighting, Added Unlisted Hashes, Added: Update Mode, Show Mode (TestKit), Registry Recover, Software Version (Old/Useless) and Arcade Mode Flags & Patches (Except Show & Software Version).
	1.8.7 (13/4/22) Added Three New v9.50 WiFi/BT FWs, Added Unlisted Results, Added Region Information
	1.8.6 (18/3/22) Bug Fix (Crash After Launch If Online), Added New WiFi/BT FW, Added Unlisted Results, Adjusted Some Validation Results
	1.8.5 (25/1/22) New Validations, Added Unlisted/New Results, New Statistical Values, Fixed Results HTML File Name Bug, Improved CID & UNK Validation (Removed False Warnings), Cosmetic Fix To 'Validation Complete', Added Block For v1.8.0 & Below.
	1.8.3 (26/11/21) Improved File Handling When Patching, Added UART Enabling Question After Validation (Requested Feature), Bug Fix Handling Files NOT In /Dumps/ (Whoops), Bug Fix Handling UART.
	1.8.2 (21/11/21) Improved Validation & Classification of WiFi/BT Modules, Improved Validation of All Encrypted Sections, Added New WiFi/BT FW MD5s, Bug Fix Handling Files In /Dumps/.
	1.8.0 (15/11/21) Added Unlisted Results, Added New Flags & Patches (Boot Parameter (Dev, Assist, Release), Memory Budget and Slow HDD Mode), Added New WiFi/BT FW MD5s, Changed Patch Offset Interpretation For WiFi/BT, Fixed Patching Showing Dump MD5 Instead of Patch MD5, Changed Interpretation of Dump Files (Save Time With Hardcore Corruption/Wrong Files), Cosmetic Fixes, Connection Fixes (Temporary).
	1.7.4 (7/10/21) Fixed Uploading Criteria, Fixed Server Side Uploading Issue (58 Dumps Lost!), Added Unlisted Results
	1.7.3 (22/8/21) Fixed IDU Patching, Added Unlisted/New Results (Thank You Uploaders!)
	1.7.2 (30/7/21) Fixed Mishandling of Bulk Warning/Danger Results (Significantly), Added Unlisted/New Results.
	1.7.1 (25/6/21) Fixed Uploading Questions, Added MB Serial to Outputs, New Spash Screen.
	1.7.0 (23/6/21) Added Questions Regarding Dump When Uploading, Added New CID Validation (Weird Key or Flag), Fixed UART Validation, Added Unlisted Results.
	1.6.9 (26/5/21) Fixed Internal Code Issues, Added Unlisted Results, New Splash Screen (Potentially last update for a short while).
	1.6.8 (16/5/21) Updated Internal Comparison Application, Improved Serial Number Validation (MB Series), Added Unlisted Results.
	1.6.7 (25/4/21) Repaired UNK 1200 Series Validation, Added Unlisted Results.
	1.6.6 (12/4/21) Added Unlisted Results, Improved Validation, Changed Output Styling.
	1.6.5 (31/3/21) Added CoreOS Statistical Analysis, Changed Some Results, Changed Some Output Formatting, Returned to Previous Packer.
	1.6.3 (30/3/21) Added CoreOS Patcher (SU-30631-3 Error Specific), Updated Results, Added Unlisted Results, Fixed Readme, Changed Packer.
	1.6.2 (18/3/21) Repaired CID Validation, Improved Handling of 72xx, Added Unlisted Results, Improved Dump Uploading Process.
	1.6.1 (20/2/21) Repaired CID Validation, Added Unlisted Results (Thanks Uploaders!)
	1.6.0 (4/2/21) Added IDU Mode Patcher, Improved Validations, Added Unlisted Results.
	1.5.9 (29/1/21) Major Improvement to CID and UNK Validations, Added Unlisted Results, Improved UART Patching, Better Handling of 1200/Pro/Slim Validations, Added v1.5 of Comparator (Comparison Tool, Option 1)
	1.5.7 (11/1/21) Fixed Version Check, Improved Statistics, Removed Some Unlisted Results (Improved Validation), Updated Upload Feature, Improved Compiler
	1.5.6 (10/1/21) Improved CID and UNK Validations, Updated Unlisted Validations, IDU Flags Added, Some Code Optimization
	1.5.5 (8/1/21) Updated Pro/Slim Specific Validations, Updated Unlisted Validations, Updated CID Validations, Updated UNK Validations, Added Dump Upload Feature
	1.5.3 (5/12/20) Updated Unlisted Validations, Updated WiFi/BT MD5s & Entropy Validation
	1.5.2 (20/11/20) Updated WiFi/BT MD5s, Added 2nd UART Flag, Updated Unlisted Validations
	1.5.1 (3/11/20) Updated Unlisted Validations, Added UART Enabler, Removed Unused Validation Option, Added Basic Loader
	1.5.0 (30/10/20) Updated Unlisted Validations, Upgraded Existing Validations, Removed Loader (Secret Patcher Coming Soon!)
	1.4.9 (3/5/20) Added 21xx Series Specific Validations, Updated Unlisted Validations
	1.4.7 (23/3/20) Added Dynamic Comparison, Updated Unlisted Validations
	1.4.6 (1/2/20) Just Keeping It Fresh! (May have fixed issues stopping the program running, if not let me know!)
	1.4.4 (16/8/19) Added and Improved Validations (CID & UNK) Including New WiFi/BT FW MD5
	1.4.2 (7/4/19) Added More Validations (Firmware & Console Specific), Improved Various Sections (CID & UNK Mostly)
	1.4.1 (1/3/19) Prettied Up Outputs, Minor Rewording (Sorry!).
	1.4.0 (1/3/19) Added Zecoxao Extraction Methodology (Will Add More Zecoxao SELF Stuff Later), Added FW/BIOS Versioning, Added Additional Entropy Validation & Various Improvements Throughout.
	1.3.8 (21/2/19) Added Additional Validations (To Suit Slim/Pro), Repaired/Improved CID Validation, More MD5s & Table Based Results.
	1.3.5 (30/1/19) Added CoreOS Reference Points (Additional CoreOS Per-Console Validation).
	1.3.3 (24/1/19) Reworked And Improved Both CID And UNK Sections Again, Added More MD5's, Added Application Version Checker, Removed Colored Bars, Added Comparator & Other Improvements Throughout.
	1.3.1 (19/1/19) Added More Validations & MD5's, Repaired Minor Bug.
	1.3.0 (15/1/19) Completely Reworked And Improved The CID Section And Added Additional Validations To The UNK Section & I Also Improved Some Other Validations Throughout.
	1.2.6 (18/12/18) Hopefully Fixed 'Black Screen' Issue, Recompiled In 32bit.
	1.2.5 (17/12/18) Added 2 New Flags (Possibly Initialization Flag?), Changed Validation Results, Improved Output/Info (HTML) & Added MD5's. 
	1.2.0 (8/12/18) Improved All Alt Validations, Repaired Vtrm1, Internal Typo & Added Repetition Checks.
	1.1.1 (29/11/18) Typo Again, Made The SKU Not Come Up As Unlisted & Added Some MD5's.
	1.1.0 (28/11/18) Improved VTRM & CID Validation, Typo Fixes & Better Colours. 
	1.0.0 (27/11/18) First Release!

### Greetz/Credit: ###
	Thailand (Xohke!)
	PS3/PS4 Dev Wiki (+ Its Contributors)
	DARKNESMONK
	Bert NL
	eussNL (<3)
	cfwprpht
	judges
	3absiso
	pearlxcore
	DEFAULTDNB
	Stooged
	GregoryRasputin
	zecoxao
	Cliques Unique
	ProConsoles NL
	Centrino
	Viktor TechStars Romania
	Nikesh
	Orbis/Akiong
	YTAndrewPaul (YouTube)
	Palestine!
	luminouslamp367 for Regex: (\S*)\s?(\$\S*)\s*?(\$FOO)\s?(\S*)
	Hoea
	DigiMod 
	SCE
	You! 
	
Proudly made in Perl with Notepad++ by BwE, alone </3
Thanks to all the people who email me and beg me to update my program <3 

Made In Australia!

## Links ##

### Support/Donate: ###
https://www.buymeacoffee.com/BwE

### Console Repair Discord: ###
- https://discord.com/servers/console-repair-discord-754165317961383997
- https://discord.gg/pXeUHMy

### Videos Featuring My Program: ###
- https://www.youtube.com/watch?v=hcmMSYmwSUQ <--- My video!
- https://www.youtube.com/watch?v=NBktKSx4FzQ
- https://www.youtube.com/watch?v=GXOBX6BDg0I
- https://www.youtube.com/watch?v=p8DyudhA7ME
- https://www.youtube.com/watch?v=1gk7HtYih84
- https://www.youtube.com/watch?v=m3wgiudcTEA
- https://www.youtube.com/watch?v=EISO-t2fnMw
- https://www.youtube.com/watch?v=Yal7cwdIKCg
- https://www.youtube.com/watch?v=m5ZUEyya82g
- https://www.youtube.com/watch?v=gHifHpquN6E
- https://www.youtube.com/watch?v=laxB_D80nJE
- https://www.youtube.com/watch?v=7D4Zte3vzvg 
- https://www.youtube.com/watch?v=35DFGCim_WY
- https://www.youtube.com/watch?v=G7Vboawafc4 (Uncredited)
- https://www.youtube.com/watch?v=5q0WWyYNsTs (Uncredited)
- https://www.youtube.com/watch?v=AH-9jE1uDPk
- https://www.youtube.com/watch?v=iSOWV-r_0J4 (Uncredited)
- https://www.youtube.com/watch?v=kol1Zy9xc8I
- https://www.youtube.com/watch?v=AH-9jE1uDPk
- https://www.youtube.com/watch?v=E-ukC-Jjwfg
- https://www.youtube.com/watch?v=QjkbB3lnRLw (Weird)
- https://www.youtube.com/watch?v=A2c2UeM9V3A (Uhhh)
- https://www.youtube.com/watch?v=FAk2oF0cByg
- https://www.youtube.com/watch?v=PLrudwJHycU (Kinda Uncredited)
- https://www.youtube.com/watch?v=bGnEu4UwsU4
- https://www.youtube.com/watch?v=5q0WWyYNsTs (Uncredited)
- https://www.youtube.com/watch?v=ZEwgtvKcB58 (Uncredited/Indian)

### Website Featuring My Program: ###
- https://repair.wiki/w/PS4_UART_Guide
- https://wololo.net/tag/bwe/
- http://www.logic-sunrise.com/recherche/bwe/
- https://www.biteyourconsole.net/?s=bwe
- https://psdevwiki.com/ps4/
- https://psx-core.ru/forum/48-3196-3
- https://consolefix.ru/aktivaciya-uart-dlya-diagnostiki-blod/
- https://vlab.su/
- https://gbatemp.net/search/3666652/?q=bwe&o=relevance
- https://gamegaz.com/2022122937784/
- https://www.psxhax.com/threads/release-bwe-ps4-nor-validator.6139/
- https://www.playstationhax.xyz/forums/topic/5259-release-bwe-ps4-nor-validator/
- https://www.psx-place.com/threads/tutorial-how-to-take-a-nor-backup-on-every-ps4.28070/
- https://tieba.baidu.com/p/8196671153
- https://yoschi.cc/gaming/es-ist-anscheinend-moeglich-ihre-ps4-ohne-backup/

### My Websites: ###
- https://www.betterwayelectronics.com.au/
- https://instagram.com/betterwayelectronics
- https://github.com/BetterWayElectronics/
- https://twitter.com/BwE_Dev
- http://www.ps5repair.com.au/

## Purchase Link ##

If you are a commercial user, I highly suggest you buy the software here: https://betterwayelectronics.com.au/bweps4norvalidator

I also sell Syscon writing hardware here: https://betterwayelectronics.com.au/#hardware

Provide your HWID (via the trial or provided application) and email it to sales(at)betterwayelectronics.com.au along with your proof of purchase to obtain your license key.

Other users will only be able to validate one dump.


![End](https://i.imgur.com/iauhGcv.png)
