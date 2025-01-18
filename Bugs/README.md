## Notes

# Bugs

## GM 2.3 is quite unstable
If the data.win/game.unx is GM2.3, it is less likely to work without patching!

## Missing sound with .ogg files 

Currently, some GameMaker ports with .ogg files (which are use for sound and background music)

**Fix:**
Create a /assets folder with a .gitkeep in the root of your game directory

Add in the following lines into the .sh Script:

	# Check for .ogg files and move to APK
    	if [ -n "$(ls ./gamedata/*.ogg 2>/dev/null)" ]; then
        mkdir -p ./assets
        mv ./gamedata/*.ogg ./assets/
        echo "Moved .ogg files to ./assets/"

        zip -r -0 ./game.apk ./assets/
        echo "Zipped contents to ./game.apk"

        rm -rf ./assets
        echo "Deleted assets directory"
    else
        echo "No .ogg files found"
    fi

## Game has both mouse and keyboard input and controller inputs concurrently active

If you use GMLoader-next then you can either disable GPTOKEYB. That is easy because you just need to remove the -c "gamename.gptk" in the GPTOKEYB Line

#OR

You deactivate Controller Support. That is done in the gmloader.json. There we will set "disable_controller" : false into  "disable_controller" : true



