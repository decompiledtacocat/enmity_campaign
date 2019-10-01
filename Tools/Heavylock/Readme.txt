*****************************************************************************
* HEAVY LOCKER by BlacKDicK (raogabriel@oceanfree.net)                      *
*****************************************************************************
* WARNING:                                                                  *
* I am not resposible in any ways if this program do any damage to your     *
* game files. Run it at your own risk. This tool is free, just give me and  *
* ShadowFlare for her wonderfull SFMPQApi some credit.                      *
*****************************************************************************

*****************************************************************************
* FOR GOD SAKE: THIS TOOL WILL ONLY WORK IF THE SELECT FILE HAS A EMBBEDED  *
* (listfile), otherwise it will not work.                                   *
*****************************************************************************

What is this?
Is a special tool that I´m still developing that will optmize MPQs (reduce
the file size). And since War3 Maps are MPQs, they get optmized too.
The optmized file will open fine both on WINMPQ and MPQVIEW, but any changes
to it using WINMPQ will probably increase the file size to its initial state. 

It does not support files within MPQs with special localeIDs. It only works
with the "default localeID", wich is english btw. If there is any file inside
the input MPQ that is not "english" it will be ignored.

I also ask users to "test" the optmized file/map before releasing it coz this
tool is still on development stages, so it may have some bugs. Note that the
War3 maps "Obfuscate Script" feature may corrupt maps. Use it at your own risk.

USER OPTIONS:

* Include (listfile)
   Turn this ON to make sure the new file will have a (listfile) inside it,
otherwise the new file will not have a (listfile).

* Include (attributes)
   Turn this ON to add the embbeded (attributes) to the new file. BTW,
the (attributes) file s pretty useless unless in some special cases (MPQs).

* Keep Table Size will make sure the new MPQ will have the same TABLE size
of the input MPQ.

* Force ZLIB-Deflate
   Will add the files using the ZLIB-Deflate algorithym, wich is only
supported by the War3 and newer games. Note that if ZLIB is on the WAVE
compression is not used. If you´re dealing with war3 stuff,you can check
this and save some extra-bytes since this compression is better.

Old games do not support this compression, but you can still use MPQDRAFT
with ShadowFlare Compression/Decompression Plugin v1.00 to "enable" this
feature on older games.
Grab ShadowFlare Compression/Decompression Plugin v1.00 here:
http://shadowflare.ancillaediting.net/cgi-bin/download.cgi?SFComp.zip

* Use Map Optmizations (Better use this only for RoC and FT Maps)
  This will enable the user to set some specific MAP OPTMIZATIONs. 

* Clean SLK will remove "comments" from any emmbedded *.SLK
(There are probably still some bugs remaining on the SLK optmization,
so it is a good idea to test your maps before releasing them)

* Clean TXT/J/AI will remove empty lines and comments from those file-types.

* Optmize Minimap will let you choose a new quality (%) to the minimap.

* Remove war3map.imp will remove the "war3map.imp" file. This file is used
with W3/FT maps to list the imported files on the map. Remove that to make
things harder to map-stealers.

* Lock Map (Better use this only for RoC and FT Maps)
   This will lock the map (enable the user to select wich protection will
be used). Locked maps may be openable or not on the WE, depends wich Lock
Mode" is used (See bellow).Please keep backups coz this can´t be undone.

* Lock Mode
   This will control the kind of protection that will be used.
"Preview Only" will lock the map and it will still be openable on the WE,
but the triggers will not show on the WE. "Full Lock" will completely lock
the map,allowing you to choose some obfuscate options and leaving the map
not openable by the WE.

* Buffer Size Level:
   Will set the block-buffer-level. It will show the "buffer size" in bytes
just bellow it. High values will improve the compression but will require
more RAM when decompressing files. 3 is the default Blizz level while 7 is the
default "HeavyLock" level.

* WAVE COMPRESSION
   If the input file has any embbeded WAV and ZLIB is "off", this will control
their compression. Pretty much like the similar option on WINMPQ.

If you find any bug, contact me at the WC3 Campaigns "Tools" forum.
http://www.wc3campaigns.com

*****************************************************************************
* DEVELOPMENT EXTRA INFO:                                                   *
*****************************************************************************

The standard Blizz MPQ "buffer" size is 4096 bytes, "level-3" size.
The standard HeavyLock MPQ "buffer" size is 65536 bytes, "level-7" size.

Level 7 is a pretty good value, but higher values may improve the compression
a bit. Try a few values till you feel comfortable. I´m not 100% sure if setting
lvls higher than 7 will have a good effect with ZLIB, since its blocks only go
up to 65536 bytes. For an example, War3.mpq will actually INCREASE with some
levels.

If you're curious, here is a small table of the "compression" schemes used:
*.bik Are not compressed.
*.smk Are not compressed.
*.w3m Are not compressed.
*.w3x Are not compressed.
*.w3n Are not compressed.
*.wav Are compressed using STORM WAVE COMPRESSION if ZLIB is "off", otherwise
they also go using ZLIB.

