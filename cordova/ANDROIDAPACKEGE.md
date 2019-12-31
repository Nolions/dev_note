# android apk 打包

## 流程

1. build
2. sign
3. align

## build

    cordova build android --release

## sign

### generate key

    # keytool -genkey -v -keystore <keystore's file name>.keystore -alias <alias name> -keyalg <encode method> -keysize <encode key size> -validity <Expiration date>
    keytool -genkey -v -keystore release-key.keystore -alias cordova-demo -keyalg RSA -keysize 2048 -validity 10000

<i> <b>show keystore information</b></i>

example:

    # keytool -list -v -keystore <your's keystore key>
    keytool -list -v -keystore android_release-key.keystore

ps. 如果已經擁有keystore key則可以跳過此步驟

### sign APK

use jarsigner

    # jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore <your keystore key> <apk> <alias name>
    jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore release-key.keystore android-apk/android-release-unsigned.apk cordova-demo

use cordova

    # cordova build android --release -- --keystore=<your keystore key> --alias=<alias name> --storePassword=<keystore's password> --password=<password>
    cordova run android --release -- --keystore=../my-release-key.keystore --alias=alias_name --storePassword=password --password=password

## align APK壓縮與優化(可省略)

    # zipalign -v 4 <original APK> <latest APK>
    zipalign -v 4 android-apk/android-release-unsigned.apk android-apk/cordova-demo.apk

## Auto package

1. creator `build.json` file on cordova project directory
2. input code on build.json

build.json example code

    {
        "android": {
            "debug": {
                "keystore": "your keystore key",
                "alias": "your keystore key's alias",
                "storePassword": "your keystore's password",
                "password" : "password",
            },
            "release": {
                "keystore": "your keystore key",
                "alias": "your keystore key's alias",
                "storePassword": "your keystore's password",
                "password": "password"
            }
        }
    }

3. run `cordova build android --release` or `cordova build android --debug`
