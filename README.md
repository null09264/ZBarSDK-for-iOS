ZBarSDK-for-iOS
---------------------

64bits ZbarSDK for iOS (armv7, amrv7s, arm64).

Refers to http://stackoverflow.com/questions/18740304/linker-error-in-xcode-5/18937831#18937831


**The lib in this repo has already been rebuilt for 64bit devices, but in case you want to built it on your own, the explicit steps are listed below:**


===============


Download Mercurial first

Clone the source:
```bash
hg clone http://zbar.hg.sourceforge.net:8000/hgroot/zbar/zbar 
cd zbar 
hg checkout iPhoneSDK-1.3.1 

open iphone/zbar.xcodeproj
```

In Xcode's menu, select **"Product > Scheme > libzbar"** and then select **"Product > Scheme > Edit Scheme…"**. Select **"Run"** in the build configuration and click **OK**.

In the Project and Targets list, select the libzbar target and click on the Build Settings tab. Verify your Architecture settings, make sure it says **iOS and arm64 armv7 armv7s**. Also don't forget to change Architectures to **Standard architectures (armv7, armv7s, arm64)**, otherwise your project won't compile with arm64.

Go back to **"Product > Scheme > Edit Scheme…"** and check the **"Destination"** drop-down menu. Change to the simulator. (Build once for both iOS Device and simulator)

Combine the two library:

```bash
cd ~/Library/Developer/Xcode/DerivedData
/Users/mario/Library/Developer/Xcode/DerivedData/zbar-******
cd Build
cd Products
lipo -create Release-iphoneos/libzbar.a Release-iphonesimulator/libzbar.a -o libzbar.a 
cp libzbar.a ~/Desktop (Copy it to your desktop)
```

replace the **libzbar.a** in your project!

Done!