Currently it´s better to add WAVES with ZLIB coz if I use the STORM WAVE COMPRESSION
with larger buffer sizes, the WAVES almost don´t get compressed at all. I still
don´t know why STORM WAVE COMPRESSION compress better with "small" buffers and
worse with "large" buffers.

Other files: ZLIB-Deflate-BEST if "Zlib" is "on", or STANDARD STORM if "off".
If files are too small (filesize < 10) they will not get compressed since this
is useless due the the compression overhead on the File-Blocks.

In the future:
- Optimize all the obfuscate code, on all levels to make them run faster.
- Improve the "PurgeConstants" , Level 3 obfuscate" to also purge Blizzard.j constants.
- Finish the "Merge globals declares/initialization" , "Level 4 obfuscate".
- Add a module to remove duplicates on WTS.
- Add scripting and last used settings feature.
- Fix some SLKs issues, if any.
- Fix some obfuscate script issues, if any.
- Improve code.

Version 0.2.8 (11/25/2003)
- User can now select the buffer size whenever protecting maps. This was done to prevent
maps with WAVEs getting bigger, as lordwiggin related.
- Probably I finally fixed the bug with comments, the "/" bug related by PitzerMike.
- Small changes to the randomization stuff used within the obfuscate.


Version 0.2.7 (10/10/2003)
- Added a "LastFiles" feature. Now the last 5 opened files will stay on the file menu.
- Added a Doodad optmization module. If the map is using the new doodad file format (TFT) then
HL can save it as the old format (ROC), saving a few bytes.
- Added a ERROR message whenever HL can´t find any files inside MPQ.(Unable to create tasklist).
- User can now select the TABLE size or set it to auto-detect. When using auto-detect, HL
will try to minimize the TABLE size. Note that if the user selects a small table size value
that does not offer enough room space for the inner files, the auto-detect mode will be used instead.

Version 0.2.6 (09/11/2003)
- Fixed a bug that was sometimes increasing the BlockLevel when using the autodetect feature.
- Fixed a bug that was causing maps with the "Preview only" mode to be unopenable with WE.
- Added and option to control wich filter shall be used with the file dialogs.
- Fixed some issues with the Level 1 = "variables" obfuscate. Note that it is not optmized yet,
so it will take little more time than usual.
- Added a Level 3 obfuscate, "PurgeConstants". For now it will do a Level 2 obfuscate plus it
will search inside the map script for some constants found on common.j and then replace'em all
with their proper value. Note that Blizzard.j constants are not working yet.

Version 0.2.5 (09/05/2003)
- Some GUI changes.
- Fixed a bug with "Clean TXT/J/AI" that was introduced on 0.2.3
- W3C (Camera File) , W3S (Sounds File) and Unis.DOO are now removed if locking the map.
- Fixed some obfuscate script bugs and changed the way it works. Obfuscate script is now
only enabled with the "Full Lock" mode. Then you will be able to select wich obfuscate level
ou want to use with the map. This change will make things easier to me when I add scripting
to the Heavy Locker in the future. Check the options bellow:
* Level 0 = "No obfuscate" will not obfuscate the script at all.
* Level 1 = "variables" will only obfuscate the global variables.
* Level 2 = "Functions" will do a "Level 1" obfuscate plus it will obfuscate some functions.
If the selected ofuscate level makes your map unplayable, try to reduce it.

Version 0.2.4 (09/04/2003)
- Added an "Auto-Detect" option to auto-detect the required Buffer lvl.
- Finished the "Minimap Quality" module. Whenever a loaded W3 map HAS a embbeded
minimap AND "Optmize Minimap" is ON, the "Minimap Quality" module will let you
choose a new minimap quality (%) to save the output map with. Ijl15.dll is required.

Version 0.2.3 (09/02/2003)
- Fixed a bug that was causing some comments to be ignored.
- Fixed a bug that was reseting the buffer size while cheking "Force ZLIB-Deflate".
- Improved "Clean TXT/J/AI" a bit. "Line Feed" is now removed.
- Obfuscate Script can now be unchecked while using the LOCK Feature.
- Increased the Max Buffer Level allowed to 15. Note that lvl 15 is about 16 MB, so
it may increase the map loading time a bit. Stay with lvl 11, use 15 for MPQs only.
- Started to work on a MINIMAP quality module. Not finished yet.
- Started to work with the globals declares/initialization (dataangel´s idea).It is
not working yet.

Version 0.2.2 (07/23/2003)
- Fixed a major bug that was causing "Obfuscate Script" to corrupt maps. It may
still have bugs, but now it should work most of the times.
- Include (listfile) is not locked anymore while using Map Optmizations, you
can set it. Note that while using the LOCK feature this is still disabled.
- Fixed a small bug that would cause "Keep table size" to fail in some cases.
- Improved the script obfuscate a bit.

Version 0.2.1 (07/19/2003)
- Fixed a bug that was preventing maps with Full-Lock to get properly locked.
- Improved the script obfuscate a bit.
- Fixed a small bug with the checkboxes.

Version 0.2.0 (07/15/2003)
- Improved the AI/J/TXT optmization a bit.
- Added an option to Obfuscate the script.

