+++
categories = ["Android", "NDK", "Gradle"]
date = "2015-11-23T12:56:25-05:00"
updated = "2016-06-03T13:16:00-05:00"
description = "Example for gradle build script for Android library module with native code with prebuilt .so"
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
        classpath 'com.android.tools.build:gradle-experimental:0.7.0'
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

    repositories {
        prebuilt(PrebuiltLibraries) {
            prebuiltSharedlib {
                binaries.withType(SharedLibraryBinary) {
                    sharedLibraryFile = file("src/main/jniLibs/${targetPlatform.getName()}/prebuiltSharedlib.so")
                }
            }
        }
    }
    android.sources {
        main {
            jni {
                dependencies {
                    library "prebuiltSharedlib"
                }
            }
        }
    }
}

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
}
```