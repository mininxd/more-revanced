# APKM to APK Conversion Feature

## Overview
This project now includes automatic conversion of APKM (Android App Bundle) files to standard APK format. This resolves build errors that occurred when the download sources provided APKM files instead of APK files, especially for Magisk module builds.

## How It Works
- When the build process downloads an app from APKMirror, UpToDown, or other sources, it may sometimes receive an APKM file (Android App Bundle format) instead of a standard APK
- The build system now automatically detects when an APKM file is downloaded
- The system uses APKEditor to convert the APKM file to a standard APK format
- Both the main build process and Magisk module creation now use the properly converted APK files

## Technical Details
- New `convert_apkm_to_apk()` function in `utils.sh` handles the conversion
- The function uses APKEditor to extract the base APK from the app bundle
- Enhanced download functions with fallback logic to handle conversion if standard merging fails
- Magisk module creation process includes additional checks to ensure APK format is used instead of APKM

## Benefits
- Eliminates build failures when sources provide APKM files instead of APK files
- Ensures Magisk modules are built correctly with proper APK format
- Maintains backward compatibility with standard APK downloads
- Improves build reliability across different download sources

## Requirements
- Java runtime (already required for the build process)
- APKEditor tool (automatically downloaded during build)