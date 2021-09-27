# Replication Package for RetipDroid

In this repository, we provide original experimental data in the folder **data** and the RetipDroid tool in the folder **RetipDroid**.

# Data

We report activity and line coverage in **activity coverage.csv** and **line_coverage.txt** respectively.

Crashes detected by each tool including RetripDroid, Ape, Monkey, Stoat is described in **Re_crash.txt**, **ape_crash.txt**, **monkey_crash.txt** and **stoat_crash.txt** respectively.

# RetipDroid

## Preparing your environment

1. Have an Android device with USB debugging enabled or an Android emulator.
2. Push RetipDroid runtime files and libraries to your device/emulator.

```bash
cd RetipDroid
adb push jar/*.jar /sdcard
adb push libs/* /data/local/tmp
```

## Run RetipDroid

Format of the command to run RetipDroid:

```
adb shell CLASSPATH=/sdcard/retipdroid.jar:/sdcard/thirdparty.jar:/sdcard/framework.jar exec app_process /system/bin com.android.commands.monkey.Monkey -p [package name] --agent reuseq --running-minutes [desired running time] --throttle [time step between actions] -v
```

### Arguments

* -p [package name]: package name is the app package name under test. If you are not sure the package name of the app, you can check all installed packages by running

```bash
adb shell pm list package
```
* --running-minutes [desired running time]: the execution time in minutes for RetipDroid to test the app.
* --throttle [time step between actions]: the time lag between two actions.

### Intepreting the results

After execution, you can find the following results:

1. Crashes is reported in /sdcard/crash-dump.log
2. Coverage is reported in the command line.