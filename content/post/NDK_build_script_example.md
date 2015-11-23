+++
categories = ["Android"]
date = "2015-11-23T12:56:25-05:00"
description = "Example for gradle build script for Android library module with native code and prebuilt .so"
keywords = ["Android", "NDK", "Gradle"]
title = "Gradle NDK Build Script Example"

+++

With this sample, you'll be able to build NDK from Android Studio. 
Now the gradle-experimental plug-in supports dependency. The dependency part show you how to include prebuilt shared library.

I put the prebuilt .so files into `/src/main/jniLibs`. source codes are in `/src/main/jni`

The sample script is for android library project which will make `.aar`

```
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle-experimental:0.4.0'
    }
}

apply plugin: 'com.android.model.library'
model {
    android {
        compileSdkVersion = 23
        buildToolsVersion = "23.0.2"
        defaultConfig.with {
            minSdkVersion.apiLevel = 19
            targetSdkVersion.apiLevel = 23
        }
    }

    compileOptions.with {
        sourceCompatibility=JavaVersion.VERSION_1_7
        targetCompatibility=JavaVersion.VERSION_1_7
    }

    android.ndk {
        moduleName = "libName"
        cppFlags.add("-DANDROID_NDK")
        cppFlags.add("-fexceptions")
        ldLibs.addAll(["android", "log", "GLESv2", "dl", "jnigraphics", "z"])
        stl       = "stlport_static"
        abiFilters.add("armeabi")
        abiFilters.add("armeabi-v7a")
        abiFilters.add("arm64-v8a")
        abiFilters.add("x86")
        abiFilters.add("x86_64")
    }

    android.sources {
        main {
            jni {
                dependencies {
                    library file("src/main/jniLibs/armeabi/prebuiltSharedlib.so") abi "armeabi"                    library file("src/main/jniLibs/armeabi-v7a/prebuiltSharedlib.so") abi "armeabi-v7a"
                    library file("src/main/jniLibs/arm64-v8a/prebuiltSharedlib.so") abi "arm64-v8a"
                    library file("src/main/jniLibs/x86_64/prebuiltSharedlib.so") abi "x86_64"
                    library file("src/main/jniLibs/x86/prebuiltSharedlib.so") abi "x86"
                }
            }
        }
    }
}

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
}
```