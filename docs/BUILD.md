## Build instructions

### Windows Visual Studio 2019

* Prequisite: vsnasm integration
  - get VSNASM from https://github.com/ShiftMediaProject/VSNASM
  - run install_script.bat

* Clone repo

  Clone https://github.com/pinterf/assrender from VS IDE or 

      git clone https://github.com/pinterf/assrender
      git submodule update --init --recursive --remote

* Prequisite: avisynth.lib versions (x86 and x64)
  - When you have installed Avisynth through an installer and have installed FilterSDK  
    get it from c:\Program Files (x86)\AviSynth+\FilterSDK\lib\x86 and x64
  - Or get it from the 'filesonly' builds at Avisynth+ releases
	  https://github.com/AviSynth/AviSynthPlus/releases

  Copy lib files  to assrender\lib\x86-64\ and assrender\lib\x86-32\ 
  32 and 64 bit versions respectively

* Build:
  Open solution file from IDE

### Windows GCC (mingw installed by msys2)

* Clone repo

      git clone https://github.com/pinterf/assrender
        
  This environment is not using the git submodules, we need libass as a package.
  There is no need for submodule update.

* Prequisite: avisynth.lib versions (x86 and x64)
  - When you have installed Avisynth through an installer and have installed FilterSDK  
    get it from c:\Program Files (x86)\AviSynth+\FilterSDK\lib\x86 and x64
  - Or get it from the 'filesonly' builds at [Avisynth+ releases](https://github.com/AviSynth/AviSynthPlus/releases)

  Copy lib files  to assrender\lib\x86-64\ and assrender\lib\x86-32\ 
  32 and 64 bit versions respectively

* Prequisite: libass package

  - List libass versions

        $ pacman -Ss libass

    Output:

        mingw32/mingw-w64-i686-libass 0.16.0-1
        A portable library for SSA/ASS subtitles rendering (mingw-w64)
        mingw64/mingw-w64-x86_64-libass 0.16.0-1
        A portable library for SSA/ASS subtitles rendering (mingw-w64)

  - Get package

    Example for x64 version:
  
        $ pacman -S mingw64/mingw-w64-x86_64-libass

    Output:

          resolving dependencies...
          looking for conflicting packages...
          warning: dependency cycle detected:
          warning: mingw-w64-x86_64-harfbuzz will be installed before its mingw-w64-x86_64-freetype dependency

          Packages (10) mingw-w64-x86_64-fontconfig-2.13.93-1
                      mingw-w64-x86_64-freetype-2.10.4-1
                      mingw-w64-x86_64-fribidi-1.0.10-2
                      mingw-w64-x86_64-glib2-2.66.4-1
                      mingw-w64-x86_64-graphite2-1.3.14-2
                      mingw-w64-x86_64-harfbuzz-2.7.4-1
                      mingw-w64-x86_64-libpng-1.6.37-3  mingw-w64-x86_64-pcre-8.44-2
                      mingw-w64-x86_64-wineditline-2.205-3
                      mingw-w64-x86_64-libass-0.15.0-1

          Total Download Size:    6.92 MiB
          Total Installed Size:  42.31 MiB

          :: Proceed with installation? [Y/n]

     Choose Y and wait

* Build
  under project root:

      rm -r build
      cmake -G "MinGW Makefiles" -B build -S .
      cmake --build build --config Release --clean-first

### Linux
* Clone repo

      git clone https://github.com/pinterf/assrender
      cd assrender
      cmake -B build -S .
      cmake --build build --clean-first
  
  Remark: submodules are not needed, libass is used as a package.

* Find binaries at
    
      build/assrender/libassrender.so

* Install binaries

      cd build
      sudo make install
