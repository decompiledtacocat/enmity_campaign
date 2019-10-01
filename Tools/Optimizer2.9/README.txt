****************************************
*                                      *
*  Wc3 Text File Optimizer 2.9         *
*                                      *
****************************************

 The usual 3rd party program warning:
 ¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯
  THIS PROGRAM IS DISTRIBUTED "AS IS".  NO WARRANTY OF ANY KIND IS EXPRESSED
  OR IMPLIED. YOU USE AT YOUR OWN RISK. THE AUTHOR WILL NOT BE LIABLE FOR 
  DATA LOSS, DAMAGES, LOSS OF PROFITS OR ANY OTHER KIND OF LOSS WHILE USING
  OR MISSUSING THIS SOFTWARE.

 What it does?
 ¯¯¯¯¯¯¯¯¯¯¯¯¯
   Is able to optimize the strings file, the map script and/or the map mpq itself to save space. Includes plenty of Script Obfuscation methods that can be really useful to save space, improve execution and may work as an effective anti unprotector method.

   Note that this program wasn't really designed for map protection, it has the option to remove the files used only by the world editor, but that's only to save space, it is not the author's fault that world editor isn't able to open maps that warcraft iii can without problems, in case you don't want to "protect" the map, don't use the Remove Useless files option or use the "Allow map preview" option.

   It is true that the script obfuscation options included in this program, proved to be really effective against wtg reconstructors, but that isn't their main objective, their objective is to improve performance and save space, It is not the author's fault if map unprotectors are unable to beat them. Anyone with a basic and kind of cheap programming knowledge and plenty of time to waste, may be able to make a program that "unprotect" maps with the obfuscation methods included, though that program doesn't exist at this moment.

 How to use it?
 ¯¯¯¯¯¯¯¯¯¯¯¯¯¯
   Open the exe file, then click the Open File... button and find your map, then use Save Optimized as... to save the optimized version of the map, before doing that you can choose what extra obfuscation methods you'd like.

   For Security reasons, it is impossible to save it as the same file you gave the program, this is to ensure you have a backup of the file you optimized.

 Map Optimization Options:
 ¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯
   * Strong Zlib Deflate Compression, will recompress the files listed in the mpq using the ZLIB deflate compression, should save some Kbytes.

 NOTE: If your map is already small, this option may cause the size reduction to be lower than when not using this option.

   * Buffer Size: Will REBUILD the entire map mpq using a new buffer size, the biggest the buffer size is the more ram the game will require to decompress it and the least space the map will need, Blizzard's favorite buffer size is 4096 bytes, and the recomended one is 65536 bytes, bigger buffer sizes may work, though they might be risky but they are worth a shot none the less. At this moment I would say that the Auto detect option is the best for you, unless you want to test other values by yourself.

   NOTE: if you choose this option, the new Map file will MISS any archive that wasn't listed in the listfile.

   NOTE 2: I found that small maps may actually GROW in size with this option.

   * Look for other scripts to obfuscate: Will check all of the files listed in the listfile that have the .j or .ai extensions, then will remove comments and useless spaces from them, This is useful when you have a custom blizzard.j or an ai script in your map.

   * Remove Useless Files : Some people call this map protection, will remove all the files that are only needed by the world editor excepting war3mapunits.doo to save space, war3mapunits.doo is not deleted because if that file is missing the map will be unopenable by the world editor.

   * Also Remove Unit Data : Will Remove war3mapunits.doo (the file that includes the positions and options of the units in the map for world editor) , leaving the map unopeneable by world editor, and saving space, if 'allow map preview' is enabled, it will create a fake war3mapunits.doo and replace the one in your map with it.

   * Optimize String usage : This will move the strings from the WTS file into the files that use them, If you have a map with long loading time and lots of abilities / units / items and-or upgrades , this option will improve loading time a lot.

       * Remove editor suffixes : The playable version of your map doesn't really need the editor suffixes anyways, use this option to remove the editor suffixes from the object files and save some kilobytes. 

   * Clean SLKs (beta): This was initially meant to save some map space, but the compression is so good that it would only save some bytes even if the SLKs' size is halved. If your map uses SLKS, (for example you widgetized it) this option will clean the slks removing the values that don't really have to be in the slks (zeros, "-", Editor Only stuff) This seems to decrease loading time even more.

   * Allow Map Preview : Will Replace the map's trigger data with a custom one that just has a comment with the info you write in the text boxes, this will allow you to include contact information, the url of the open source version / downloadable files that include your stuff, or whatever you want a guy that opens the world editor read. If "Also Remove Unit Data" is enabled, this will also create a fake war3mapunits.doo to leave the map openeable.

    If you are the kind of person that updates its map very often, you can use the [...] button that should be found in bottom right of the textbox to load the comment contents from a text file. (The first 2 lines of the text file would go to category and name.

   If Category or Name are blank, this will remove the wtg and wct files instead of making a new one, this is because otherwise it would corrupt the file.

 Extra Obfuscating Methods
 ¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯
   * Remove Useless code: The way world editor converts the GUI "triggers" into JASS is kind of bad, and would leave some unnecessary code like else statements just before an endif , or ==true which is completelly worthless or calling the DoNothing function which does nothing, this will just remove that stuff from the script.

    It will also remove most of these constant functions used for configuration on JASS spells like the ones I make, and replace the places where they are used with their values. This will work for every takes nothing returns XXXXX constant function.

    Also shortenes code like the ones used a lot by GUI like, creating a special effect in a line then setting a variable to last created effect, this will replace both lines with a line that sets the variable to the call of the function.

   * Anti BJ : Will replace most of Blizzard.j functions and constants with native / number counterparts, this process has various intentions:
       - It improves map speed, cause the triggers will use less calling times because of the replacement of the functions / constants (don't expect a huge improvement though)
       - It saves up some space (not too much, but always helps).

    NOTE: You shouldn't use this if you are using a custom blizzard.j file or you are going to obfuscate a custom blizzard.j file.

   * Merge Initialization functions: Will merge all the functions called by main and config:
       - The functions that get mixed are the global initializations, the sound creation, the rect creation, the unit creation and the trigger setup.
       - It saves some space and loading time (not too much, but always helps)

      NOTE: This function is completelly designed for maps.

    It will even work with functions that have local declarations, excepting some few cases , where two of the functions have 2 local variables with the same name but with different type (it will still work in case both have the same name and same type).

   * Merge Global declarations with initializations: When world editor saves the map, it declares the global variables in a place, and makes a separated function to initialize them (giving them initial values), but in JASS it is possible to initialize non-arrays at the moment of declaring the variable, this obfuscation will move the initializations of non-array global variables, rects and cameras to the globals section, would save some map space.

   * Merge Array Initializations: World Edit makes it so arrays are initialized with some loops, one loop per array, but it is normal that most of the arrays in a map will have the same starting index, this will put all the arrays that use the same starting index into the same loop, saving some worthless space and little loading time.

   * Conditions: World Editor Loves to create a lot of code for trigger conditions, it makes the script easier to read, but in game they are completelly worthless, this method will reconfigure the map's conditions to use the least space possible.

   * Order Strings To Ids : Warcraft III has 2 ways of using orders, orderstrings and orderids , basically orderstrings are the ones you use often to issue or detect orders (ie: "frostnova" ) but orderids are integer values that represent each order directly. When you use an order string, warcraft iii checks an internal table looking for the orderid that is represented by the order string, losing some execution time. This method will just replace every direct usage of Orderstrings with usage of the OrderIds they represent, this shall save some space and improve efficiency.

 * The "Shortest variable / function names possible" method
 ¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯
     What this option does is to replace the function and variable names in the map with the shortest possible values, this was an objective since the day Grater found out that the length of names in JASS has an influence in map speed, also it reduces some important kilobytes depending on the size of your map script, and as a secondary effect makes the map's more difficult to understand or change.

     Extprotect and Heavylocker had an option like this, but this program's version also takes care of strings, many JASS systems like my caster system, my templates system, InVx, AIAndy's classes system, and a lot more, use ExecuteFunc , a function that takes a function's name (in string format) as argument to execute it in another thread, When you use Extprotect or heavylocker on a map with any of those systems the map would crash, that doesn't happen with this one.

     As a bonus, it will try to remove unused global variables and functions, it would only remove functions if they take arguments though, this to prevent issues with ExecuteFunc, you can check certain option to make it clean every unused function, but I don't recomend to do that.

     This method needs to first parse common.j and blizzard.j before doing anything, if you are willing to use this program to obfuscate your custom blizzard.j , just gave it an empty file for blizzard.j.

 To determine which common.j and blizzard.j files to use you have two choices:
  - Use warcraft's folder war3patch.mpq : will extract them from war3patch.mpq when needed.
  - Determine the location of the j files directly.

 Most likelly if you don't know which option to use there, you should use the war3patch.mpq one.

 So before using this method, you have to choose the location of those files, if everything goes allright, the program will automatically ask you for them when you activate the option, in case it doesn't, or you already gave the program the locations and wish to change them, you should click that "common.j / blizzard.j location ..." button.

 notes:
 ¯¯¯¯¯¯
 - This method also removes the declaration of unused global variables.

 - FOR JASS USERS ONLY: The program will change the contents of ANY STRING that has as content the exact name (case sensitive) of a declared real global variable or a function that takes nothing . So there is a RARE chance to have issues with:
   - Order strings
   - Text messages/ multiboard values / leaderboard values / dialogs text, or whatever that appears in the screen of the map.

   Because of this you should give the map a complete test after using this program, and look for weird issues, a weird text message or something bugged with order triggers may happen.

   In order to avoid this issue, you can simply avoid giving function or real globals names that match the ones you use for messages or to match an order string.

 If you use gui, you shouldn't really have problem with this.

 - It won't change the name of a function that is not called anywhere in the map and takes no arguments, this is to prevent issues with ExecuteFunc being used with concatenating and that stuff, If the function isn't called by any function and it does take arguments, the function will be deleted.

 - Not guaranteed to work 100% right and it is still at beta stage, so please give your map an intensive test after using this method on it.

 Though I already tested it on my map which has a lot of variables and functions, and is also intensivelly based in ExecuteFunc systems. My map seemed to work perfectly.

 Extra options for the shortest names obfuscation method
 ¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯
 I seriously recomend to avoid using these options unless you are completelly sure you know what you are doing:

 * Make sure to clean every unused function/variable : The method already cleans unused globals and functions that have arguments, But let's say it deleted a function that was also the only function that called another function / used a global variable, the other function/variable should be deleted too, this option will make the optimizer repeat the process until there is no function/variable to clean.

 * Clean 'unused' functions: As default the program will just avoid changing the names of functions that are not called anywhere in the map and don't take arguments, to avoid probable crashes with ExecuteFunc based systems that use concatenations or other ways to call the functions. But if you are sure that you don't use any ExecuteFunc based system in your map, you can check this option so the method removes those functions and the map saves some space (this is only valid for functions that don't take arguments, unused functions that don't take arguments are always removed no matter this option is checked or not)

 * Ignore strings: If you have an issue with an order or with a text message and you DON'T use ExecuteFunc in
your map, you can check this option to prevent the problems.


 What to do if the optimized map doesn't work
 ¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯
In the weird cases the map doesn't work, I suggest these debugging steps:

 1) Try Optimizing the map without using any extra map script obfuscation. If the new map works, then the problem was caused by one of the obfuscation methods. In that case, Try with different combinations of obfuscation options, I recomend trying with all the obfuscation methods enabled excepting the last three which have the most chances of malfunctioning, the merge and anti bj methods are often enough. Now that we know it was caused by the obfuscation methods, I will really appreciate if you send me your map's map script file (I only need the map script).

 2) In case it doesn't work even without the extra obfuscation methods, try disabling all of the extra map optimization methods, in case the map works now report it to me, and If possible send me your map so I can debug this program.

 ** What to do if X trigger on the map doesn't work correctly in the optimized version, while it does in the original version?

   This is surelly caused by one of the obfuscation methods, in this case, I will really appreciate if you send me your map's script, and you tell me which is the trigger that malfunctions.


 What to do if the optimized map becomes BIGGER than original?
 ¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯
   Map size increasement, might be caused by various reasons:

 - Wav files in the map and Zlib or buffer size make the map bigger. To fix this get a mp3 encoder such as Lame and convert the wavs to mp3 (this unless the file has to be a wav file - likelly when replacing unit dialog sounds)

 - A bug in the obfuscation methods, I've never seen this, but in theory a bug in any of the obfuscation methods may cause the script to increase on size a lot, this is really unprobable though, just try the map without any extra obfuscation method, and see if the map's size is reducing now. In case you find it is caused by the obfuscation methods, please send Vexorian at wc3campaigns your map's script, I will really appreciate it,

 Widgetizer
 ¯¯¯¯¯¯¯¯¯¯
    Widgetizer is a tool by Pitzermike that basically converts the object data into slks and txts , this greatly improves loading time, but it also reduces the chances to get a better compression.

    When you use a map on widgetizer, it will actually reduce its size most of the times, but this is actually because widgetizer already uses the buffer size feature.

    Using the optimizer on a widgetized map, will reduce the map's size but not as much as it would reduce the size on a non widgetizer map, just take that in mind.

    Also the 'Optimize Strings' will have no effect on a widgetized map, since widgetizer converts them to slks, and it already inlines the strings. But Remove Editor Suffixes will work.

  Some tests
  ----------
     This information may help you decide what combination is better for you:

  Tested Map : Vexorian Hero Arena 0.507 (not released yet)

			Map Size 	Loading Time
  Original File		1227 KB		2 min 32.45 sec
  Map Optimizer		 655 KB		2 min 17.24 sec
  Widgetizer		1142 KB		1 min 13.68 sec
  Widgetizer+Optimizer   888 KB         1 min 11.25 sec

     Granted Widgetizer and Optimizer make a great synergy with a 339KB reduction and 81.2 less loading time seconds.

     One thing to note is the 233KB difference between the combined Widgetizer and Optimizer and the Optimizer alone, and the 1 minute 5 seconds difference in loading time. What is more important Map Size or loading time? If the map is for LAN or Single player, then you should just focus on loading time, but if the map is for bnet you should reconsider, since Bigger map size means bigger download time, certain map may grow bigger than others depending on their object data, so you have to double check if the extra size isn't causing a download time as big as the loading time saved.

     Optimizer seems to decrease loading time a little after widgetizer, but consider that the difference (2 seconds) is not meaningful and that it is in the Error range of the test. I used an external timer for that  and because of lack of time I only did one test per version of the map. It should have sense that Map optimizer decreases loading time though, because of the Script optimizations.

     The loading time of my map seems to be big after both optimizations, it is because those optimizations are based on object data (both the strings optimization from the Optimizer and what the Widgetizer does) , my map has thousands of lines at map initialization to declare values of spell templates, horadric cube recipes and other stuff.

 Error Messages:
 ¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯
 - I/O Exception, unable to open file, and similars, The file you want to replace is currently opened by another program, or your disk is damaged.

 - Too Much lines on file : Certain obfuscation methods have a limit of JASS lines in the file, the actual value is 30000 lines, I don't think a map script with more lines than 30000 will ever appear, but in case your map script has more than 30000 lines, tell me so I can increase the value (thus making the program use more memory)

 - Merge Error: Function to merge never ends! : the map script, either because of the original file or may be the obfuscation methods made before, doesn't have its correspondant endfunction, If you are using a map script this shouldn't happen, in that case I'll ask you to send me your map script (just the script not the map) , to see what is happening.

 - Other error messages: Please report them.

 Final Notes:
 ¯¯¯¯¯¯¯¯¯¯¯¯
 - You can associate map, and map script files with this program now, in case you want to associate string files with it too use the -wts argument before the %1

 - This is not a 'map protection' program, its objective is to decrease map downloading time and to improve the script's execution. Even though some of its obfuscation methods proved to beat automatic map unprotectors, the point of this program is to optimize the map, and if it leaves the map unopeneable by World Editor while the game can play it correctly, it is actually World Editor's fault, The Allow map preview option was added to prevent the map to be unopenable, and you are even able to put an url to the source there, but still delete the stuff that is only needed by the world editor.

 - The program comes with the source code, for learning purposes, you should use Delphi to open it, you may update the program as long as you share the source of the updated stuff to me, and don't forget my name on the credits of your new tool.

 Credits and special thanks
 ¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯
 Program Author: Vexorian (Víctor Hugo Solíz Kúncar)
 Uses the wonderful SFMPQ.DLL Library by ShadowFlare

 Special thanks to:
 - Pitzermike and StarcraftFreak for the huge help they gave me about mpq manipulation.
 - BlackDick for helping so much.
 - AIAndy for keeping updating pjass which helps testing and finding bugs with the obfuscation methods.
 - Zoar for telling me about the fact that blizzard uses UTF8
 - PantoCrator, eScpy, Tyler Blank, ArcanisteR, Karukef,Archael : for helping to find and fix bugs with obfuscation methods.
 - BlackDick (again), DJBnJack, PitzerMike (again), StonedStoopid, Ziutek and most specially Zepir for the War3 file specifications document.

 The Ultimate Packer for eXecutables :
          Copyright (c) 1996-2002 Markus Oberhumer & Laszlo Molnar
                       http://upx.sourceforge.net
 In the future :
 ¯¯¯¯¯¯¯¯¯¯¯¯¯¯
   - More Obfuscation methods will keep getting released.
   - Make Anti BJ also replace the functions that just swap the arguments' positions for functions that have 3 arguments, and for function return values.
   - Finally fix the issues with maps that have wav files by making a wav optimization feature.
   - Options for campaign file optimizing will be added.

 Version History
 ¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯
 2.9 :
 - Fixed a bug with the script loader and AntiBJ combined that sometimes stopped the map from working.
 - Fixed a bug with AntiBJ actually stopping the Set Unit Ability level function for GUI from working at all.
 - String Optimizing / Remove editor suffixes should work for object strings files too.
 - New Script optimizing method: Option to make sure to clean every unused function/variable.
 - New Map optimizing option: SLK cleaning.
 - Fixed some typos in this file.

 2.8 :
 - Works on Widgetized maps without halting now.
 - Fixed bugs with scripts that had \\ at the end of strings.
 - Conditions obfuscation method is faster.
 - No longer loads the map script again when using the 'shortest' obfuscation method
 - Fixed a bug that was reducing compression ratio a lot and was kind of lame, the script file was getting duplicated? , and even worse the duplicated was the unobfuscated version.

 2.7 :
 - Fixed major bugs with maps that had scripts that used /" inside strings.
 - Fixed a bug with shortest variable/function names possible combined with conditions obfuscation
 - Will now consider the strings used on war3map.wtg and war3map.wct in case protection and map preview are unchecked.

 2.6 :
 - New map optimization option that allows to move the strings from the wts file into the files that use them, this is effective for reducing loading time and also allows you to remove the editor suffixes to save some extra kilobytes.
 - Rebuildin the map with new buffer size or making Zlib compression should be much faster now.
 - Simple string file optimization is much faster.
 - Fixed a bug when copying the map, was copying the map twice, so it halved the time used for that.

 2.5 :
 - New important obfuscation method that replaces the names of variables/ functions in the map with really small names, this makes the map smaller and much faster.
 - Fixed a small bug, maps would generally lose some extra bytes now.

 2.4 :
 - AntiBJ and remove useless code now optimize patch 1.18 stuff.
 - Compatibility with other languages, again.
 - Now uses the right places to save options and temporal files (Would fix problems with user restrictions and that stuff in some windows versions)

 2.3 :
 - Fixed a horrible bug that would cause total corruption when you had a comment with a " inside in your map.
 - Fixed a with codifications that inserted '?' signs at the start of the maps.
 - Fixed a bug with 'AntiBJ' not working in certain situations
 - Fixed a bug with 'Merge array initializations' not working in certain situations

 - It will tell you how much bytes it saved besides of the percentage now.

 2.2 :
 - Fixed a horrible bug that happened when a string finished with a carriage return in the JASS script, making the program to 'eat' some of the remaining code.
 - There was a chance of odd I/O errors on certain maps, that was fixed.
 - Fixed a bug with the merge array initializations method.
 - Hopefully now works 100% allright with maps that use 'Foreign' characters. The only way to test this I had was the Ñ I had from spanish, but it should work with the other languages.

 - Added AUTODETECT to the buffer size level option, and fixed a bug with it, (it wasn't actually using the values you wanted).
 - Merged the Constant function purge method with the remove useless code method.
 - The Remove Useless code method will also merge variable sets with function calls.
 - AntiBJ now deals with calls to BJ swapped functions.
 - The merge array initializations method is now incredibly fast, so fast that in most of the cases you don't even note the moment it is called.

 2.1 :
 - Fixed an evil bug with the purge constant functions method that was making any map unplayable
 - Fixed an evil bug, yet not that important that was happening with Big script files.

 2.0 :
 - My logic was flawed, again, figured that a function that has a return statement shouldn't be merged, fixed that now.
 - Another Flawed logic issue, it can't just add a -1 to the arguments because it would screw becase * has priority in the evaluation order, if you were having problems in certain triggers and you love using Convert Player to index and the convert index to player, then the cause of that issue was fixed.
 - Fixed another bug with AntiBJ, there was a slight chance that it wouldn't change certain functions.
 - Fixed another problem, the merge array initializations method wasn't actually working if the merge functions option was enabled, now its fixed.

 - Added the Purge constant functions method.

 1.9 :
 - My logic was flawed, I found a big problem with the way I was merging functions with locals, now the initial value of the local variable would be set in the right place (putting it in the declaration would cause problems in certain situations)
 - Fixed a rather small frozen time before starting the global merge method.
 - The merge initialization functions method got a major speed boost.
 - Other methods excepting the Merge Array Initializations and the conditions obfuscation were improved speed wise too.

 1.8 :
 - Fixed a bug that was causing the merge Initialization functions option to make the map unplayable under certain circunstances.
 - Fixed various bugs in the merge Initialization functions options when strings had carriage returns.
 - The "merge global initializations with declarations" options got a major speed boost, used to be the slowest method and now is the fastest, similar improvements will be done with the other methods.
 - Fixed some stuff in the readme file (this file)

 1.7 :
 - The function merge methods now are able to merge functions that use local variables, excepting some weird cases.
 - The function merging methods were all merged into one option, this is because they all use the same function afterall, so if one is bugged all the other ones will too, and it will save you 2 clicking times.
 - More functions are merged, at this time it will end with a gigantic main function that contains everything from global initializations to triggers, including unit creation.
 - Maps that use the Remove weather effect action, can now use Anti BJ without problems, in other words I fixed the bug with Anti BJ.

 1.6 :
 - Fixed a bug with the conditions obfuscation method, thanks Karukef for the feedback that helped finding it.
 - Fixed problems with "foreign" characters , thanks a lot to Zoar for this.
 - Reorganized the form so the status label has more space to show information.
 - Hopefully no longer leaves any temp file.

 1.5 :
 - Now you can open map files directly, and the program will automatically fix the strings and obfuscate the script of the map.
 - Also added some map optimization options like changing the buffer size, forcing zlib deflate, and removing useless files, you can get really incredibly file size compression now.
 - The Interface was changed somehow now that it can open maps too.
 - Now the program is called wc3 map optimizer.
 - Script and Wts file fixing without changing the map are still possible when you open that kind of files.
 - Global initialization merge was fixed due to a lot of glitches that certain types cause, even if the map compiled well, now it would only merge certain types or any variable that is initialized with null.
 - Global initialization merge also works with sounds now.
 - Updated AntiBJ, does its work with more functions, and the new BJ dummies that came with 1.17
 - Added The Conditions Obfuscation Method.
 - You can now associate script files or maps with this program.
 - Temporal files are now created on the same directory of this program.

 1.1 :
 - Added the "Merge Global Declarations with initializations" obfuscation method.
 - Added the "Merge Array Initializations" obfuscation method.
 - Added the "Remove useless code" optimization method.

 - Added a check/uncheck all check box, since the options are already too many.

 0.9 :
 - JASS script obfuscating no longer ignores tabs.
 - Added 3 new obfuscation methods based in merging the initialization functions into a giant one.
 - Array brackets are now considered operators as they are supposed to be, so the problem with stuff inside array brackets not being fixed is solved.
 - Fixed a bug in the Anti BJ, was causing it to fix strings instead of non strings after certain circunstances.
 - Anti BJ no longer leaves a temp file.
 - Anti BJ now also replaces the GUI get player number with the native one +1 (so it takes less space)
 - String File Fixer now makes sure it is not removing lines inside the strings.

 - The program now tells you how much the file size was reduced.
 - Added a progress bar, new obfuscating methods were too time consuming for me.

 0.3 :
 - Added the Anti BJ obfuscation method, still at beta stage so it can ruin your map, my tests of the method didn't show problems though.

 0.2 :
 - I recently discovered that strings might have a weird behaviur in JASS syntax, and this program wasn't aware of that either, just fixed it, so there aren't bugs with strings that have carriage returns inside.          

 0.1 :  (first version)