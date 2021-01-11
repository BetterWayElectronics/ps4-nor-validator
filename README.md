# Better Way Electronics - PS4 NOR Validator
 
Hello!

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

Launches the comparison app, used for bulk diagnosis of offsets

	1. Compare Offsets (Result - SKU - Filename)
	2. Compare Offsets MD5 (MD5 Hash - Filename)
	3. Compare Offsets Entropy (Entropy - Filename)
	4. Compare File MD5 (MD5 Hash - Filename)
	5. Double Comparison (Result 1 - Result 2 - Filename)
	6. Dynamic MD5 Calculation (Size - MD5 - FW & SKU - Filename)

##### 2 - Patch (/Patches/) #####

Designed to load .bin patches from the /patches/ directory. It will interpret and auto locate patch offsets if they've been extracted by my program.

##### 3 - Enable/Disable UART #####

Enabling/Disabling the UART flag within the PS4 - Will work without the need to jailbreak. If this does not work check the UNK UART Flag status and email me!

##### 4 - Extract (BwE Style) #####

Extract based on literal files and does so dynamically based on their size

##### 5 - Extract (Zecoxao Style) #####

Extracting file sections pursuant to Sony's file blocks

##### 6 - Validate #####

Pretty obvious, will scan the entire dump from start to finish and produce a readable validation output in HTML format

#### Upload Feature: ####

As of 1.5.5 there is a feature to upload your dump directly to me. These dumps will be used to improve the validation of this program.
Users who abuse this system may be banned from this application and or future updates of it.

#### Stats: ####
- 14,480+ Lines of Code
- 2220+ Offsets Read

#### Version History: ####
- 1.5.7 (11/1/21) Improved Statistics, Removed Some Unlisted Results (Improved Validation), Updated Upload Feature, Improved Compiler
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
- File MD5: E295F19A282CE7F2CC613C25AF7ACD1A
- Technical Support: heeeeeeeelp@betterwayelectronics.com.au

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
- SCE
- You! 

Proudly made in PERL with Notepad++

Thanks to all the people who email me and beg me to update my program <3 

#### Console Repair Discord: ####
https://discord.gg/pXeUHMy

#### Forums: ####
https://www.psxhax.com/threads/release-bwe-ps4-nor-validator.6139/
https://www.playstationhax.xyz/forums/topic/5259-release-bwe-ps4-nor-validator/

#### My Website: ####
https://www.betterwayelectronics.com.au/
http://www.ps5repair.com.au/

Made In Australia!


