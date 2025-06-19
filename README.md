# MyReactNativeApp Domain Verification

This repository hosts the domain verification files for MyReactNativeApp Android App Links.

## Files:
- `index.html` - Test page with app links
- `.well-known/assetlinks.json` - Digital Asset Links file for Android App Links verification

## Setup Instructions:

1. **Enable GitHub Pages:**
   - Go to repository Settings → Pages
   - Select "Deploy from a branch"
   - Choose "main" branch and "/ (root)" folder
   - Save

2. **Update AndroidManifest.xml:**
   Replace `myreactnativeapp.com` with your GitHub Pages URL:
   ```xml
   <data android:scheme="https"
         android:host="tiny76767.github.io" 
         android:pathPrefix="/myapp-verification" />
   ```

3. **Test the verification:**
   ```bash
   # Test custom scheme (already working)
   adb shell am start -W -a android.intent.action.VIEW -d "myapp://test" com.myreactnativeapp
   
   # Test HTTPS link (after domain verification)
   adb shell am start -W -a android.intent.action.VIEW -d "https://tiny76767.github.io/myapp-verification/test" com.myreactnativeapp
   ```

## Certificate Fingerprint Used:
```
FA:C6:17:45:DC:09:03:78:6F:B9:ED:E6:2A:96:2B:39:9F:73:48:F0:BB:6F:89:9B:83:32:66:75:91:03:3B:9C
```

This is the SHA256 fingerprint of your debug certificate. For production, you'll need to update this with your release certificate fingerprint.
