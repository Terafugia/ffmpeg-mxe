###Build FFmpeg under Unix for Windows (x86) 32bit and 64bit

This script is going to build a *shared* version of ffmpeg that does not have any dependencies, i.e: all dependencies are linked statically. 

This is expected that you have installed MXE http://mxe.cc and cloned their git repository somewhere.
We will reference that git repository root in the script build-ffmpeg.sh by the variable **MXE_PATH**.

The first time you install MXE you must create a file **settings.mk** as such:

    cd mxe
    echo "MXE_TARGETS := x86_64-w64-mingw32.static i686-w64-mingw32.static" > settings.mk

On the first install you will be probably missing most of dependencies, so you should try installing the ffmpeg package provided by MXE itself. We will build our own afterwards because MXE will build a *static* version of ffmpeg (libav*.a). 
    #You are in mxe/
    make ffmpeg

Now ffmpeg static is assumed to be installed via MXE.

Open *build-ffmpeg.sh* and edit the customizable options to setup the remote server where to upload and get third party sources. Optionally you can change the dependencies and ffmpeg version.

Now just type:
    
    export MXE_PATH=...
    sh build-all.sh

This will build 4 variants of ffmpeg: 64bit-Gplv2 64bit-LGPL 32bit-GPLv2 32bit-LGPL.

Alternatively you can build only one of them by using:

    export MXE_PATH=...
    env <BUILD_LGPL=1> sh build-ffmpeg.sh 64


