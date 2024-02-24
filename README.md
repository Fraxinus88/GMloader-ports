## Notes

**GameMaker Games**

GameMaker games usually have a data.win OR game.unx file which contains the main data to make the games work. As the games are not meant to run natively on ARM devices supported by portmaster, it uses gmloader together with an appropriate wrapper (.apk file) to help translate the data into information which can be read by arm devices. Based on the current limitations of gmloader, games which uses the YoYo Compiler (i.e game data is stored directly on the .exe of the game file) are currently not portable. 

**Note:** the following instructions assumes you already have Portmaster installed on your device. 
It is also a lot more convenient to SSH your files via WIFI to your device rather than physically transferring the data via an SD card reader.

**How to port GameMaker games to Portmaster**
1. Download the test.zip from https://github.com/Fraxinus88/GMloader-ports/blob/main/Test/Test.zip
2. Download Undertale Mod Tool  from https://github.com/UnderminersTeam/UndertaleModTool
3. Legally obtain your GameMaker game files or the many wonderful free ones available from websites such as https://itch.io/
4. Locate the data.win or game.unx file inside the game files and open it using the Undertale Mod Tool and determine the GameMaker version to see which wrapper (.apk) can help to translate the game information appropriately.
5. You can find the game version at the top of the window or under Data -> General Information -> Version
![Pingo Game Version.png](https://github.com/Fraxinus88/GMloader-ports/blob/main/Pingo%20Game%20Version.PNG)
6. Copy the appropriate wrapper version from https://github.com/Fraxinus88/GMloader-ports/tree/main/gmloader%20wrappers%20(APK)
7. Delete test.apk and rename the wrapper (e.g  rename GMS 2.2.2.302.apk to test.apk)
8. Place all your game files (data.win, audiogroup.dat, .ogg file) and folders under /test/gamedata
9. Place Test.sh and /test folder into your ports folder on your device (e.g roms2/ports).
10. Run Test under your ports menu to see if your game works.

**If your game works... then it is time to edit your filenames and troubleshoot!**


