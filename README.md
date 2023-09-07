# obsidian-oblige-doom-termux
How to build obsidian / oblige doom level generator in termux


```

Get latest stable from:

https://github.com/obsidian-level-maker/Obsidian/releases

tar xvf release.tgz

pkg install proot-distro
proot-distro install void
proot-distro clear-cache

alias void='proot-distro login void --termux-home --isolated'

void

xbps-install -Su
xbps-install -u xbps

xbps-install gcc
xbps-install cmake
xbps-install make
xbps-install flex
  
 add CONSOLE_ONLY flag:
 
  +++ CMakePresets.json   2023-09-07 01:51:36.706241948 +0000
@@ -53,7 +53,8 @@
       "generator": "Unix Makefiles",
       "installDir": "${sourceDir}/install",
       "cacheVariables": {
-        "CMAKE_BUILD_TYPE": "Release"
+        "CMAKE_BUILD_TYPE": "Release",
+"CONSOLE_ONLY": "ON"
       }
     },
     {
  
 cmake --preset dist
 cmake --build --preset dist
  
    ./obsidian -b test.wad
    
 clean up if you want: 
    
xbps-remove -R gcc
xbps-remove -R cmake
xbps-remove -R flex
xbps-remove -R make
xbps-remove -oO
xbps-remove -yO
rm /var/cache/xbps/*
  

```
