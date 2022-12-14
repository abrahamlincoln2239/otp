#  OTP -  Android OTP Authenticator

[![Build Status](https://travis-ci.org/andOTP/andOTP.svg?branch=master)](https://travis-ci.org/andOTP/andOTP)
[![Current release](https://img.shields.io/github/release/andOTP/andOTP/all.svg)](https://github.com/andOTP/andOTP/releases/download/v0.9.0.1/andOTP_v0.9.0.1.apk)
[![Crowdin](https://d322cqt584bo4o.cloudfront.net/andotp/localized.svg)](https://crowdin.com/project/andotp)
[![Chat - Telegram](https://img.shields.io/badge/chat-Telegram-blue.svg)](https://t.me/andOTP)
[![Chat - Matrix](https://img.shields.io/badge/chat-Matrix-blue.svg)](https://matrix.to/#/#andOTP:privacytools.io)


## Intro

OTP is a two-factor authentication App for Android 5.1+.

It implements Time-based One-time Passwords (TOTP) and HMAC-Based One-Time Passwords (HOTP).
Simply scan the QR code and login with the generated 6-digit code.

This project started out as a fork of the great [OTP Authenticator](https://github.com/0xbb/otp-authenticator) app written by Bruno Bierbaumer,
which has sadly been inactive since 2015. By now almost every aspect of the app has been changed/re-written so the fork status of the Github repository got
detached upon [user request](https://github.com/andOTP/andOTP/issues/145). But all credit for the original version and for starting this project still goes to Bruno!

## Help wanted:
I currently don't have that much time to spend developing OTP, so any contributions are always welcome.
Don't worry, I will still continue to develop OTP it will just slow down from the incredible speed I had going in the beginning.

## Features:

 * Free and Open-Source
 * Requires minimal permissions
   - Camera access for QR code scanning
   - Storage access for import and export of the database
 * Encrypted storage with two backends:
   - Android KeyStore
   - Password / PIN
 * Multiple backup options:
   - Plain-text
   - Password-protected
   - OpenPGP-encrypted
 * Sleek minimalistic Material Design with three different themes:
   - Light
   - Dark
   - Black (for OLED screens)
 * Great Usability
 * Compatible with Google Authenticator
 * Supported algorithms:
   - TOTP (Time-based One-time Passwords) as specified in [RFC 6238](https://tools.ietf.org/html/rfc6238)
   - HOTP (HMAC-based One-time Passwords) as specified in [RFC 4226](https://tools.ietf.org/html/rfc4226)

## Backups:

To keep your account information as secure as possible OTP only stores it in
encrypted data files. A part of the encryption key used for that is stored in the
Android KeyStore system. The advantage of this approach is that the key is kept
separate from the apps data and, as a bonus, can be backed by hardware cryptography
(if your device supports this).

However, due to that separation, backups with 3rd-party apps like Titanium Backup can not
be used with OTP. Such apps only backup the encrypted data files and not the encryption
key, which renders them useless.

**Please only use the internal backup functions provided by OTP to backup your accounts!**
**Everything else WILL result in data loss.**

### Opening the backups on your PC:

 * [OpenPGP](https://openpgp.org/): OpenPGP can be used to easily decrypt the **OpenPGP-encrypted backups** on your PC.
 * [WebDecrypt](https://flocke.shadowice.org/andOTP/decrypt/): JavaScript-based decryption of the **new password-protected backup format** in the browser ([source code](https://github.com/andOTP/WebDecrypt)).
 * [andOTP-decrypt](https://github.com/asmw/andOTP-decrypt): Python script written by @asmw to decrypt the **old and new password-protected backup format** on your PC.
 * [mac2fa](https://github.com/lorenzo2897/mac2fa): Electron app for macOS that lives in your system tray and generates OTPs from an encrypted backup file.
 * [go-andotp](https://github.com/grijul/go-andotp): CLI Program written in go to encrypt/decrypt andOTP files on your PC. Decrypted files can be encrypted and imported back to andOTP.

### Automatic backups:

 * BroadcastReceivers: AndOTP supports a number of broadcasts to perform automated backups, eg. via Tasker. These will get saved to the defined backup directory. **These only work when KeyStore is used as the encryption mechanism**
   - **org.shadowice.flocke.andotp.broadcast.PLAIN_TEXT_BACKUP**: Perform a plain text backup. **WARNING**: This will save your 2FA tokens onto the disk in an unencrypted manner!
   - **org.shadowice.flocke.andotp.broadcast.ENCRYPTED_BACKUP**: Perform an encrypted backup of your 2FA database using the selected password in settings.

## Migration:

Check out [this](https://github.com/andOTP/andOTP/wiki/Migration) wiki page to learn about the different ways to migrate to andOTP from other 2FA apps.

## Downloads:

[<img height=80 alt="Get it on Google Play" src="https://play.google.com/intl/en_us/badges/images/generic/en-play-badge.png" />](https://play.google.com/store/apps/details?id=org.shadowice.flocke.andotp)
[<img height=80 alt="Get it on F-Droid" src="https://fdroid.gitlab.io/artwork/badge/get-it-on.png" />](https://f-droid.org/packages/org.shadowice.flocke.andotp/)
[<img height=80 alt="Get it on GitHub" src="https://raw.githubusercontent.com/flocke/andOTP/master/assets/badges/get-it-on-github.png" />](https://github.com/andOTP/andOTP/releases)

**Warning**: All three versions (Google Play, F-Droid and the APKs) are not compatible (not signed by the same key)!
You will have to uninstall one to install the other, which will delete all your data.
So make sure you have a **current backup** before switching!

## Contribute:

 * **Translation**: If you want to help translate OTP into your language head over to the [Crowdin project](https://crowdin.com/project/andotp).
 * **Bug reports and feature requests**: You can report bugs and request features in the [Issue tracker](https://github.com/andOTP/andOTP/issues) on GitHub.
 * **Requesting thumbnails**: If you are missing a thumbnail you can request it by [opening a thumbnail request](https://github.com/andOTP/andOTP/issues/new/choose).
 * **Discussion and support**: 
   - [XDA thread](https://forum.xda-developers.com/android/apps-games/app-andotp-android-otp-authenticator-t3636993) (please keep off-topic to a minimum)
   - Telegram group [@OTP](https://t.me/andOTP) (if you just want important updates you can mute the group so you only get notified about pinned messages)
   - Matrix channel [#OTP:tchncs.de](https://matrix.to/#/#andOTP:tchncs.de)

#### Donations:

If you want to show your appreciation for our work with a small donation you can do so using the following links:

 * [Donate to Jakob Nixdorf](https://flocke.shadowice.org/donate.html) (Main developer, maintainer)
 * [Donate to Richy HBM](https://richyhbm.co.uk/donate) (Developer)

## Acknowledgments:
#### Open-source components used:

 * [AboutLibraries](https://github.com/mikepenz/AboutLibraries)
 * [Apache Commons Codec](https://commons.apache.org/proper/commons-codec/)
 * [Expandable Layout](https://github.com/AAkira/ExpandableLayout)
 * [Floating Action Button Speed Dial](https://github.com/leinardi/FloatingActionButtonSpeedDial)
 * [material-intro](https://github.com/heinrichreimer/material-intro)
 * [MaterialProgressBar](https://github.com/DreaminginCodeZH/MaterialProgressBar)
 * [OpenPGP API library](https://github.com/open-keychain/openpgp-api)
 * [ZXing Android Embedded](https://github.com/journeyapps/zxing-android-embedded)
 * [Droid Sans Mono Zeromod](https://github.com/AlbertoDorado/droid-sans-mono-zeromod)

#### Code examples used:

 * [Android-ItemTouchHelper-Demo](https://github.com/iPaulPro/Android-ItemTouchHelper-Demo/tree/master/app/src/main/java/co/paulburke/android/itemtouchhelperdemo/helper)
 * [Code Parts from Google's Android Samples](https://android.googlesource.com/platform/development/+/master/samples/Vault/src/com/example/android/vault)
 * [LetterBitmap](https://stackoverflow.com/questions/23122088/colored-boxed-with-letters-a-la-gmail)
 * [DimensionConverter](https://stackoverflow.com/questions/8343971/how-to-parse-a-dimension-string-and-convert-it-to-a-dimension-value)
 * [NumberPickerPreference](https://github.com/Alobar/AndroidPreferenceTest/tree/master/alobar-preference)

#### Previously used open-source components:

 * [FABsMenu](https://github.com/jahirfiquitiva/FABsMenu)
 * [LicensesDialog](https://github.com/PSDev/LicensesDialog)
 * [VNTNumberPickerPreference](https://github.com/vanniktech/VNTNumberPickerPreference)

#### Previously used code examples:

 * [FloatingActionMenuAndroid](https://github.com/pmahsky/FloatingActionMenuAndroid)

