# Cosmetics POS (Android)

A Persian, RTL single-file cosmetics point-of-sale app. The web app is in `www/index.html`; data is stored locally in the browser (localStorage). Initial accounts: `admin / 1234`, `seller / 1111`, and `acc / 2222`.

## Option A — Instant install on Android using Chrome

1. Publish or serve the contents of `www/` from an HTTPS website (camera scanning and PWA installation require a secure context; `localhost` also works for local testing).
2. Open that site in Chrome on Android.
3. Open Chrome's menu and choose **Add to Home screen** (or **Install app**, if shown), then confirm.

The app needs internet access on first load for its CDN-hosted libraries/styles (Tailwind, Vazirmatn font, and Html5Qrcode). Product and invoice data is kept on that device/browser. Export a JSON backup regularly. Browser permissions are required for live camera scanning.

## Option B — Build a standard Android APK with Capacitor

Requirements: Node.js/npm and Android Studio with Android SDK installed. From the project directory:

```sh
npm install
npx cap add android
npx cap open android
```

In Android Studio, use **Build > Build Bundle(s) / APK(s) > Build APK(s)**. The generated APK is available from the Android Studio build output (typically `android/app/build/outputs/apk/debug/app-debug.apk`). If Android platform files are already present, use `npx cap sync android` before opening/building.

`capacitor.config.json` points Capacitor at the `www` directory. For production distribution, configure signing and build a signed release APK/AAB from Android Studio.

## Features

- Login and role-specific navigation.
- Product management, live camera barcode scanner and image/gallery barcode scan via Html5Qrcode.
- Inventory stock adjustments.
- POS cart, scan/search, checkout, VAT, and on-screen invoice receipt.
- Sales and profit reports with Jalali dates and top-product/brand bar charts.
- JSON data export/import.

## Notes

- The checkout calculates VAT using each product's configured VAT rate (seeded products default to 10%).
- Data is local to one browser/device; this is not a multi-user cloud database or a payment gateway.
