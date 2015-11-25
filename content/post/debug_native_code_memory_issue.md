+++
categories = ["Android", "NDK", "AOSP"]
date = "2015-11-24T18:56:44-05:00"
description = ""
keywords = ["Android", "Debug", "NDK", "Memory", "AOSP", "addr2func"]
title = "How I debugged memory leak issue for mediaserver"

+++

Recently I had to fix big memory leak issue in "medieaserver". From the internet I found very nice tool called `addr2func` for fixing the issue.

The tool is written by [freepine](http://freepine.blogspot.ca/2010/02/analyze-memory-leak-of-android-native.html) and I modified for supporting latest version of AOSP bases codes(5.0) and uploaded into Github : [addr2func](https://github.com/leehack/addr2func)

*Pre-condition - eng or userdebug build of device and android full source code*

1. Download [addr2func](https://raw.githubusercontent.com/leehack/addr2func/master/addr2func.py)
2. Give excute permission.  
    ```
    $chmod +x addr2func.py
    ```

3. Enable memory allocation debug feature for `mediaserver`.  
    ```
    $adb shell setprop libc.debug.malloc 1
    $adb shell ps mediaserver
    $adb shell kill <mediaserver_pid>
    ```

4. Dump memory status of `mediaserver` into `dump1` file.  
    ```
    $adb shell ps mediaserver
    $adb pull /proc/<mediaserver_pid>/maps
    $adb shell dumpsys media.player -m > dump1
    ```

5. Do the memory leak test on the device.  
6. Dump memory status of `mediaserver` into `dump2` file.  
    ```
    $adb pull /proc/<mediaserver_pid>/maps
    $adb shell dumpsys media.player -m > dump2
    ```

7. make `diff` between `dump1` and `dump2`.  
    ```
    $diff dump1 dump2 > diff
    ```
    
8. Save memory allocation trace into `mem_trace` file.  
    ```
    $./addr2func.py --root-dir=<AOSP_dir> --maps-file=maps --product=<product_name_of_your_build> diff > mem_trace
    ```

The memory allocation trace is saved in `mem_trace` file. It will show you where exactly the memory is allocated. `dup` is duplication count.