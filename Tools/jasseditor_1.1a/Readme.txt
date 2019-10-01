---------------------------------------
      Jass Editor 1.0 by KaTTaNa
---------------------------------------

== README ==

Contents:
1 Changing syntax colors and keywords
2 Changing Functions and Constants list
3 What is the Merge Files feature?
4 Templates
5 Suggestions and Contact info



---------------------------------------
1. Changing syntax colors and keywords
---------------------------------------
Open Syn.txt. In that file you can read the syntax for making your own syntax words.
In JassConfig.txt you can edit what files are used as Syntax Files.
For example if you made a new syntax file called MySyntax.txt you would add it to JassConfig.txt like this:

  [Syntax]
  Syn.txt
  MySyntax.txt

Just be sure to keep the rest of the file intact. 
If JassConfig.txt gets messed up, you can always delete it and the editor automatically restores the original one.
However, it doesn't restore files like Const.txt, Syn.txt and Func.txt


-----------------------------------------
2. Changing functions and constants list
-----------------------------------------
Look in Const.txt and Func.txt.
Func.txt contains the declarations of all the functions, where const contains all the constants.
Be sure to add THE WHOLE DECLARATION, if you decide to add some of your own.
I recommend that you keep your own declarations out of Const.txt and Func.txt.
To make the editor use your own list, edit JassConfig.txt


-----------------------------------------
3. What is this Merge Files feature?
-----------------------------------------
It merges two or more Jass code files into one. The topmost files in the list, have higher priority than the
lower ones. If two or more files have different declarations with the same identifier (eg. variable name), the one from
the file with the highest priority will be used.
This feature might contain bugs at the moment, so you might want to check the output file before using it.


-----------------------------------------
4. Templates
-----------------------------------------
The templates can be accessed through the menu, or by clicking the shortcut for it.
Currently there is no support for custom templates. If you want one added, ask me and I might add it
in the next version.


-----------------------------------------
4. Suggestions and Contact info
-----------------------------------------
Suggestions and comments are very welcome.

You can contact me in either of the following ways:

MSN / Windows Messenger: asger@feldthaus.dk   (Don't send E-Mails! Only for Messenger use)

Send me a PM on either:
  http://www.wc3modforge.com
  http://www.wc3campaigns.com

Add a reply to the thread regarding the editor on either of the above sites.












