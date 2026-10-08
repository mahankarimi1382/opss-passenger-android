# opss Passenger (Android) — اپ اندروید مسافر

اپلیکیشن اندروید مسافرِ پلتفرم چندسرویسی **opss** (سورس v3Cube سال ۲۰۲۱، در قالب پروژه opss سازماندهی شده).

| مورد | مقدار |
| --- | --- |
| Package | `com.alaadcin.user` |
| minSdk / targetSdk | 17 / 31 |
| Gradle / AGP | 5.4.1 / 3.5.2 |
| JDK موردنیاز | **8** |
| Flavor اصلی | `prod` |

## CI/CD

هر push روی شاخه `main` باعث اجرای GitHub Actions می‌شود:
بیلد `assembleProdDebug` گرفته شده و APK روی **GitHub Release** با تگ `v<versionName>` منتشر می‌شود (asset هر بیلد جدید جایگزین قبلی می‌شود).

اجرای دستی: تب **Actions** → **Build & Release** → **Run workflow**.

## بیلد محلی

نیازمند JDK 8 و Android SDK با platform 31 و build-tools 31.0.0:

```bash
./gradlew assembleProdDebug
```

## یادداشت امضا (signing)

کانفیگ امضای release به مسیر keystore روی ماشین فروشنده (`C:\Users\sitw2\Documents\okboz.jks`) اشاره می‌کند. چون فایل keystore در مخزن قرار ندارد، این کانفیگ **شرطی** شده است: اگر keystore موجود نباشد، بیلد debug با keystore پیش‌فرض debug اندروید انجام می‌شود. برای بیلد release واقعی، مسیر keystore را در `app/build.gradle` به مکان درست خودتان تغییر دهید.
