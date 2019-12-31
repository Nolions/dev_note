# Cordova CLI Tutorial

## Install cordova

npm install -g cordova

## Created Project

    cordova create hello com.example.hello “APP Name"

## list

    cordova run android —list

## clean

    cordova clean

## Android

### add platform

     cordova platform add android

Example:

    cordova build android --debug
    cordova build android --release

### run & deploy

    cordova run android --<device> --<model>

device|describe
---|---|  
emulator| to deploy the app on a default android emulator
device| to deploy the app on a connected device

model|describe
---|---|  
nobuild|
debug|
release|

Example:

    # deploy to android emulator
    cordova run --emulator android
    # deploy to connected device
    cordova run android --device

    # build debug app and deploy to android emulator
    cordova run --emulator --debug
    # build release app and deploy to android emulator
    cordova run --emulator --release

### build

generate app's apk file

    cordova build android

    cordova build android --<model>

model|describe
---|---|  
debug|
release|

### Package

[android package](./ANDROIDAPACKEGE.md)

## iOS

### add platform

    cordova platform add ios

### build

    cordova build ios

### run & deploy

cordova run ios --<device>

device|describe
---|---|  
emulator| to deploy the app on a default android emulator
device| to deploy the app on a connected device

example:

    cordova run ios --emulator
    cordova run ios --device

When Error is:

`ios/build/emulator/--appname.app--/Info.plist file not found`

`error: archive not found at path '/Users/~/platforms/ios/appname.xcarchive`

    cordova emulate ios --target="--device--" --buildFlag="-UseModernBuildSystem=0"
