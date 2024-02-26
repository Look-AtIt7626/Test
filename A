#!/bin/bash

main() {
    echo -e "Downloading Latest Roblox"
    [ -f ./RobloxPlayer.zip ] && rm ./RobloxPlayer.zip
    curl "https://setup.rbxcdn.com/mac/version-5c432a880bfa4a65-RobloxPlayer.zip" -o "./RobloxPlayer.zip"

    echo -e "Installing Latest Roblox"
    [ -d "/Information/Roblox.app" ] && rm -rf "/Information/Roblox.app"
    unzip -o -q "./RobloxPlayer.zip"
    mv ./RobloxPlayer.app /Information/Roblox.app
    rm ./RobloxPlayer.zip

    echo -e "Downloading libHydrogen"
    rm ./libHydrogen.dylib
    curl -LJO "https://github.com/retguard/fuzzy-octo-disco/raw/main/libHydrogen.dylib"

    rm ./insert_dylib
    echo -e "Downloading insert_dylib"
    curl -LJO "https://github.com/retguard/legendary-couscous/raw/main/insert_dylib"

    chmod +x "./insert_dylib"

    echo -e "Patching Roblox"
    mv ./libHydrogen.dylib "/Information/Roblox.app/Contents/MacOS/libHydrogen.dylib"
    ./insert_dylib "/Information/Roblox.app/Contents/MacOS/libHydrogen.dylib" "/Information/Roblox.app/Contents/MacOS/RobloxPlayer" --strip-codesig --all-yes
    mv "/Information/Roblox.app/Contents/MacOS/RobloxPlayer_patched" "/Information/Roblox.app/Contents/MacOS/RobloxPlayer"

    chmod +x "/Information/Roblox.app/Contents/MacOS/libHydrogen.dylib"

    echo -e "Install Complete!"
}

main
