# Buxgalteriya — Android va iOS ilova loyihasi

Bu loyiha Capacitor yordamida sizning HTML ilovangizni haqiqiy Android (.aab) va iOS (.ipa) ilovaga aylantiradi.
Ilova kodi: `www/index.html` (o'zgartirsangiz — hammasi shu faylda).

## Oldindan kerak bo'ladi
- Node.js (nodejs.org, LTS versiya)
- Android uchun: Android Studio (developer.android.com/studio)
- iOS uchun: Mac kompyuter + Xcode (Windows'da iOS ilova yig'ib bo'lmaydi)
- Google Play Console akkaunt: bir martalik $25
- Apple Developer Program: yiliga $99

## 1-qadam: tayyorlash (bir marta)
```
npm install
npx cap add android
npx cap add ios          # faqat Mac'da
npx capacitor-assets generate   # ikonka va splash yaratadi (assets/ papkasidan)
npx cap sync
```

## 2-qadam: Android → Play Market
```
npx cap open android
```
Android Studio ochiladi:
1. `Build > Generate Signed App Bundle / APK` → **Android App Bundle (.aab)**
2. Yangi keystore yarating va **uni va parolini yo'qotmang** (kelajakda yangilash uchun kerak).
3. Hosil bo'lgan `.aab` faylni play.google.com/console ga yuklang.
4. Do'kon sahifasi: nom, tavsif, skrinshotlar, 512x512 ikonka (`www/icon-512.png`), 1024x500 banner.
5. **Maxfiylik siyosati (Privacy Policy) havolasi** kerak — ilova hech narsa yig'maydi, deb oddiy sahifa yozing.
6. Yangi shaxsiy akkauntlarda: ommaga chiqishdan oldin yopiq testda kamida 12 ta tester 14 kun sinashi talab qilinadi (Google qoidasi o'zgargan bo'lishi mumkin — Play Console'da tekshiring).

## 3-qadam: iOS → App Store
```
npx cap open ios
```
Xcode'da: Signing & Capabilities'da Apple akkauntingizni tanlang → `Product > Archive` → `Distribute App` → App Store Connect. Keyin appstoreconnect.apple.com da sahifani to'ldirib, review'ga yuboring.

## Yangilash
`www/index.html` ni o'zgartiring, keyin:
```
npx cap sync
```
va Android Studio/Xcode'da versiyani oshirib (versionCode / Build number) qayta yuklang.

## Bundle ID
`uz.hisobvaraqlar.rejasi` — Play Market'da noyob bo'lishi kerak. O'zgartirmoqchi bo'lsangiz, `npx cap add` dan OLDIN `capacitor.config.json` da o'zgartiring.
