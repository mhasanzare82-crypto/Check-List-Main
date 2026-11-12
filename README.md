# Check List Main

اپلیکیشن مستقل اندرویدی Check List Main برای ساخت و مدیریت چک‌لیست‌ها.

## امکانات
- ساخت چند چک‌لیست، تغییر نام و حذف
- افزودن، ویرایش و حذف موارد
- علامت‌گذاری انجام‌شده و ثبت تاریخچه تغییر وضعیت
- ساخت چک‌لیست از متن چندخطی
- ورود فایل‌های TXT و Excel
- خروجی Excel برای هر چک‌لیست و TXT برای همه چک‌لیست‌ها
- پشتیبان‌گیری و بازیابی
- تنظیم اندازه متن و استفاده از فونت‌های TTF/OTF

## شناسه و نسخه برنامه
شناسه ثابت اندروید: `com.mhasanzare82crypto.checklist_maik`.
نسخه از `pubspec.yaml` خوانده می‌شود. برای هر انتشار، شماره build بعد از `+` را افزایش دهید؛ مثلاً `1.0.0+1` به `1.0.1+2`. شناسه برنامه و کلید امضا نباید عوض شوند.

## اجرای محلی پروژه\n\nپوشه Android در زمان اجرای GitHub Actions ساخته می‌شود. برای اجرای محلی، ابتدا Flutter را نصب کنید و در ریشه پروژه این دستور را اجرا کنید:\n\n\`\`\`bash\nflutter create --platforms=android --org com.mhasanzare82crypto --project-name checklist_maik .\nflutter pub get\n\`\`\`\n\n## تنظیم یک‌باره کلید امضا
برای اینکه APKهای آینده روی نسخه قبلی نصب شوند، همه نسخه‌های Release باید با **یک keystore ثابت** امضا شوند. این فایل را یک‌بار روی رایانه خود بسازید و آن را در مخزن عمومی قرار ندهید:

```bash
keytool -genkeypair -v -keystore checklist-release.jks -keyalg RSA -keysize 2048 -validity 10000 -alias checklist
base64 checklist-release.jks | tr -d '\\n'
```

در GitHub مخزن، به Settings → Secrets and variables → Actions بروید و این چهار Secret را بسازید:
- `SIGNING_KEYSTORE_BASE64`: خروجی دستور base64
- `SIGNING_STORE_PASSWORD`: رمز keystore
- `SIGNING_KEY_ALIAS`: مقدار `checklist`
- `SIGNING_KEY_PASSWORD`: رمز کلید

**فایل keystore و رمزهایش را در جای امن نگه دارید و گم نکنید.** بدون همان کلید، نصب به‌روزرسانی روی نسخه قبلی ممکن نیست.

## انتشار نسخه
1. در `pubspec.yaml` مقدار version را افزایش دهید؛ عدد build بعد از `+` باید هر بار بزرگ‌تر شود.
2. تغییرات را روی شاخه `main` ارسال کنید یا یک تگ مانند `v1.0.1` بسازید.
3. APK در Actions → آخرین اجرا → Artifacts قرار می‌گیرد. با تگ نسخه، Release نیز ساخته می‌شود.

نصب نسخه جدید با همان شناسه و کلید، اطلاعات محلی برنامه را نگه می‌دارد. حذف برنامه یا پاک‌کردن داده‌های آن اطلاعات را حذف می‌کند.
