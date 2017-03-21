# pangolin_android
A repository for pangolin on android

## MainPage
This repository is aimed at transplanting pangolin to android.Author of Pangolin is stevenlovegrove and source repository is:[https://github.com/stevenlovegrove/Pangolin](https://github.com/stevenlovegrove/Pangolin).Introduction about Pangolin detail can be found at source code's github page. Original Pangolin contains a method to transplant it to android however hard to achieve with some errors inside the CMakeLists and source code.I made a small change for Pangolin to make it suitable for OPENGL ES/ES2.

## Code
Find the latest version on [Github](https://github.com):
``` 
 git clone https://github.com/FangGet/pangolin_android.git
```

## Standalone Libs And Examples
Compiled libs and examples for android can be found here: [http://pan.baidu.com/s/1c2dXRXm](http://pan.baidu.com/s/1c2dXRXm);

## Dependencies
* Android SDK;
* Android NDK(>r5e);
* Android-Cmake(given);

You should have installed Android SDK on your Linux and environment variables should have been setted properly. SDK have to be updated with version>android-8.

Android NDK can be only extracted to certain directory.

Android-Cmake may not perform properly on Windows.

Other dependencies for pangolin can be found at[https://github.com/FangGet/pangolin_android/tree/master/Pangolin](https://github.com/FangGet/pangolin_android/tree/master/Pangolin).

## Building
pangolin_android uses CMake portable pre-build tool. Please excute the following at a shell (or the equivelent using a GUI):
```
git clone  https://github.com/FangGet/pangolin_android.git
export $ANDROID_NDK=you android ndk root directory
cd pangolin_android
mkdir build
cd build
cmake -DCMAKE_TOOLCHAIN_FILE=../android-cmake/android.toolchain.cmake \
      -DANDROID_NDK=$ANDROID_NDK                       \
      -DCMAKE_BUILD_TYPE=Release                     \
      -DANDROID_ABI="armeabi-v7a with NEON"          \
      -DANDROID_NATIVE_API_LEVEL=android-14          \
      <source_path>
 cmake --build 
```
ANDROID_BUILD_TYPE:(must be specified)
  * Debug
  * Release

Android_ABI:
  * armeabi
  * armeabi-v7a
  * armeabi-v7a with NEON

## Issues
Please visit [Github Issues](https://github.com/FangGet/pangolin_android/issues) to view and report problems with pangolin_android. I will try my best to answer it.

Contact with: fangasfrank@gmail.com

## Usage
The examples can be directly built and run with cmake and ant. Below is how it can be used in regular android app:

Compiled libs(libpangolin.so) and headers(including config.h) can be used in regular android apps as a native activity. Pangolin contains a DeferredNativeActivity_onCreate method which would call main function defined in a seperate lib which contains the application code by users. So the convention in the examples can be followed: by providing a bootstrap native activity, loading the application lib and pangolin and calling xxx_onCreate method, the pangolin lib will do all the  initialization work and call the main method in the application lib which is just like application in regular linux environment.

User code must be linked with the android lib and egl libs.
