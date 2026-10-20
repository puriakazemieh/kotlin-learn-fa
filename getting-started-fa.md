---
cssclasses:
  - persian-rtl
---

# شروع کار با Kotlin

[مشاهدهٔ جدیدترین نسخهٔ منتشرشدهٔ Kotlin](https://kotlinlang.org/docs/releases.html)

زبان Kotlin زبانی مدرن، مختصر و چندسکویی (multiplatform) است که با Java و زبان‌های دیگر قابلیت همکاری (interoperability) دارد.

تازه با Kotlin آشنا شده‌اید؟ برای یادگیری مفاهیم پایه، تور Kotlin را مستقیماً در مرورگر خود بگذرانید.

[شروع تور Kotlin](tour/kotlin-tour-welcome.md)

## نصب Kotlin

زبان Kotlin در هر نسخهٔ [IntelliJ IDEA](https://www.jetbrains.com/idea/download/) و [Android Studio](https://developer.android.com/studio) گنجانده شده است.
برای شروع استفاده از Kotlin، یکی از این محیط‌های توسعهٔ یکپارچه (IDE) را دانلود و نصب کنید.

## انتخاب کاربرد Kotlin

### کنسول

در این بخش یاد می‌گیرید چگونه یک برنامهٔ کنسولی (console application) بسازید و با Kotlin آزمون واحد (unit test) بنویسید.

1. **[ساخت یک برنامهٔ پایه برای JVM با راهنمای ساخت پروژهٔ IntelliJ IDEA](jvm/jvm-get-started.md).**

2. **[نوشتن نخستین آزمون واحد](jvm/jvm-test-using-junit.md).**

### بک‌اند

در این بخش یاد می‌گیرید چگونه با Kotlin یک برنامهٔ بک‌اند (backend) در سمت سرور بسازید.

* **افزودن Kotlin به پروژهٔ Java:**

  * [پیکربندی یک پروژهٔ Java برای کار با Kotlin](jvm/mixing-java-kotlin-intellij.md)
  * [افزودن آزمون‌های Kotlin به پروژهٔ Java مبتنی بر Maven](jvm/jvm-test-using-junit.md)

* **ساخت یک برنامهٔ بک‌اند از ابتدا با Kotlin:**

  * [ساخت یک سرویس وب RESTful با Spring Boot](jvm/jvm-get-started-spring-boot.md)
  * [ساخت APIهای HTTP با Ktor](https://ktor.io/docs/creating-http-apis.html)

### چندسکویی

در این بخش یاد می‌گیرید چگونه با استفاده از [Kotlin Multiplatform](https://kotlinlang.org/docs/multiplatform/get-started.html) یک برنامهٔ چندسکویی (cross-platform) بسازید.

1. **[آماده‌سازی محیط برای توسعهٔ چندسکویی](https://kotlinlang.org/docs/multiplatform/quickstart.html).**

2. **ساخت نخستین برنامهٔ خود برای iOS و Android:**

   * یک برنامهٔ چندسکویی از ابتدا بسازید و:
     * [منطق کسب‌وکار را به اشتراک بگذارید و رابط کاربری (UI) را بومی نگه دارید](https://kotlinlang.org/docs/multiplatform/multiplatform-create-first-app.html)
     * [منطق کسب‌وکار و رابط کاربری را به اشتراک بگذارید](https://kotlinlang.org/docs/multiplatform/compose-multiplatform-create-first-app.html)
   * [برنامهٔ Android موجود خود را برای اجرا روی iOS آماده کنید](https://kotlinlang.org/docs/multiplatform/multiplatform-integrate-in-existing-app.html)
   * [یک برنامهٔ چندسکویی با Ktor و SQLdelight بسازید](https://kotlinlang.org/docs/multiplatform/multiplatform-ktor-sqldelight.html)

3. **[پروژه‌های نمونه](https://kotlinlang.org/docs/multiplatform/multiplatform-samples.html) را بررسی کنید**.

### Android

برای شروع استفاده از Kotlin در توسعهٔ Android، [پیشنهاد Google برای شروع کار با Kotlin در Android](https://developer.android.com/kotlin/get-started) را بخوانید.

### تحلیل داده

از ساخت خط لولهٔ داده (data pipeline) تا آماده‌سازی مدل‌های یادگیری ماشین (machine learning) برای استفاده در محیط عملیاتی، Kotlin گزینه‌ای مناسب برای کار با داده‌ها و بهره‌برداری بهتر از آن‌ها است.

1. **داده‌های خود را بررسی و با آن‌ها آزمایش کنید:**

   * [DataFrame](https://kotlin.github.io/dataframe/overview.html) – کتابخانه‌ای برای تحلیل و دست‌کاری داده‌ها.
   * [Kandy](https://kotlin.github.io/kandy/welcome.html) – ابزاری برای رسم نمودار و مصورسازی داده‌ها.

2. **Kotlin for Data Analysis را در Twitter دنبال کنید:** [KotlinForData](http://twitter.com/KotlinForData).

## دریافت پشتیبانی

اگر با دشواری یا مشکلی روبه‌رو شدید، در ![[slack.svg|25]] Slack کمک بخواهید: [دعوت‌نامه بگیرید](https://surveys.jetbrains.com/s3/kotlin-slack-sign-up) یا مشکل را در [سامانهٔ پیگیری مشکلات](https://youtrack.jetbrains.com/issues/KT) گزارش کنید.

اگر چیزی در این صفحه جا افتاده است یا به نظرتان گیج‌کننده می‌آید، لطفاً [بازخورد خود را با ما در میان بگذارید](https://surveys.hotjar.com/d82e82b0-00d9-44a7-b793-0611bf6189df).

---

## تمرین و مرور

این بخش برای مرور اضافه شده و بخشی از متن رسمی نیست. این صفحه فقط مسیرهای شروع را معرفی می‌کند و آموزش کدنویسی یا مثال کد ندارد؛ بنابراین فعالیت‌های زیر بر اساس اطلاعات همین صفحه هستند.

### پنج پرسش بازیابی فعال

1. این صفحه چه ویژگی‌هایی برای Kotlin نام می‌برد و از کدام زبان به‌عنوان نمونه‌ای برای قابلیت همکاری نام می‌برد؟
2. برای شروع کار با Kotlin کدام محیط‌های توسعه در این صفحه معرفی شده‌اند؟
3. برای ساخت یک برنامهٔ کنسولی و نوشتن آزمون واحد، از کدام مسیرها می‌توانید شروع کنید؟
4. در Kotlin Multiplatform چه گزینه‌هایی برای اشتراک‌گذاری کد بین iOS و Android معرفی شده است؟
5. برای تحلیل داده و برای دریافت کمک در صورت بروز مشکل، چه ابزارها یا منابعی معرفی شده‌اند؟

### سه فعالیت بر اساس همین صفحه

1. یکی از کاربردهای معرفی‌شده، مانند کنسول، بک‌اند یا Android، را انتخاب کنید و نام مسیر یا پیوند پیشنهادی صفحه برای شروع آن را یادداشت کنید.
2. دو گزینهٔ معرفی‌شده برای ساخت برنامهٔ چندسکویی از ابتدا را مقایسه کنید: در هر گزینه چه چیزی به اشتراک گذاشته می‌شود و در کدام گزینه رابط کاربری بومی می‌ماند؟
3. تصور کنید می‌خواهید داده‌ها را تحلیل کنید و سپس نمودار بکشید. با توجه به توضیح‌های صفحه، نام ابزاری را که برای هر کار معرفی شده است بنویسید.

### دو خطای رایج

1. تصور اینکه در برنامهٔ چندسکویی همیشه باید رابط کاربری هم مشترک باشد: صفحه گزینهٔ اشتراک‌گذاری منطق کسب‌وکار با رابط کاربری بومی را نیز معرفی می‌کند.
2. اشتباه گرفتن کاربرد ابزارهای تحلیل داده: صفحه DataFrame را برای تحلیل و دست‌کاری داده و Kandy را برای رسم نمودار معرفی می‌کند.
