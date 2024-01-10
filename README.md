# Better Way Electronics - PS4 NOR Validator & Syscon Patcher
 
![BwE](https://i.imgur.com/Wds9cCH.png)


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

	Downgrade Firmware (CoreOS Swap/Revert)
	Repair LoadBios -8 Error
	Repair SU-39176-6 Error
	Repair BlStorageHeader Error
	Repair checkUpdVersion Error
	Manipulate Entire Syscon (Debug Mode)
	Manipulate PSN Activation
	Repair Obscure UART Errors
	Store & Revert Syscon Images
	Rebuild Syscon 
	Change Boot Modes

	More Information/Guide: https://betterwayelectronics.com.au/sce_syscon.html or https://www.youtube.com/watch?v=hcmMSYmwSUQ


### Why is your software no longer free? ###
	My software was free from 2008-2022 and in that time I recieved next to no donations (under $500aud). While this was happening businesses were making money using my software.
	So while I updated weekly/monthly I got nothing in return but a few thank yous and blog posts. Now since 2022 I have become very busy, stopped repairing and started a PhD.
	
	So given this is a business to business product I feel it best to charge for it.
	
	If you enjoy my program visit https://betterwayelectronics.com.au/bweps4norvalidator to purchase a license!
	
	Each licence allows once PC and is locked to your HWID. You can change your HD and format your PC and the licence will work, but you cannot use it on another PC.
	You can also upgrade an existing license to a USB based one so you can use it on multiple PCS.
	
	Trials have been removed due to abuse! Hello Alexey <3

	Don't want to buy? Try the online version instead! https://validate.betterwayelectronics.com.au/
		
### Your program is a VIRUS/SPYWARE! WAAAH! ### 
	I protect my programs with Themida. The problem with this is that heuristically some AV software see it as a threat.
	This is totally fine and normal, but also very annoying and unavoidable.
	
	My program collects user data via the HWID generator as to be able to generate your license details. The validator itself also communicates with my website to store use data which must then match the HWID data.
	This is a totally normal and boring process that has nothing to do with spying on the end user. If you consider that me knowing that you are using my program is spying on you, then don't use my program.

### Whats up with the image that pops up when the program starts? ###
	Hey, I am allowed some creativity aren't I? I have no GUI so this is all I can do design wise. Older versions of my program had chiptunes, be happy they're gone!
	
### What is the HWID Generator? ###
	You use it to generate your Hardware Identification. I then use that to create your license file. The one that pops up when you first open the program is NOT ENOUGH! 
	You wont get a license without running the HWID Generator.
	https://betterwayelectronics.com.au/hwid.html
	
### Do people even read this? ###
	Unfortunately not
	
### Yeah but how often do you update it? ###
	Not that often, I always forget.

### Pro Tips ###
	Enter an obviously wrong value or press ENTER if there is no 'go back' menu options. You can also likely accept Y/N prompts with 1.



## TLDR ##
* TLDR; Will this fix my BLOD? Well yes and no, if there are sections that are corrupt it is possible to patch it with valid data from another PS4 (or from a different section) - but NOT perconsole data (maybe)!
* TLDR; Will this prove my BLOD is software based? Yes, if the dump comes up 100% valid then it is likely a hardware issue - I recommend enabling UART and seeing its output.
* TLDR; Will this fix my corrupt CoreOS? Yeah with a patched Syscon.
* TLDR; Will this fix my loadBios -8 Error? Yeah with a patched Syscon (Or reduced memory clk)
* TLDR; OK = OK, Warning = Weird but MIGHT be okay, DANGER = Bad

## Bulk NOR Tools Menu: ##

	Launches the comparison app, used for the bulk diagnosis and comparison of dumps (Put multiple .bin files in the same directory). Features multiple output and filter options.
	
		1. Compare Specific Version Only
		2. Compare Specific SKU Only
		3. Compare Specific Version & SKU Only
		4. Compare All Dumps

		1. Compare Offsets (Hex)
		2. Compare Offsets (ASCII)
		3. Compare Offsets MD5
		4. Compare Offsets Entropy
  		5. Compare Offsets Statistics
		6. Double Offset Comparison (Data 1 & Data 2)
		7. Double Offset Comparison (Data 1 & MD5 2)
		8. Double Offset Comparison (MD5 1 & MD5 2)
		9. Dynamic MD5 Calculation
		10. Compare File Entropy & Byte Count
		11. Compare File MD5
		12. Sort Dumps Into Folders (SKU - FW)
		13. Extract Dumps by Offset

## Syscon Menu Options: ##
	
	Syscon Menu:

		1. Auto Patch
			Will automatically grab the last 080B and replace it with the first in the current active slot or blank out the latest, depending on your Syscon.
   
		2. Manual Patch
			If it cannot automatically patch, or if you decide to manually patch you may do the above yourself.
			You must then replace the last active 080B with an earlier one, or with an empty slot/space. Sizing is automatic so if you go over it will auto-trim.

## NOR Menu Options: ##

	1 - Select Different Dump

   		Return to main menu!
	
	2 - Extract Dump (2 Methods)
		
		1. Extract (BwE Style)
	
			Extract based on literal files and does so dynamically based on their size.
	
		2. Extract (Traditional Style)
	
			Extracting file sections pursuant to Sony's file blocks.
	
	3 - Patch (/Patches/)
	
		Designed to load .bin patches from the /patches/ directory. It will interpret and auto locate patch offsets if they've been extracted by my program. If not it will ask for a start address.
	
	4 - Patch Corrupt CoreOS (SU-30631-3 Error)
	
		Basically an automated version of what Andrew Paul suggests (https://youtu.be/35DFGCim_WY). It will scan the CoreOS and patch the corrupt sections within about 1 second.
		If you have this error (or SU-37553-3) but my program tells you that there is no corruption, you need to replace the actual NOR IC itself and reflash it.
		Another option is to wipe the flash entirely with FF or 00 and re-read it and THEN reflash your original valid dump. Do not just use the default wipe+flash option in your software.
		
	5 - Patch Corrupt EAP Key (Panic EAP Key Not Available Error) (SU-30645-8 Potentially)
		
		Compare both EAP keys against eachother, if one is corrupt or blank it will copy it over. If both are blank it will generate a new one for both slots. If patch fails, there is a reverse patch option which copies the data the other way around.
		Repairs BLOD related to EAP Key panic.
		
		Guide: https://www.youtube.com/watch?v=noS8wfZA99g 
		
	6 - Patch & Switch CoreOS + Southbridge Slots (LoadBios & Downgrade)
	
		Allows for switching of the CoreOS and or Southbridge slots to aid in either downgrading or repairing LoadBios/No Beep errors. Must not be used without first backing up Syscon chip.
		Header patches are provided but you can also insert your own. This is because some patches may not work, you may need to apply multiple until it works.
		
		To see what the previous version is, simply patch the syscon then upload and run it without patching NOR. The UART will tell you the standby mode, which is the previous FW.
		
		Apply in sequence until BLOD with checkUpdVersion 0xfffffff AND secure loader version lower than standby version.
		
		1. Auto Generate CoreOS Header & UART Patches
			Automatically applies x14 patches, it is up to you to determine which is valid. You will have to upload each one individually and use UART to see which one is successful or not.
			
		2. Manually Patch CoreOS Header & UART
			Select one of the 14 patches yourself, if you are confident in the patches that is. This may save some users time, but I doubt it.
			
		3. Generate Legitimate CoreOS Header Patch
			Creates a patch based on what the PS4 will naturally produce. This requires you to update the current console to the same version via safe mode. Instructions and automated patching within the app.
			
		4. Patch Southbridge Header Only
			May fix issues with patches that worked, but have EMC related issues in the UART.
				
		See Guide/s:
			https://betterwayelectronics.com.au/sce_syscon.html
			https://betterwayelectronics.com.au/syscon.html
			https://www.youtube.com/watch?v=hcmMSYmwSUQ
		
	7 - Patch Empty or Corrupt NVS (CID & UNK) Blocks (1CA, 1CD, 1C9, 1CC)

		Allows for patching of these corrupt blocks by swapping them with their backup data. Run this BEFORE patching UART or anything else.
		Confirm the areas are corrupt/empty by running validator. Not as effective on 10xx and 11xx series PS4.
	
		Both options detect blank blocks and mismatch blocks and repairs by swapping blocks or regenerate them entirely if needed.
		
		1. 1CA000-1CAFFF <-> 1CD000-1CDFFF (UNK + CID)
		2. 1C9000-1CA610 <-> 1CC000-1CD610 (UNK + CID)
		
		Guide: https://www.youtube.com/watch?v=noS8wfZA99g 
		
	8 - Patch or Change Southbridge (EAP & EMC)
	
		Validation and patching of your entire Southbridge firmware.
		Allows for the repair of consoles that have no power response (caused by corrupt Southbridge).
		Fixes 'EMC VERSION DOWN' errors.
		Allows you to replace the Southbridge chip with a cheaper model (46 to 36 for example).
		Allows for the replacement of processor bundles that have different Southbridges (SAE/SAD Slim 21xx -> 22xx, Pro 71xx -> 72xx)
		
	9 - Patch or Change WiFI/BT Firmware (Torus)
	
		Allows for the validating and patching of corrupt WiFi/BT Firmware and or the changing between different physical modules.
		
	10 - Enable/Disable/Toggle 17 System Flags
	
		These flags will work without the need to jailbreak. 
	
			1. Enable/Disable UART
			2. Enable/Disable IDU Mode (CE-34706-0, CE-30022-7)
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
			13. Modify SAMU Boot Flag
			14. Modify Memory Clock Speed
			15. Swap X and O Buttons
			16. Change/Reset Resolution
			17. Enable/Disable UART, Memory Test & RNG/Keystorage Test
			
		Press ENTER to cancel and return to main menu if you do not want to make any changes!
	
		UART is well vetted, the others are not so use at own risk.
		I recommend the following UART guide: https://repair.wiki/w/PS4_UART_Guide It includes drivers and programming software you may need.
		
		Memory Test mode tests the memory within UART. It will do a checksum to confirm if its valid or not. Disable when finished to avoid issues.
		
		Update mode may fix CE-35888-2/SU-35888-2 errors - it may not and you will require repair to your BD chip.
		
		MANU Mode will enable Service Mode on older firmwares.
		
		Memory Clock Speed can be adjusted from 400mhz to 2250mhz. Underclocking may repair Loadbios and Memory errors!
		
		Info on IDU Mode: https://youtube.com/watch?v=HlpjWLbL67Y
		
	11 - Regenerate New NVS (CID & UNK) (Repair Reset Loop/No Power/3BOD/Some UART Errors)
	
		Will entirely regenerate and reset your NVS while also retaining important per-console data. Will likely fix reboot loops, no power and 3 beep of death issues.
		Can also likely repair consoles that have sceRegMgrCntlStart or partition mount errors or other obscure UART errors.
		
		Will ask for patch options, they're only really important if you're doing an APU change/swap or if the patch failed. Yes you can do that!
		
	12 - Patch IDATA Keys 
	
		Experimental. Will corrupt/damage/alter part of your IDATA file, which stores a lot of keys. This will be developed further in the future.
		Banned PSN? Give it a go!
	
	13 - Upload Only
	
		If this appears, you have a good connection to my server and you can upload without validating - good if you forgot to do it earlier. Does not appear if offline.
		Can also upload your UART output if you saved it as a .txt file and stored it with your NOR dump. I highly recommend doing this for BLOD consoles!
	
	13/14 - Validate
	
		Will scan the entire dump from start to finish and produce a readable validation output in HTML format. Becomes option 11 if server is offline.


## File Information: ##
	File MD5: 84229BF7B2D68E264FEB2D46FD10CD50 
	Technical Support: spamlist@betterwayelectronics.com.au

	System Requirements:
	Minimum 4 CPU Threads
	Windows XP, 7, 8 or 10 (64bit) 
	9mb+ Storage Space

	Archive Password:
	BwE

## Stats: ##
	29,755 Lines of Code
	3389+ Possible HTML Outputs
	1750+ Hashes
	
## Version History: ##
	2.5.1 (10/1/24) Updated Southbrige Patcher, Updated Extractor, Updated Validations, UI Improvements (Can Return After Validation)
	2.5.0 (11/12/23) Updated Validations (Including 11.02 Specific), Added Statistics To Bulk Tools, Bug Fixes
	2.4.9 (15/11/23) Improved Previous Firmware Detection, Updated Validations, Removed Block Matching (Not Reliable)
	2.4.8 (21/10/23) Updated Validations, Changed CoreOS Header Interpretation, Updated 1CA + 1CD and 1C9 + 1CC (UNK + CID) Patching & Validation, Dump Upload Bugfix, Dump Extract & Patch Bugfixes
	2.4.7 (19/10/23) Added WiFi/BT Patching/Changing Option, Fixed Some Sub-Menu Options (Press Enter To Bail On Patching), Other Small Forgettable Fixes/Changes
	2.4.6 (2/10/23) Added Resolution Patch, Added IDATA Patch, Fixed EAP Patcher (Partially Corrupt Bug Fix), Added More Flags, Improved CID & UNK Validation, Updated UART Reader (Space to Clear, Enter to Quit)
	2.4.5 (20/9/23) Updated Validations (11.00), Updated Southbridge Patcher, Updated Potential Lowest FW, Added 138 IPL Hashes + 93 KBL Hashes + 53 Torus Hashes, Fixed Bulk Dump Extractor.
	2.4.4 (12/9/23) Added Bulk NOR Extractor, Reworked Menu (Moved Dump Tools), Updated Validations
	2.4.3 (7/9/23) Added Motherboard Type Detection, Significantly Updated NVS Regenerator, Updated NVS Validation (CID & UNK), More Validations Updated to Suit 10.71, Fixed/Updated HTML Output
	2.4.2 (29/8/23) Added NVS Regenerator, Updated Validations and Definitions, Updated EAP Patcher, Updated Corrupt Block Patcher
	2.4.1 (23/8/23) Critical Bug Fix (Syscon Patcher) (Thanks to Updated Menu Behaviour...)
	2.4.0 (23/8/23) Added Southbridge Patching/Converting, Updated Validations, Code Optimization, Updated Menu Behaviour, Updated HWID Generator
 	2.3.9 (13/8/23) Updated to Suit 10.71, Updated CID Validation
	2.3.8 (9/8/23) Added New Validations & Flags, Bug Fix in Comparison Tool
	2.3.7 (2/8/23) Updated Comparison Tool (Better Outputs, More Options), Changed EAP Key Patching Slightly.
	2.3.6 (2/8/23) 9th Hour Critical Bug Fix. I Need Beta Testers!
	2.3.5 (1/8/23) Major Update to EAP Key Patching, Updated Version Detection, Changed SDK to 'Lowest FW' (Who Cares About SDK), Added 'Potential Previous FW' (Based on EMC - Not Reliable), Added Southbridge Type In Main Menu.
	2.3.4 (31/7/23) Updated Validations to Suit 10.70 Firmware, Removed Individual File Entropy, Updated UNK/CID Validations & Flags, Other Validation Improvements!
	2.3.3 (23/7/23) Updated Syscon Patching, Updating Southbridge Detection (Chip Type), Re-Arranged Menu, Other Small/Important Changes
	2.3.2 (18/7/23) Added Block Validation for EMC_IPL, EAP_KBL and Torus (Detect & Describe Southbridge Version/Type), Improved CID Validation, HTML Output Fixed
	2.3.1 (12/7/23) Changes for Chinese Language Users
	2.3.0 (11/7/23) Added SDK Versioning (Lowest Downgradeable Firmware), Better FW Detection, Slightly Changed Warning for Memory Overclocking, HWID Generator Update, Better Support for Chinese Systems
	2.2.9 (10/7/23) 8th Hour Bug Fixes! (Nothing Major).
	2.2.8 (9/7/23) Updated Syscon Patching, Updated Validations, Future Proofing, Bug Fixes.
	2.2.7 (27/6/23) Updated UNK Validation, Updated Syscon Patching, Better Suited for Current OFW.
	2.2.6 (12/6/23) Wider System Compatibility, Updated & Fixed HWID Processes
	2.2.5 (10/6/23) Bug Fixes, New HWID Generation Process
	2.2.4 (9/6/23) Updated Syscon Patcher, Bug Fix to Patching & Extracting, Updated Validations & Results, Server Updates (Future Proofing/Downtime Protection)
	2.2.3 (27/5/23) Updates to Corrupt/Blank Area Patching, Update to CID Corrupt/Blank Block Detection, Better Auto Deletion of %TMP%, Updated Unlisted/New Results, UART Reader Updated, HWID Generator Updated.
	2.2.2 (9/5/23) Greatly Improved Patching & Validation for CID/UNK Areas, Potentially Less Issues With HWID Generator, Better Menu Flow.
	2.2.1 (2/5/23) Fixed Compatibility Issue #5 (Maybe), Fixed Accidental Highlighting, Fixed Assignment Operator Error/s, Other Improvements!
	2.2.0 (1/5/23) Fixed Versioning, Fixed USB Licensing, Other Small Changes
	2.1.9 (30/4/23) Added USB License Support, Bug Fixes, Fixed SB Patch Error, Better UART Log Handling, Added Unlisted/New Validations, Improved UNK Validation (Block Corruption Detection)
	2.1.8 (28/3/23) Bug Fixes, Updates to Validation Processes, More Windows 11 Support
	2.1.7 (24/3/23) Added the 6 New Patches to Auto Patcher (Total of 14! - I Recommend New Method!), Some Validation Updates, Changes to Internal Messages
	2.1.6 (22/3/23) Added New CoreOS Header Patching Methodology & 6 New Patches, Added UART .txt Uploading (Please Use!), Added Unlisted & New Validations, Other Small Fixes.
	2.1.5 (9/3/23) Significant Updates and Changes to UNK & CID Validations, Added New Empty 1CA000-1CA5FF / 1CD000-1CDFFF Patch Option, Added Unlisted & New Validations.
	2.1.4 (6/3/23) Critical Bug Fix In Downgrade Patches (Whoops)
	2.1.3 (5/3/23) Upgraded/Reworked System Patch Handling & Validation (Important Update!), Added New UNK Validation, Won't Ask For UART @ End If Already Enabled!
	2.1.2 (5/3/23) Added x2 Additional Downgrade Patches, Fixed SAMU Boot Flag, Increased Memory CLK to 2250mhz (Samsung HC-25 Recommended), Modified Serial Reader (Removed .BIN Output), Renamed to UART Reader
	2.1.1 (3/3/23) Critical Bug Fix In Syscon Patcher
	2.1.0 (2/3/23) Added SAMU Boot Flag and Memory Clock Speed Editing (Can Potentially Fix LoadBios/Memory Issues), Added x2 Additional Syscon Patches, Removed Southbridge Patch From Main Patch Option (Only Use For SB FW Errors), Patching Bug
	2.0.9 (1/3/23) Small Bug Fixes, Trial Removed
	2.0.8 (23/2/23) Syscon Patcher Update (Will Also Fix Closing Bug)
	2.0.7 (21/2/23) Further Bug Fixes (Bug Testing Sucks), Added Flags to CID, Updated UNK Validation, Updated Unlisted Results, More Unique Values Thanks To Thailand PS4's, Updated 4 Year Old Validations (Wow).
	2.0.6 (20/2/23) Bug Fixes For Bug Fixes, Better Handling of Trial Users.
	2.0.5 (19/2/23) Bug Fixes to HWID Handling (Also Updated HWID Generator), Bug Fixes to Syscon Patcher, Some Validation Changes/Upgrades
	2.0.4 (13/2/23) Improved Validation, Preparing For Auto Corruption Repair (Some Areas), Added Unlisted Results, New Flags CID/UNK, Other Mild Changes.
	2.0.3 (7/2/23) Improved Syscon Auto Patching (Less Chance Of Manual Patching) (Still Beta! Report All Syscon Patch Issues!), Fixed Potentially Broken Trial Mode + HWID Stuff,  Fixed Other Patching Issues.
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
	DarkNESMonk
	JEFF
	Wildcard
	fail0verflow
	PDJ
	eussNL (<3)
	cfwprpht
	judges
	3absiso
	pearlxcore
	DEFAULTDNB
	Stooged
	GregoryRasputin
	Elhout
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
	Indonesia!
 	Egypt!
	SCE
	You! 
	
Proudly made in Perl with Notepad++ by BwE, alone </3 
To be clear, there has been nobody but myself contributing to the source code of this program! I have only got support on what to do at times!
Thanks to all of my nice loyal and friendly customers!

Made In Australia!

## Links ##

### Support/Donate: ###
https://www.buymeacoffee.com/BwE

### Console Repair Discord: ###
- https://discord.com/servers/console-repair-discord-754165317961383997
- https://discord.gg/pXeUHMy

### Videos Featuring My Program: ###	
- https://www.youtube.com/watch?v=hcmMSYmwSUQ <--- My Video!
- https://www.youtube.com/watch?v=noS8wfZA99g <--- My Other Video!
- https://www.youtube.com/watch?v=NDNld92tsZc <--- My PS5 Video
- https://www.youtube.com/watch?v=fE4qGHJyX8E
- https://www.youtube.com/watch?v=q1F0AL3ttjY
- https://www.youtube.com/watch?v=W7RpkG5hiA0
- https://www.youtube.com/watch?v=2hXO60rUt40
- https://www.youtube.com/watch?v=D8-AMvsfadM (Uncredited)
- https://www.youtube.com/watch?v=syfiph70reQ
- https://www.youtube.com/watch?v=NBktKSx4FzQ
- https://www.youtube.com/watch?v=LCOUepj5_8o
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
- https://www.youtube.com/watch?v=m9nopeQw6dI (Uncredited)
- https://www.youtube.com/watch?v=mSiMdqTJTk8 (Uncredited - Spanish)
- https://www.youtube.com/watch?v=mEDRb-XIqlw (Uncredited - Spanish)
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
- https://www.youtube.com/watch?v=ZEwgtvKcB58 (Uncredited)

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
- https://psx-core.ru/forum/48-3196-5

### My Websites: ###
- https://www.betterwayelectronics.com.au/
- https://instagram.com/betterwayelectronics
- https://github.com/BetterWayElectronics/
- https://twitter.com/BwE_Dev
- http://www.ps5repair.com.au/

## Purchase Link ##

If you are a commercial user, I highly suggest you buy the software here: https://betterwayelectronics.com.au/bweps4norvalidator

I also sell Syscon writing hardware here: https://betterwayelectronics.com.au/#hardware

Provide your HWID (via the provided application) and email it to sales(at)betterwayelectronics.com.au along with your proof of purchase to obtain your license key.

Don't want to buy? Try the online version instead! https://validate.betterwayelectronics.com.au/


![End](https://i.imgur.com/iauhGcv.png)
