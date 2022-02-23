# Better Way Electronics - PS4 NOR Validator
 
![Github Logo](https://i.imgur.com/QoUGxZb.png)


This program is the release version of my PS4 NOR Validator, it is designed solely to validate the NOR flash of your PS4 console!

Why would you need to do this? Well if your console has suddenly died and has what is called the 'BLOD', the NOR can be the reason why.
Using my program will allow you to validate literally every single byte of the NOR (or over 2100 specific areas) - allowing you to see where or if it is corrupted.

The most common area of corruption that causes the BLOD is the CID. Some areas of this section can actually be repaired, if you're lucky! I and others have done this!
Don't forget to use my Comparator tool to help you understand what the difference is for a specific section of the NOR. It will help you with patching!

Other areas can be inter-changed between different consoles and are more suited for repair, the WiFi/BT module is a good example of this.

So fundamentally, this program is for console repairers like myself. If you are indeed a repairer and run a business I can make a custom 'bulk' version for you! 
But for now, feel free to put multiple *.bin files in the working directory as my program will provide a selection menu.

I am also happy to give advice on your NOR or help interpret your results, just post on the forum or give me an email. If you can bypass my filter, send me a link to your NOR!

If you encounter any errors or weird results - or better yet if your NOR is labled danger in any areas, but still runs fine - let me know!

Keep in mind the CoreOS and other large encrypted areas could still be corrupt regardless of the results (I cant check every byte in an encrypted section, hence alt validations).
This program is NOT perfect, but it is WAY better than just using a hex editor or never truely knowing if your BLOD is caused by the NOR!

This also goes above and beyond that of the psdevwiki page regarding the main flash of the PS4 (Thank you cfwprpht). 

#### TLDR: ####

##### Will this fix my BLOD? #####
Well yes and no, if there are sections that are corrupt it is possible to patch it with valid data from another PS4 - but NOT perconsole data!
##### Will this prove my BLOD is software based? #####
Yes, if the dump comes up 100% valid then it is likely a hardware issue - I recommend enabling UART and seeing its output.

#### Menu Options: ####

##### 1 - Comparison #####

Launches the comparison app, used for the bulk diagnosis and comparison of dumps (Put multiple .bin files in the same directory). Features multiple output options.

	1. Compare Offsets (Hex)
	2. Compare Offsets (ASCII)
	3. Compare Offsets MD5
	4. Compare Offsets Entropy
	5. Double Offset Comparison
	6. Dynamic MD5 Calculation
	7. Compare File MD5
	8. Compare File Entropy & Byte Count

##### 2 - Patch (/Patches/) #####

Designed to load .bin patches from the /patches/ directory. It will interpret and auto locate patch offsets if they've been extracted by my program. If not it will ask for a start address.

##### 3 - Patch Corrupt CoreOS (SU-30631-3 Error) #####

Basically an automated version of what Andrew Paul suggests (https://youtu.be/35DFGCim_WY). It will scan the CoreOS and patch the corrupt sections within about 1 second.
If you have this error but my program tells you that there is no corruption, you need to replace the actual NOR IC itself and reflash it.

##### 4 - Enable/Disable/Toggle UART, IDU, Boot Parameter, Memory Budget or Slow HDD Mode #####

These flags will work without the need to jailbreak. UART is well vetted, the others are not so use at own risk.
I recommend the following UART guide: https://repair.wiki/w/PS4_UART_Guide

##### 5 - Extract (BwE Style) #####

Extract based on literal files and does so dynamically based on their size

##### 6 - Extract (Zecoxao Style) #####

Extracting file sections pursuant to Sony's file blocks

##### 7 - Upload Only #####

If this appears, you have a good connection to my server and you can upload without validating - good if you forgot to do it earlier. Does not appear if offline.

##### 8 - Validate ##### 

Pretty obvious, will scan the entire dump from start to finish and produce a readable validation output in HTML format. Remember, you can put multiple dumps in the same directory. Becomes option 7 if offline.

#### Notes: ####

As of version 1.5.5 there is an ability to upload dumps directly to me. I use these to improve the program and validations.
Abusing this service will result in your ban from future use of my validator. Mislabling files that are clearly corrupt as working will result in a ban.

Regarding Anti-Virus:

I protect my program with Themida. The problem with this is that heuristically some AV software see it as a threat.
This is because people who make or redistribute old malware also use Themida to help make themselves undetected.

Ultimately, it is up to you to trust the program and me. I encourage you to upload to a sandbox to see for yourself.

https://www.virustotal.com/gui/file-analysis/OTg2NjAzOTRhNjg4NGMxZmIzYjRhYTQxNThmNjk0ZjQ6MTY0NTYyNjc2NA==

#### Stats: ####
- 16,360+ Lines of Code
- 2430+ Offsets Read
- 2757 Possible Results/Outputs

#### Version History: ####
- 1.8.5 (25/1/22) New Validations, Added Unlisted/New Results, New Statistical Values, Fixed Results HTML File Name Bug, Improved CID & UNK Validation (Removed False Warnings), Cosmetic Fix To 'Validation Complete', Added Block For v1.8.0 & Below.
- 1.8.3 (26/11/21) Improved File Handling When Patching, Added UART Enabling Question After Validation (Requested Feature), Bug Fix Handling Files NOT In /Dumps/ (Whoops), Bug Fix Handling UART.
- 1.8.2 (21/11/21) Improved Validation & Classification of WiFi/BT Modules, Improved Validation of All Encrypted Sections, Added New WiFi/BT FW MD5s, Bug Fix Handling Files In /Dumps/.
- 1.8.0 (15/11/21) Added Unlisted Results, Added New Flags & Patches (Boot Parameter (Dev, Assist, Release), Memory Budget and Slow HDD Mode), Added New WiFi/BT FW MD5, Changed Patch Offset Interpretation For WiFi/BT, Fixed Patching Showing Dump MD5 Instead of Patch MD5, Changed Interpretation of Dump Files (Save Time With Hardcore Corruption/Wrong Files), Cosmetic Fixes, Connection Fixes (Temporary).
- 1.7.4 (7/10/21) Fixed Uploading Criteria, Fixed Server Side Uploading Issue (58 Dumps Lost!), Added Unlisted Results
- 1.7.3 (22/8/21) Fixed IDU Patching, Added Unlisted/New Results (Thank You Uploaders!)
- 1.7.2 (30/7/21) Fixed Mishandling of Bulk Warning/Danger Results (Significantly), Added Unlisted/New Results.
- 1.7.1 (25/6/21) Fixed Uploading Questions, Added MB Serial to Outputs, New Spash Screen.
- 1.7.0 (23/6/21) Added Question Regarding Dump When Uploading, Added New CID Validation (Weird Key or Flag), Fixed UART Validation, Added Unlisted Results.
- 1.6.9 (26/5/21) Fixed Internal Code Issues, Added Unlisted Results, New Splash Screen (Potentially last update for a short while).
- 1.6.8 (16/5/21) Updated Internal Comparison Application, Improved Serial Number Validation (MB Series), Added Unlisted Results.
- 1.6.7 (25/4/21) Repaired UNK 1200 Series Validation, Added Unlisted Results.
- 1.6.6 (12/4/21) Added Unlisted Results, Improved Validation, Changed Output Styling.
- 1.6.5 (31/3/21) Added CoreOS Statistical Analysis, Changed Some Results, Changed Some Output Formatting, Returned to Previous Packer.
- 1.6.3 (30/3/21) Added CoreOS Patcher (SU-30631-3 Error Specific), Updated Results, Added Unlisted Results, Fixed Readme, Changed Packer.
- 1.6.2 (18/3/21) Repaired CID Validation, Improved Handling of 72xx, Added Unlisted Results, Improved Dump Uploading Process.
- 1.6.1 (20/2/21) Repaired CID Validation, Added Unlisted Results (Thanks Uploaders!)
- 1.6.0 (4/2/21) Added IDU Mode Patcher, Improved Validations, Added Unlisted Results.
- 1.5.9 (29/1/21) Major Improvement to CID and UNK Validations, Added Unlisted Results, Improved UART Patching, Better Handling of 1200/Pro/Slim Validations, Added v1.5 of Comparator (Comparison Tool, Option 1)
- 1.5.7 (11/1/21) Fixed Version Checker, Improved Statistics, Removed Some Unlisted Results (Improved Validation), Updated Upload Feature, Improved Compiler
- 1.5.6 (10/1/21) Improved CID and UNK Validations, Updated Unlisted Validations, IDU Flags Added, Some Code Optimization
- 1.5.5 (8/1/21) Updated Pro/Slim Specific Validations, Updated Unlisted Validations, Updated CID Validations, Updated UNK Validations, Added Dump Upload Feature
- 1.5.3 (5/12/20) Updated Unlisted Validations, Updated WiFi/BT MD5s & Entropy Validation
- 1.5.2 (20/11/20) Updated WiFi/BT MD5s, Added 2nd UART Flag, Updated Unlisted Validations
- 1.5.1 (3/11/20) Updated Unlisted Validations, Added UART Enabler, Removed Unused Validation Option, Added Basic Loader
- 1.5.0 (30/10/20) Updated Unlisted Validations, Upgraded Existing Validations, Removed Loader (Secret Patcher Coming Soon!)
- 1.4.9 (3/5/20) Added 21xx Series Specific Validations, Updated Unlisted Validations
- 1.4.7 (23/3/20) Added Dynamic Comparison, Updated Unlisted Validations
- 1.4.6 (1/2/20) Just Keeping It Fresh! (May have fixed issues stopping the program running, if not let me know!)
- 1.4.4 (16/8/19) Added and Improved Validations (CID & UNK) Including New WiFi/BT FW MD5
- 1.4.2 (7/4/19) Added More Validations (Firmware & Console Specific), Improved Various Sections (CID & UNK Mostly)
- 1.4.1 (1/3/19) Prettied Up Outputs, Minor Rewording (Sorry!).
- 1.4.0 (1/3/19) Added Zecoxao Extraction Methodology (Will Add More Zecoxao SELF Stuff Later), Added FW/BIOS Versioning, Added Additional Entropy Validation & Various Improvements Throughout.
- 1.3.8 (21/2/19) Added Additional Validations (To Suit Slim/Pro), Repaired/Improved CID Validation, More MD5s & Table Based Results.
- 1.3.5 (30/1/19) Added CoreOS Reference Points (Additional CoreOS Per-Console Validation).
- 1.3.3 (24/1/19) Reworked And Improved Both CID And UNK Sections Again, Added More MD5's, Added Application Version Checker, Removed Colored Bars, Added Comparator & Other Improvements Throughout.
- 1.3.1 (19/1/19) Added More Validations & MD5's, Repaired Minor Bug.
- 1.3 (15/1/19) Completely Reworked And Improved The CID Section And Added Additional Validations To The UNK Section & I Also Improved Some Other Validations Throughout.
- 1.2.6 (18/12/18) Hopefully Fixed 'Black Screen' Issue, Recompiled In 32bit.
- 1.2.5 (17/12/18) Added 2 New Flags (Possibly Initialization Flag?), Changed Validation Results, Improved Output/Info (HTML) & Added MD5's. 
- 1.2 (8/12/18) Improved All Alt Validations, Repaired Vtrm1, Internal Typo & Added Repetition Checks.
- 1.1.1 (29/11/18) Typo Again, Made The SKU Not Come Up As Unlisted & Added Some MD5's.
- 1.1 (28/11/18) Improved VTRM & CID Validation, Typo Fixes & Better Colours. 
- 1.0 (27/11/18) First Release!

#### More Information: ####
- File SHA256: E529BE57440ADBA6D1BD40D348BA9B7E478060BC7BFB411D0847866010873EE4 
- Technical Support: heeeeeeeelp [at] betterwayelectronics.com.au

#### System Requirements: ####
- Minimum 4 CPU Threads
- Windows XP, 7, 8 or 10 (64bit) 
- 9mb+ Storage Space

#### Archive Password: ####
BwE
 
#### Greetz/Credit: ####
- Thailand (Xohke!)
- PS3/PS4 Dev Wiki (+ Its Contributors)
- eussNL (<3)
- cfwprpht
- judges
- 3absiso
- pearlxcore
- DEFAULTDNB
- Stooged
- GregoryRasputin
- zecoxao
- Cliques Unique (For Discord Help)
- ProConsoles NL
- Centrino
- Viktor TechStars Romania
- Nikesh
- Orbis/Akiong
- YTAndrewPaul
- Palestine!
- SCE
- You! 

Proudly made in PERL with Notepad++

Thanks to all the people who email me and beg me to update my program <3 

#### Support/Donate: ####
https://www.buymeacoffee.com/BwE

#### Console Repair Discord: ####
https://discord.gg/pXeUHMy

#### Forums: ####
- https://www.psxhax.com/threads/release-bwe-ps4-nor-validator.6139/
- https://www.playstationhax.xyz/forums/topic/5259-release-bwe-ps4-nor-validator/
- https://www.psx-place.com/threads/tutorial-how-to-take-a-nor-backup-on-every-ps4.28070/

#### Video Featuring My Program: ####
https://www.youtube.com/watch?v=35DFGCim_WY

#### Website Featuring My Program: ####
- https://repair.wiki/w/PS4_UART_Guide
- https://psdevwiki.com

#### My Websites: ####
- https://www.betterwayelectronics.com.au/
- http://www.ps5repair.com.au/

Made In Australia!

![Github Logo](https://i.imgur.com/dshQf7P.png)
