# Two-Foot Trainer — iOS Build (Capacitor)

This folder is ready for you to generate an iOS app (TestFlight/App Store) from your existing PWA.

## Quick preview on iPhone (no App Store)
1. Host the `www` folder (any static host) **or** open `index.html` directly in Safari.
2. In Safari, tap **Share → Add to Home Screen**. That installs it as a web app.

## Build a real iOS app (TestFlight/App Store)
**Prereqs:** Apple Developer account, Xcode, Node.js

```bash
cd twofoot-ios
npm install @capacitor/core @capacitor/ios --save
# (Optional) if a package.json already exists, just run npm install
npx cap init "Two-Foot Trainer" "com.cognitivesoccer.twofoot" --web-dir=www
npx cap add ios
npx cap copy
npx cap open ios
```

Then in Xcode:
1. Select the **iOS** target → set Team (your Apple ID) → increment version/build.
2. In **Signing & Capabilities**, enable **Push Notifications** only if you need them (not required here).
3. Set `Info.plist` → `LSApplicationQueriesSchemes` only if you add custom schemes later.
4. Archive (**Product → Archive**) and distribute to **TestFlight** or **App Store**.

## App Icons / Launch Screens
- Included maskable icons in `www/assets/icons`. Xcode will auto-generate most sizes when you drag in `icon-512.png`.
- For Splash/LaunchScreen, use Xcode's **LaunchScreen.storyboard** with a white/gray background to match `#f1f3f5`.

## PWA Notes
- `manifest.webmanifest` and `sw.js` are included for offline support.
- The app stores custom drills and notes in **localStorage** per device.

## Updating the app
- Replace files in `www/` (e.g., new drills or UI updates).
- Run `npx cap copy` then rebuild/Archive from Xcode.

— Enjoy!
```