Version 0.1.9 (07/14/2003)
- Improved the code a bit.
- Small GUI changes.
- External listfiles can now be used. Note that if the source does not have
an internal listfile and no external listfile is given, we´ll get an error.
- Non-english LCIDs internal files are supported now.
- Added an option to only add the english internal files.
- Enabled more buffer-levels (0-2) if ZLIB is off. This was done as a workaround
to minimize the WAVE-COMPRESSION "weird-bug?" with high buffer-levels.
- I guess the (attributes) generation is finished. Note that by using 
"include attributes" the average LOCK speed will be slower since I need to do
some CRC checks. This will not affect the map loading time tough.
- Added a small check to the main compression routine to avoid negative
compression rates. If a file turns to get a negative compression rate,
we will add it back with no compression.

Version 0.1.8 (07/03/2003)
- More GUI changes. Moved the "INFO" to an about box.
- Added an option to control if any embbeded "war3map.imp" will be added or not.
- Small improvements with WAVE compression. (only if ZLIB is off).
- Enabled the Options menu. Currently you can select the starting path by
browsing or auto-select the WAR3 path. External listfiles is not completed yet.

Version 0.1.7 (06/30/2003)
- Small GUI changes (WAVE compression settings now is only visible if ZLIB is off).
- Started to create menus. Options is disabled for now.
- Created another option to control if (attributes) will be added.
- Fixed anoter problem related to TXT/AI/J optmization.
- Added Frozen Throne W3N to the "Open/Save as" dialogs.
- Frozen Throne W3N files inside MPQs now go uncompressed.

Version 0.1.6 (06/19/2003)
- Fixed a small problem with TXT/AI/J optmization.

Version 0.1.5 (06/06/2003)
- Fixed a problem that was causing W3 maps to get corrupt.
- Fixed another problem that was causing some WE defined "cameras" to get ignored.
- Removed COMMON DIALOG. Now this program only requires the Visual Basic 6
runtime (MSVBVM60.dll) and the ShadowFlare MPQ API (SFMpq.dll).

Version 0.1.4 (06/02/2003)
- Now if ZLIB is "ON" WAVEs also go compressed using ZLIB, otherwise they go
using STANDARD WAVE compression.
- W3M and W3X inside MPQs now always go uncompressed.
- Allowed the user to select wich MAP OPTMIZATIONS will be used.
- Allowed the use the select if the new MPQ will keep the original table-size.
- Cleaned up the code a lot and fixed some small things.

Version 0.1.3 (05/28/2003)
- Fixed a small bug that was showing wrong compression percentages.
- Added a small check to prevent the user from saving the new file with the
same name as the source file.
- MPQ "tails" are now supported.
- Added "SLK Optimization". It will be activated if "Map Optmizations" is on.
Note that the "SLK Optimization" is not fully tested yet, so the optmized
map may not work. If your embbeded SLKs seem to be not working at all,
please report the bug to me.

Version 0.1.2 (05/27/2003)
- Fixed a bug that was causing optmized stuff to get bigger. Please make sure
that the SFMPQ Version is "1.0.7.3".
- Fixed a bug that was causing the MPQ handles to stay open.
- Fixed a bug that was causing Map Optimizations not to work even when user
checked "Use map optmizations".
- Small improvements on some dialogs.
- Fixed a bug that was causing optmized minimap BLPs to get corrupted.
- Added a button to "Cancel" the operation.
- Lock protection now has 2 modes: "Preview only" and "Full Lock".
"Full lock" completely locks the map while on the "Preview Only" mode, the
map will still be openable by the WE, but the triggers will not show up.

Version: 0.1.1 (05/24/2003) (Intenal only)
- Fixed a small bug while dealing with non-stardard listfiles (SC Maps).
- Added an option to set the buffer level.
- Small improvement on the COMMONNDIALOG "Open" Filter.
- Started to work on a special procedure to handle "unknowns" but this turned
to be almost impossible. It will not handle files that are not listed on the
internal "(listfile)" of the source.

Version: 0.1.0 (05/23/2003)
- ** Complete Rewrite of the code. **
- Using SFMpqApi now, MPQx.dll is not needed anymore.
- Supports MPQs with compressions <> ZLIB, so now it works with older games.
- Speed enhancements and bug fixes.
- Removed "Special" optimizations from the "general" procedure. Now they
only get activated if the user says so on the option box. This was done to
keep MPQs as much as the same as the input file.
- Special handling of MPQs made possible to properly work with "embbeded"
stuff on the file. If you are opening a EXE or a W3M for an example, the
"header" above the MPQ will also go to the new file. Note that file "tails"
are still not supported.
- Removed the FDF Optimization, since I'm not sure if this would work nice.

Version: 0.0.3 (05/11/2003)
- Lot of bug Fixes
- Added AI and FDF Optimization
- Some speed enhancements

Version: 0.0.2 (05/10/2003)
- zlib.dll is not required anymore.
- Changed from SfmpqAPI to Storm
- Fixed some bugs
- Added BLP (Minimap) Optimization
- Added TXT (Profile) Optimization

Version: 0.0.1 (05/09/2003)
- Initial testing