## Notes

### **GameMaker Games**

GameMaker games usually have a data.win OR game.unx file which contains the main data to make the games work. As the games are not meant to run natively on ARM devices supported by portmaster, it uses gmloader together with an appropriate wrapper (.apk file) to help translate the data into information which can be read by arm devices. Based on the current limitations of gmloader, games which uses the YoYo Compiler (i.e game data is stored directly on the .exe of the game file) are currently not portable. 

**Note:** the following instructions assumes you already have Portmaster installed on your device. 
It is also a lot more convenient to SSH your files via WIFI to your device rather than physically transferring the data via an SD card reader.

### **How to port GameMaker games to Portmaster**
1. Download the test.zip from https://github.com/Fraxinus88/GMloader-ports/blob/main/Test/Test.zip
2. Download Undertale Mod Tool  from https://github.com/UnderminersTeam/UndertaleModTool
3. Legally obtain your GameMaker game files from Steam or GOG or Itch.io OR try the many wonderful free ones available from websites such as https://itch.io/
4. Locate the data.win or game.unx file inside the game files and open it using the Undertale Mod Tool and determine the GameMaker version to see which wrapper (.apk) can help to translate the game information appropriately.
5. You can find the game version at the top of the window or under Data -> General Information -> Version
![Pingo Game Version.png](https://github.com/Fraxinus88/GMloader-ports/blob/main/Pingo%20Game%20Version.PNG)
6. Copy the appropriate wrapper version from https://github.com/Fraxinus88/GMloader-ports/blob/main/images/Pingo%20Game%20Version.PNG)
7. Delete test.apk and rename the wrapper (e.g  rename GMS 2.2.2.302.apk to test.apk)
8. Place all your game files (data.win, audiogroup.dat, .ogg file) and folders under /test/gamedata
9. Place Test.sh and /test folder into your ports folder on your device (e.g roms2/ports).
10. Run Test under your ports menu to see if your game works.

**If your game works... then it is time to edit your filenames and troubleshoot!**

#### **First Step: Renaming your folder name, file names and .sh name**
Script Name: Test.sh -> Game Name.sh
Game folder name: /test -> /gamename
Under your gamefolder you need to rename the following 2 files:
test.apk ->gamename.apk
test.gptk -> gamename.gptk

Note: The script should have capital letters (like Port Name.sh ) and must end in .sh , the port directory (Game folder name) should be the same as the containing directory. Usually it is combined into a single word with no space and all in lowercase.

#### **Second Step: Editing the .sh file**
![Testsh.png](https://github.com/Fraxinus88/GMloader-ports/blob/main/images/Testsh.png)
Replace the highlighted parts above with your Game Name and renamed folders and files. The .zip usually has the same name as your game folder name.
The above lines will be replaced as such:

"# PORTMASTER: test.zip, Test.sh -> # PORTMASTER: gamename.zip, Game Name.sh"

"GAMEDIR="/$directory/ports/test" -> GAMEDIR="/$directory/ports/gamename"

"$GPTOKEYB "gmloader" -c ./test.gptk & -> $GPTOKEYB "gmloader" -c ./gamename.gptk &"

"./gmloader test.apk -> ./gmloader test.apk"

#### **Third Step: Editing the gamename.gptk file**
Kindly refer to https://portmaster.games/gptokeyb-documentation.html

First and foremost, if the GameMaker game has in-built gamepad controls, you may edit all the lines as the following:

![testaptk.png](https://github.com/Fraxinus88/GMloader-ports/blob/main/images/testgptk.png)

The "\"" basically means that the input from the .gptk file is empty and hence controls will mainly be gotten from the in-build SDL2 controls available on your handheld.

If your game solely utilizes mouse and keyboard controls, then use the above [link](https://portmaster.games/gptokeyb-documentation.html) to remap the controls appropriately (i.e play the game on your computer first to see the controls in the menu and in-game to decide how to rebind the controls)

#### **Forth Step: Test and Troubleshoot**
Join the Portmaster discord server and put a new post under #testing-n-dev and the Portmaster discord community will help you with your port.

There are many games which requires patches or extra coding to help the game run optimally (i.e prevent slowdowns, fix missing sounds)


