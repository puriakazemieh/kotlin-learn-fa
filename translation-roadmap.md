# مسیر ترجمه و یادگیری جامع مستندات Kotlin

> امروز: **شنبه ۱۸ مهر ۱۴۰۵**  
> آغاز برنامه: **شنبهٔ آینده، ۲۵ مهر ۱۴۰۵**  
> آخرین همگام‌سازی: **۱۸ مهر ۱۴۰۵** با commit [`38512ff`](https://github.com/JetBrains/kotlin-web-site/commit/38512ffcb9be58019fdb5d9e6b3c821061445028) مورخ ۱۴ مهر ۱۴۰۵  
> منابع مبنا: [مستندات رسمی Kotlin](https://kotlinlang.org/docs/home.html) و [مخزن kotlin-web-site](https://github.com/JetBrains/kotlin-web-site)

این فایل تنها محل پیگیری پیشرفت است. برای هر فایل رسمی فقط یک checkbox وجود دارد؛ بنابراین پس از پایان ترجمه یا بازبینی، همان checkbox را تیک بزنید.

## وضعیت فعلی

- پیشرفت همگام: **۴ از ۳۰۶ فایل رسمی**
- ترجمهٔ موجود ولی نیازمند تطبیق با متن تازه: **۱۳ فایل** با علامت 🔄
- ترجمهٔ آماده و در انتظار تمرین و مرور یادگیرنده: **۲ فایل**
- ترجمهٔ همگام و در انتظار مطالعهٔ یادگیرنده: **۱ فایل**
- فایل رسمی بدون ترجمه: **۲۸۶ فایل**
- فایل سفارشی خارج از فهرست رسمی: [واژه‌نامهٔ فارسی](glossary-fa.md)

> علامت 🔄 یعنی ترجمه وجود دارد، اما checkbox تا پایان بازبینی تغییرهای متن مبنا خالی می‌ماند.

## نتیجهٔ همگام‌سازی با منبع رسمی

- **43 فایل جدید** اضافه و **212 فایل موجود** به‌روزرسانی شد.
- **24 مسیر قدیمی** برای جلوگیری از حذف ناخواسته نگه داشته شد.
- هیچ فایل `-fa.md` تغییر یا حذف نشد.

<details>
<summary>فایل‌های تازه‌اضافه‌شده</summary>

```text
ai/ai-for-development.md
ai/kotlin-ai-apps-development-overview.md
ai/kotlin-ai-skills.md
ai/kotlin-with-ai.md
ai/spring-ai-guide.md
ai/spring-boot-claude.md
api-references.md
compatibility-guides/compatibility-guide-23.md
compatibility-guides/compatibility-guide-24.md
compiler-plugins/all-open-plugin.md
compiler-plugins/compiler-plugins-overview.md
compiler-plugins/custom-compiler-plugins.md
compiler-plugins/kapt.md
compiler-plugins/lombok.md
compiler-plugins/no-arg-plugin.md
compiler-plugins/power-assert.md
compiler-plugins/sam-with-receiver-plugin.md
compiler/command-line.md
compiler/compiler-execution-strategy.md
compiler/compiler-reference.md
compiler/k2-compiler-migration-guide.md
gsoc-2026.md
js/js-frameworks.md
jvm/jvm-annotation-processors.md
jvm/jvm-code-analysis.md
jvm/jvm-test-maven.md
jvm/server-overview.md
kotlin-lsp.md
ksp/ksp-kapt-migration.md
ksp/ksp-kotlin-model.md
maven/maven-compile-package.md
maven/maven-configure-project.md
maven/maven-kotlin-compiler.md
maven/maven-set-dependencies.md
maven/maven.md
native/native-lib-import-stability.md
unused-return-value-checker.md
uuids.md
web-overview.md
whatsnew/whatsnew23.md
whatsnew/whatsnew2320.md
whatsnew/whatsnew24.md
whatsnew/whatsnew2420.md
```

</details>

<details>
<summary>مسیرهای قدیمی نگه‌داری‌شده</summary>

```text
all-open-plugin.md
ant.md
api-references.topic
command-line.md
compiler-reference.md
js-frameworks.md
jvm/jvm-spring-boot-restful.md
k2-compiler-migration-guide.md
kapt.md
kotlin-ai-apps-development-overview.md
kotlin-mascot.md
ksp/ksp-additional-details.md
ksp/ksp-examples.md
ksp/ksp-faq.md
lombok.md
maven.md
multiplatform.topic
native/native-c-interop-stability.md
no-arg-plugin.md
power-assert.md
sam-with-receiver-plugin.md
serialization.md
server-overview.md
spring-ai-guide.md
```

</details>

## برنامهٔ ۱۲ شنبهٔ نخست

امروز، ۱۸ مهر، فقط برای آماده‌سازی مسیر و همگام‌سازی در نظر گرفته شده است. ترجمه از شنبهٔ آینده آغاز می‌شود.

| تاریخ شمسی | فایل مبنا | خروجی مورد انتظار | هدف یادگیری |
|---|---|---|---|
| ۲۵ مهر ۱۴۰۵ | [`getting-started.md`](getting-started.md) | `getting-started-fa.md` | آشنایی با مسیر شروع Kotlin |
| ۲ آبان ۱۴۰۵ | [`tour/kotlin-tour-welcome.md`](tour/kotlin-tour-welcome.md) | `tour/kotlin-tour-welcome-fa.md` | نمای کلی تور Kotlin |
| ۹ آبان ۱۴۰۵ | [`tour/kotlin-tour-hello-world.md`](tour/kotlin-tour-hello-world.md) | `tour/kotlin-tour-hello-world-fa.md` | اولین برنامه و ساختار پایه |
| ۱۶ آبان ۱۴۰۵ | [`tour/kotlin-tour-basic-types.md`](tour/kotlin-tour-basic-types.md) | `tour/kotlin-tour-basic-types-fa.md` | مرور نوع‌های پایه |
| ۲۳ آبان ۱۴۰۵ | [`tour/kotlin-tour-collections.md`](tour/kotlin-tour-collections.md) | `tour/kotlin-tour-collections-fa.md` | آشنایی اولیه با مجموعه‌ها |
| ۳۰ آبان ۱۴۰۵ | [`tour/kotlin-tour-control-flow.md`](tour/kotlin-tour-control-flow.md) | `tour/kotlin-tour-control-flow-fa.md` | کنترل جریان |
| ۷ آذر ۱۴۰۵ | [`tour/kotlin-tour-functions.md`](tour/kotlin-tour-functions.md) | `tour/kotlin-tour-functions-fa.md` | توابع و لمبداهای مقدماتی |
| ۱۴ آذر ۱۴۰۵ | [`tour/kotlin-tour-classes.md`](tour/kotlin-tour-classes.md) | `tour/kotlin-tour-classes-fa.md` | کلاس‌ها و اشیاء |
| ۲۱ آذر ۱۴۰۵ | [`tour/kotlin-tour-null-safety.md`](tour/kotlin-tour-null-safety.md) | `tour/kotlin-tour-null-safety-fa.md` | ایمنی در برابر null |
| ۲۸ آذر ۱۴۰۵ | [`tour/kotlin-tour-intermediate-extension-functions.md`](tour/kotlin-tour-intermediate-extension-functions.md) | `tour/kotlin-tour-intermediate-extension-functions-fa.md` | extension functionها |
| ۵ دی ۱۴۰۵ | [`tour/kotlin-tour-intermediate-scope-functions.md`](tour/kotlin-tour-intermediate-scope-functions.md) | `tour/kotlin-tour-intermediate-scope-functions-fa.md` | scope functionها |
| ۱۲ دی ۱۴۰۵ | [`tour/kotlin-tour-intermediate-lambdas-receiver.md`](tour/kotlin-tour-intermediate-lambdas-receiver.md) | `tour/kotlin-tour-intermediate-lambdas-receiver-fa.md` | لمبداهای دارای receiver |

این جدول دقیقاً از ۱۲ checkbox نخست مسیر یادگیری ساخته شده است. پس از ۱۲ دی، از ردیف بعدی چک‌لیست ادامه دهید. `home.topic` صفحهٔ ساختاری سایت است و پس از پایان تور ترجمه می‌شود، نه به‌عنوان نخستین درس.

## روش تیک‌زدن و تعریف «تمام‌شده»

- شروع‌نشده یا ناقص: `- [ ]`
- ترجمه و کنترل کیفیت کامل: `- [x]`
- در Obsidian می‌توانید مستقیماً روی checkbox کلیک کنید.
- checkbox را فقط وقتی تیک بزنید که ترجمه کامل باشد، کد و لینک‌ها حفظ شده باشند، حداقل سه تمرین متناسب با محتوای صفحه انجام داده باشید و بتوانید مفهوم را بدون نگاه‌کردن توضیح دهید. برای صفحهٔ معرفیِ بدون مثال کد، به‌جای تمرین کدنویسی فعالیت‌های مرتبط با همان صفحه انجام دهید.
- checkbox دیگری برای همان فایل در این سند وجود ندارد؛ جدول برنامه فقط زمان‌بندی است و وضعیت را نگه نمی‌دارد.

## الگوی ثابت هر جلسهٔ شنبه

1. **۱۵ دقیقه — مرور:** هدف صفحه، پیش‌نیازها و واژه‌های تازه را مشخص کنید.
2. **۶۰ تا ۹۰ دقیقه — ترجمه:** ساختار، لینک‌ها، کدها و هشدارها را بدون تغییر معنا حفظ کنید.
3. **۳۰ تا ۴۵ دقیقه — تمرین:** دست‌کم سه تمرین متناسب با مطالب صفحه انجام دهید؛ اگر صفحه مثال کد دارد، مثال‌ها را اجرا یا از نو تایپ کنید و در صورت امکان یک مثال مرزی بسازید.
4. **۱۵ دقیقه — بازیابی فعال:** بدون نگاه‌کردن، مطلب را در پنج بند توضیح دهید و پنج پرسش بسازید.
5. **۱۰ دقیقه — کنترل کیفیت و تیک:** فایل، لینک‌ها، اصطلاحات و checkbox همان مورد را بررسی کنید.

## قرارداد ترجمه

- خروجی در همان پوشه و با `-fa` پیش از پسوند ساخته شود؛ مثال: `classes.md` → `classes-fa.md`.
- keywordها و شناسه‌های Kotlin مثل `val`، `when` و `suspend` ترجمه نشوند.
- اصطلاح تخصصی در نخستین کاربرد به‌صورت «معادل فارسی (English term)» نوشته شود و سپس معادل ثابتی داشته باشد.
- کد، خروجی، نام API و مقصد پیوندها حفظ شوند. ساختار و متادیتای متن مبنا را تا جای ممکن حفظ کنید، اما قالب‌های مخصوص Writerside را برای نمایش درست در Obsidian به معادل خوانا تبدیل کنید؛ معنا و محتوای هیچ بخشی نباید از دست برود.
- هیچ بخش، مثال یا هشدار خلاصه یا حذف نشود.
- هر ترجمه باید در حالت خواندن و ویرایش Obsidian خوانا باشد: متن فارسی راست‌به‌چپ و کدها و شناسه‌های انگلیسی چپ‌به‌راست باشند. ویژگی `cssclasses` را در front matter به‌صورت فهرست اضافه یا با ویژگی موجود ادغام کنید و مقدار `persian-rtl` را در آن بگذارید؛ تنظیم‌های لازم در snippet فعال `.obsidian/snippets/rtl.css` همین vault قرار دارد.
- تب‌های Writerside مانند `<tabs>` و `<tab>` را به عنوان‌ها و بخش‌های معمول Markdown تبدیل کنید؛ هر تب و محتوایش باید باقی بماند. از قرار دادن Markdown داخل تگ‌های HTML ناسازگار با Obsidian خودداری کنید.
- عنوان‌ها، لینک‌ها، تصویرها، هشدارها و فهرست‌ها را با قالب قابل‌نمایش در Obsidian بنویسید. شناسه‌های اختصاصی Writerside مانند `{id="..."}` را به متن نمایشی اضافه نکنید؛ لینک به بخش‌های ترجمه را با عنوان واقعی آن در Obsidian تنظیم کنید و در صورت نبود مقصد فارسی به بخش متن رسمی پیوند دهید.
- متغیرهای سایت مانند `%kotlinVersion%` را که در Obsidian پردازش نمی‌شوند، خام در متن نمایشی نگذارید؛ به صفحهٔ رسمی مناسب برای اطلاعات به‌روز پیوند دهید یا مقدار معتبر را با تاریخ بررسی بنویسید. دارایی‌های محلی موردنیاز را نیز بررسی کنید.
- قبل از تحویل، نمایش عنوان‌ها، فهرست‌ها، لینک‌ها، تصاویر، متن ترکیبی فارسی و انگلیسی، و جهت بلوک‌های کد را در حالت خواندن و ویرایش بررسی کنید. اگر امکان بررسی در خود Obsidian نبود، محدودیت را گزارش کنید.

## پرامپت آمادهٔ ترجمهٔ یک فایل

فقط مقدار `{{FILE_PATH}}` را با نام یا مسیر فایل موردنظر، مثلاً `typecasts.md`، جایگزین کنید و کل متن زیر را بدهید:

```text
نام/مسیر فایل مبنا: {{FILE_PATH}}

این فایل از مستندات رسمی Kotlin است. فایل مبنا را کامل بخوان و بدون تغییر دادن آن، ترجمهٔ فارسی را در همان پوشه بساز. نام فایل خروجی را با افزودن -fa پیش از پسوند تعیین کن؛ برای مثال typecasts.md باید به typecasts-fa.md تبدیل شود.

الزامات ترجمه:
1. متن را کامل، دقیق و روان ترجمه کن و هیچ بخش، هشدار یا مثالی را خلاصه یا حذف نکن.
2. محتوای کامل، کدها، خروجی‌ها، نام APIها و keywordهای Kotlin را حفظ کن و قالب مخصوص Writerside را مطابق قرارداد ترجمه به Markdown خوانا در Obsidian تبدیل کن. مقصد لینک‌ها و محتوای هشدارها را حفظ کن؛ لینک‌های بخش‌ها را با عنوان‌های واقعی Obsidian یا متن رسمی هماهنگ کن.
3. اصطلاح تخصصی را در اولین کاربرد به شکل «معادل فارسی (English term)» بیاور و سپس از یک معادل ثابت استفاده کن.
4. لینک داخلی را فقط وقتی به نسخهٔ -fa تغییر بده که آن فایل فارسی واقعاً وجود داشته باشد؛ در غیر این صورت لینک متن رسمی را حفظ کن.
5. در پایان ترجمه، پنج پرسش بازیابی فعال، سه تمرین و دو خطای رایج مرتبط با مطالب همان صفحه را در بخش «تمرین و مرور» اضافه کن. تمرین کدنویسی فقط بر اساس مفاهیم آموزش‌داده‌شده در همان صفحه باشد؛ برای صفحهٔ معرفی بدون مثال کد، به‌جای آن فعالیت‌های مرتبط با اطلاعات همان صفحه بنویس. برای پاسخ به پرسش‌ها و تمرین‌ها به مطالب آموزش‌داده‌نشده در صفحه نیاز نباشد.
6. `persian-rtl` را به `cssclasses` فایل اضافه کن. کامل‌بودن بخش‌ها، بسته‌شدن code fenceها، سالم‌بودن لینک‌های محلی و نمایش فارسی، انگلیسی، فهرست‌ها، تصاویر و کد را در حالت خواندن و ویرایش Obsidian بررسی کن؛ اگر بررسی در خود برنامه ممکن نبود، آن را گزارش کن.
7. فقط پس از کامل‌شدن ترجمه و کنترل کیفیت، checkbox مربوط به همین فایل را در translation-roadmap.md از [ ] به [x] تغییر بده. اگر کار ناقص است یا نیاز به تصمیم من دارد، checkbox را تیک نزن.
8. پس از تیک‌زدن، شمارنده‌های بخش «وضعیت فعلی» را هم سازگار به‌روز کن: «پیشرفت همگام» یک واحد زیاد شود؛ اگر ترجمه تازه ساخته‌ای «بدون ترجمه» یک واحد کم شود، و اگر مورد 🔄 را بازبینی کرده‌ای «نیازمند تطبیق» یک واحد کم شود.
```

## چک‌لیست کامل بر اساس ترتیب یادگیری

ساختار هر ردیف: checkbox → فایل خروجی فارسی → متن مبنا → عنوان. کافی است پس از پایان کار `[ ]` را به `[x]` تبدیل کنید. مراحل صفر تا هفت مسیر عمومی‌اند؛ مراحل هشت تا دوازده شاخه‌های تخصصی هستند.

### مرحلهٔ صفر: آشنایی و تور کاتلین (19 فایل)

این مرحله دروازهٔ مسیر یادگیری است و جدول ۱۲ هفتهٔ نخست نیز مستقیماً از همین ترتیب پیروی می‌کند.

- [x] [`getting-started-fa.md`](getting-started-fa.md) ← [`getting-started.md`](getting-started.md) — Get started
- [x] [`tour/kotlin-tour-welcome-fa.md`](tour/kotlin-tour-welcome-fa.md) ← [`tour/kotlin-tour-welcome.md`](tour/kotlin-tour-welcome.md) — Kotlin tour overview
- [ ] [`tour/kotlin-tour-hello-world-fa.md`](tour/kotlin-tour-hello-world-fa.md) ← [`tour/kotlin-tour-hello-world.md`](tour/kotlin-tour-hello-world.md) — kotlin-tour-hello-world (ترجمه آماده؛ در انتظار تمرین و مرور)
- [ ] [`tour/kotlin-tour-basic-types-fa.md`](tour/kotlin-tour-basic-types-fa.md) ← [`tour/kotlin-tour-basic-types.md`](tour/kotlin-tour-basic-types.md) — kotlin-tour-basic-types (ترجمه آماده؛ در انتظار تمرین و مرور)
- [ ] `tour/kotlin-tour-collections-fa.md` ← [`tour/kotlin-tour-collections.md`](tour/kotlin-tour-collections.md) — kotlin-tour-collections
- [ ] `tour/kotlin-tour-control-flow-fa.md` ← [`tour/kotlin-tour-control-flow.md`](tour/kotlin-tour-control-flow.md) — kotlin-tour-control-flow
- [ ] `tour/kotlin-tour-functions-fa.md` ← [`tour/kotlin-tour-functions.md`](tour/kotlin-tour-functions.md) — kotlin-tour-functions
- [ ] `tour/kotlin-tour-classes-fa.md` ← [`tour/kotlin-tour-classes.md`](tour/kotlin-tour-classes.md) — kotlin-tour-classes
- [ ] `tour/kotlin-tour-null-safety-fa.md` ← [`tour/kotlin-tour-null-safety.md`](tour/kotlin-tour-null-safety.md) — kotlin-tour-null-safety
- [ ] `tour/kotlin-tour-intermediate-extension-functions-fa.md` ← [`tour/kotlin-tour-intermediate-extension-functions.md`](tour/kotlin-tour-intermediate-extension-functions.md) — kotlin-tour-intermediate-extension-functions
- [ ] `tour/kotlin-tour-intermediate-scope-functions-fa.md` ← [`tour/kotlin-tour-intermediate-scope-functions.md`](tour/kotlin-tour-intermediate-scope-functions.md) — kotlin-tour-intermediate-scope-functions
- [ ] `tour/kotlin-tour-intermediate-lambdas-receiver-fa.md` ← [`tour/kotlin-tour-intermediate-lambdas-receiver.md`](tour/kotlin-tour-intermediate-lambdas-receiver.md) — kotlin-tour-intermediate-lambdas-receiver
- [ ] `tour/kotlin-tour-intermediate-classes-interfaces-fa.md` ← [`tour/kotlin-tour-intermediate-classes-interfaces.md`](tour/kotlin-tour-intermediate-classes-interfaces.md) — kotlin-tour-intermediate-classes-interfaces
- [ ] `tour/kotlin-tour-intermediate-objects-fa.md` ← [`tour/kotlin-tour-intermediate-objects.md`](tour/kotlin-tour-intermediate-objects.md) — kotlin-tour-intermediate-objects
- [ ] `tour/kotlin-tour-intermediate-open-special-classes-fa.md` ← [`tour/kotlin-tour-intermediate-open-special-classes.md`](tour/kotlin-tour-intermediate-open-special-classes.md) — kotlin-tour-intermediate-open-special-classes
- [ ] `tour/kotlin-tour-intermediate-properties-fa.md` ← [`tour/kotlin-tour-intermediate-properties.md`](tour/kotlin-tour-intermediate-properties.md) — kotlin-tour-intermediate-properties
- [ ] `tour/kotlin-tour-intermediate-null-safety-fa.md` ← [`tour/kotlin-tour-intermediate-null-safety.md`](tour/kotlin-tour-intermediate-null-safety.md) — kotlin-tour-intermediate-null-safety
- [ ] `tour/kotlin-tour-intermediate-libraries-and-apis-fa.md` ← [`tour/kotlin-tour-intermediate-libraries-and-apis.md`](tour/kotlin-tour-intermediate-libraries-and-apis.md) — kotlin-tour-intermediate-libraries-and-apis
- [ ] `home-fa.topic` ← [`home.topic`](home.topic) — Home (صفحهٔ ساختاری سایت)

### مرحلهٔ یک: مبانی زبان، نوع‌ها و کنترل جریان (22 فایل)

پایهٔ اجباری برای تمام شاخه‌های بعدی.

- [ ] [`basic-syntax-fa.md`](basic-syntax-fa.md) ← [`basic-syntax.md`](basic-syntax.md) — Overview 🔄
- [ ] [`keyword-reference-fa.md`](keyword-reference-fa.md) ← [`keyword-reference.md`](keyword-reference.md) — keyword-reference 🔄
- [ ] [`packages-fa.md`](packages-fa.md) ← [`packages.md`](packages.md) — packages 🔄
- [ ] [`annotations-fa.md`](annotations-fa.md) ← [`annotations.md`](annotations.md) — annotations 🔄
- [ ] [`visibility-modifiers-fa.md`](visibility-modifiers-fa.md) ← [`visibility-modifiers.md`](visibility-modifiers.md) — visibility-modifiers 🔄
- [ ] [`coding-conventions-fa.md`](coding-conventions-fa.md) ← [`coding-conventions.md`](coding-conventions.md) — coding-conventions 🔄
- [ ] [`idioms-fa.md`](idioms-fa.md) ← [`idioms.md`](idioms.md) — idioms
- [ ] [`types-overview-fa.md`](types-overview-fa.md) ← [`types-overview.md`](types-overview.md) — Overview 🔄
- [ ] [`numbers-fa.md`](numbers-fa.md) ← [`numbers.md`](numbers.md) — numbers 🔄
- [ ] [`unsigned-integer-types-fa.md`](unsigned-integer-types-fa.md) ← [`unsigned-integer-types.md`](unsigned-integer-types.md) — unsigned-integer-types 🔄
- [ ] [`booleans-fa.md`](booleans-fa.md) ← [`booleans.md`](booleans.md) — booleans 🔄
- [ ] [`characters-fa.md`](characters-fa.md) ← [`characters.md`](characters.md) — characters 🔄
- [ ] [`strings-fa.md`](strings-fa.md) ← [`strings.md`](strings.md) — strings (ترجمه همگام است؛ پس از پایان تور مقدماتی بخوانید)
- [ ] [`arrays-fa.md`](arrays-fa.md) ← [`arrays.md`](arrays.md) — arrays 🔄
- [ ] `typecasts-fa.md` ← [`typecasts.md`](typecasts.md) — typecasts
- [ ] `type-aliases-fa.md` ← [`type-aliases.md`](type-aliases.md) — type-aliases
- [ ] [`control-flow-fa.md`](control-flow-fa.md) ← [`control-flow.md`](control-flow.md) — control-flow 🔄
- [ ] [`returns-fa.md`](returns-fa.md) ← [`returns.md`](returns.md) — returns
- [ ] `exceptions-fa.md` ← [`exceptions.md`](exceptions.md) — Exception handling
- [ ] `null-safety-fa.md` ← [`null-safety.md`](null-safety.md) — null-safety
- [ ] `equality-fa.md` ← [`equality.md`](equality.md) — equality
- [ ] `standard-input-fa.md` ← [`standard-input.md`](standard-input.md) — standard-input

### مرحلهٔ دو: توابع، لمبداها و DSLها (9 فایل)

پس از نوع‌ها و کنترل جریان مطالعه شود.

- [ ] `functions-fa.md` ← [`functions.md`](functions.md) — functions
- [ ] `lambdas-fa.md` ← [`lambdas.md`](lambdas.md) — Lambdas
- [ ] `scope-functions-fa.md` ← [`scope-functions.md`](scope-functions.md) — scope-functions
- [ ] `type-safe-builders-fa.md` ← [`type-safe-builders.md`](type-safe-builders.md) — type-safe-builders
- [ ] `using-builders-with-builder-inference-fa.md` ← [`using-builders-with-builder-inference.md`](using-builders-with-builder-inference.md) — using-builders-with-builder-inference
- [ ] `context-parameters-fa.md` ← [`context-parameters.md`](context-parameters.md) — context-parameters
- [ ] `inline-functions-fa.md` ← [`inline-functions.md`](inline-functions.md) — inline-functions
- [ ] `operator-overloading-fa.md` ← [`operator-overloading.md`](operator-overloading.md) — operator-overloading
- [ ] `unused-return-value-checker-fa.md` ← [`unused-return-value-checker.md`](unused-return-value-checker.md) — unused-return-value-checker

### مرحلهٔ سه: کلاس‌ها، شیءگرایی و جنریک‌ها (18 فایل)

مدل شیءگرایی Kotlin و قابلیت‌های پیشرفتهٔ نوع‌ها.

- [ ] `classes-fa.md` ← [`classes.md`](classes.md) — classes
- [ ] `properties-fa.md` ← [`properties.md`](properties.md) — properties
- [ ] `data-classes-fa.md` ← [`data-classes.md`](data-classes.md) — data-classes
- [ ] `extensions-fa.md` ← [`extensions.md`](extensions.md) — extensions
- [ ] `interfaces-fa.md` ← [`interfaces.md`](interfaces.md) — interfaces
- [ ] `delegation-fa.md` ← [`delegation.md`](delegation.md) — delegation
- [ ] `delegated-properties-fa.md` ← [`delegated-properties.md`](delegated-properties.md) — delegated-properties
- [ ] `inheritance-fa.md` ← [`inheritance.md`](inheritance.md) — inheritance
- [ ] `object-declarations-fa.md` ← [`object-declarations.md`](object-declarations.md) — object-declarations
- [ ] `this-expressions-fa.md` ← [`this-expressions.md`](this-expressions.md) — this-expressions
- [ ] `sealed-classes-fa.md` ← [`sealed-classes.md`](sealed-classes.md) — sealed-classes
- [ ] `enum-classes-fa.md` ← [`enum-classes.md`](enum-classes.md) — enum-classes
- [ ] `inline-classes-fa.md` ← [`inline-classes.md`](inline-classes.md) — inline-classes
- [ ] `nested-classes-fa.md` ← [`nested-classes.md`](nested-classes.md) — nested-classes
- [ ] `fun-interfaces-fa.md` ← [`fun-interfaces.md`](fun-interfaces.md) — fun-interfaces
- [ ] `generics-fa.md` ← [`generics.md`](generics.md) — Generics
- [ ] `reflection-fa.md` ← [`reflection.md`](reflection.md) — reflection
- [ ] `destructuring-declarations-fa.md` ← [`destructuring-declarations.md`](destructuring-declarations.md) — destructuring-declarations

### مرحلهٔ چهار: کتابخانهٔ استاندارد و مجموعه‌ها (22 فایل)

کار روزمره با collectionها، sequenceها، ورودی و ابزارهای استاندارد.

- [ ] `collections-overview-fa.md` ← [`collections-overview.md`](collections-overview.md) — Overview
- [ ] `constructing-collections-fa.md` ← [`constructing-collections.md`](constructing-collections.md) — Create
- [ ] `iterators-fa.md` ← [`iterators.md`](iterators.md) — Traverse
- [ ] `collection-ordering-fa.md` ← [`collection-ordering.md`](collection-ordering.md) — Order
- [ ] `collection-grouping-fa.md` ← [`collection-grouping.md`](collection-grouping.md) — Group
- [ ] `collection-transformations-fa.md` ← [`collection-transformations.md`](collection-transformations.md) — Transform
- [ ] `collection-filtering-fa.md` ← [`collection-filtering.md`](collection-filtering.md) — Filter
- [ ] `collection-parts-fa.md` ← [`collection-parts.md`](collection-parts.md) — collection-parts
- [ ] `collection-elements-fa.md` ← [`collection-elements.md`](collection-elements.md) — collection-elements
- [ ] `collection-operations-fa.md` ← [`collection-operations.md`](collection-operations.md) — Operations overview
- [ ] `collection-aggregate-fa.md` ← [`collection-aggregate.md`](collection-aggregate.md) — collection-aggregate
- [ ] `collection-write-fa.md` ← [`collection-write.md`](collection-write.md) — Write operations
- [ ] `list-operations-fa.md` ← [`list-operations.md`](list-operations.md) — list-operations
- [ ] `set-operations-fa.md` ← [`set-operations.md`](set-operations.md) — set-operations
- [ ] `map-operations-fa.md` ← [`map-operations.md`](map-operations.md) — map-operations
- [ ] `collection-plus-minus-fa.md` ← [`collection-plus-minus.md`](collection-plus-minus.md) — collection-plus-minus
- [ ] `sequences-fa.md` ← [`sequences.md`](sequences.md) — sequences
- [ ] `ranges-fa.md` ← [`ranges.md`](ranges.md) — ranges
- [ ] `read-standard-input-fa.md` ← [`read-standard-input.md`](read-standard-input.md) — read-standard-input
- [ ] `opt-in-requirements-fa.md` ← [`opt-in-requirements.md`](opt-in-requirements.md) — opt-in-requirements
- [ ] `time-measurement-fa.md` ← [`time-measurement.md`](time-measurement.md) — time-measurement
- [ ] `uuids-fa.md` ← [`uuids.md`](uuids.md) — uuids

### مرحلهٔ پنج: برنامه‌نویسی ناهمگام و Coroutine (2 فایل)

بعد از تسلط بر توابع و لمبداها.

- [ ] `async-programming-fa.md` ← [`async-programming.md`](async-programming.md) — Asynchronous programming
- [ ] `coroutines-overview-fa.md` ← [`coroutines-overview.md`](coroutines-overview.md) — coroutines-overview

### مرحلهٔ شش: JVM، Java interop و Backend (21 فایل)

مسیر کاربردی برای توسعهٔ JVM و سرور.

- [ ] `jvm/server-overview-fa.md` ← [`jvm/server-overview.md`](jvm/server-overview.md) — Overview
- [ ] `jvm/mixing-java-kotlin-intellij-fa.md` ← [`jvm/mixing-java-kotlin-intellij.md`](jvm/mixing-java-kotlin-intellij.md) — Add Kotlin to a Java project
- [ ] `jvm/jvm-test-using-junit-fa.md` ← [`jvm/jvm-test-using-junit.md`](jvm/jvm-test-using-junit.md) — Test Java code with Kotlin
- [ ] `jvm/jvm-test-maven-fa.md` ← [`jvm/jvm-test-maven.md`](jvm/jvm-test-maven.md) — Testing with Maven
- [ ] `jvm/jvm-annotation-processors-fa.md` ← [`jvm/jvm-annotation-processors.md`](jvm/jvm-annotation-processors.md) — Use annotation processors
- [ ] `jvm/jvm-code-analysis-fa.md` ← [`jvm/jvm-code-analysis.md`](jvm/jvm-code-analysis.md) — Use code analysis tools
- [ ] `jvm/jvm-get-started-spring-boot-fa.md` ← [`jvm/jvm-get-started-spring-boot.md`](jvm/jvm-get-started-spring-boot.md) — jvm-get-started-spring-boot
- [ ] `jvm/jvm-create-project-with-spring-boot-fa.md` ← [`jvm/jvm-create-project-with-spring-boot.md`](jvm/jvm-create-project-with-spring-boot.md) — Create a Spring Boot project
- [ ] `jvm/jvm-spring-boot-add-data-class-fa.md` ← [`jvm/jvm-spring-boot-add-data-class.md`](jvm/jvm-spring-boot-add-data-class.md) — Upgrade your project with data classes
- [ ] `jvm/jvm-spring-boot-add-db-support-fa.md` ← [`jvm/jvm-spring-boot-add-db-support.md`](jvm/jvm-spring-boot-add-db-support.md) — jvm-spring-boot-add-db-support
- [ ] `jvm/jvm-spring-boot-using-crudrepository-fa.md` ← [`jvm/jvm-spring-boot-using-crudrepository.md`](jvm/jvm-spring-boot-using-crudrepository.md) — Use Spring Data CrudRepository
- [ ] `jvm/comparison-to-java-fa.md` ← [`jvm/comparison-to-java.md`](jvm/comparison-to-java.md) — comparison-to-java
- [ ] `jvm/java-interop-fa.md` ← [`jvm/java-interop.md`](jvm/java-interop.md) — java-interop
- [ ] `jvm/java-to-kotlin-interop-fa.md` ← [`jvm/java-to-kotlin-interop.md`](jvm/java-to-kotlin-interop.md) — java-to-kotlin-interop
- [ ] `jvm/jvm-records-fa.md` ← [`jvm/jvm-records.md`](jvm/jvm-records.md) — jvm-records
- [ ] `jvm/java-to-kotlin-idioms-strings-fa.md` ← [`jvm/java-to-kotlin-idioms-strings.md`](jvm/java-to-kotlin-idioms-strings.md) — Strings
- [ ] `jvm/java-to-kotlin-collections-guide-fa.md` ← [`jvm/java-to-kotlin-collections-guide.md`](jvm/java-to-kotlin-collections-guide.md) — Collections
- [ ] `jvm/java-to-kotlin-nullability-guide-fa.md` ← [`jvm/java-to-kotlin-nullability-guide.md`](jvm/java-to-kotlin-nullability-guide.md) — Nullability
- [ ] `metadata-jvm-fa.md` ← [`metadata-jvm.md`](metadata-jvm.md) — Kotlin Metadata JVM (kotlin-metadata-jvm)
- [ ] `jvm/jvm-get-started-fa.md` ← [`jvm/jvm-get-started.md`](jvm/jvm-get-started.md) — Create a console app
- [ ] `jvm/jvm-spring-boot-collections-fa.md` ← [`jvm/jvm-spring-boot-collections.md`](jvm/jvm-spring-boot-collections.md) — jvm-spring-boot-collections

### مرحلهٔ هفت: Gradle، Maven، کامپایلر و افزونه‌ها (39 فایل)

پس از تجربهٔ ساخت حداقل یک پروژهٔ Kotlin مطالعه شود.

- [ ] `gradle/gradle-fa.md` ← [`gradle/gradle.md`](gradle/gradle.md) — Overview
- [ ] `gradle/get-started-with-jvm-gradle-project-fa.md` ← [`gradle/get-started-with-jvm-gradle-project.md`](gradle/get-started-with-jvm-gradle-project.md) — Get started with Gradle – tutorial
- [ ] `gradle/gradle-configure-project-fa.md` ← [`gradle/gradle-configure-project.md`](gradle/gradle-configure-project.md) — gradle-configure-project
- [ ] `gradle/gradle-best-practices-fa.md` ← [`gradle/gradle-best-practices.md`](gradle/gradle-best-practices.md) — gradle-best-practices
- [ ] `gradle/gradle-compiler-options-fa.md` ← [`gradle/gradle-compiler-options.md`](gradle/gradle-compiler-options.md) — Compiler options in KGP
- [ ] `gradle/gradle-compilation-and-caches-fa.md` ← [`gradle/gradle-compilation-and-caches.md`](gradle/gradle-compilation-and-caches.md) — Compilation and caches in KGP
- [ ] `gradle/gradle-binary-compatibility-validation-fa.md` ← [`gradle/gradle-binary-compatibility-validation.md`](gradle/gradle-binary-compatibility-validation.md) — Binary compatibility validation in KGP
- [ ] `gradle/gradle-plugin-variants-fa.md` ← [`gradle/gradle-plugin-variants.md`](gradle/gradle-plugin-variants.md) — gradle-plugin-variants
- [ ] `maven/maven-fa.md` ← [`maven/maven.md`](maven/maven.md) — Overview
- [ ] `maven/maven-configure-project-fa.md` ← [`maven/maven-configure-project.md`](maven/maven-configure-project.md) — Configure project
- [ ] `maven/maven-set-dependencies-fa.md` ← [`maven/maven-set-dependencies.md`](maven/maven-set-dependencies.md) — Set repositories and dependencies
- [ ] `maven/maven-kotlin-compiler-fa.md` ← [`maven/maven-kotlin-compiler.md`](maven/maven-kotlin-compiler.md) — Configure Kotlin compiler
- [ ] `maven/maven-compile-package-fa.md` ← [`maven/maven-compile-package.md`](maven/maven-compile-package.md) — Package your project
- [ ] `build-tools-api-fa.md` ← [`build-tools-api.md`](build-tools-api.md) — build-tools-api
- [ ] `kotlin-daemon-fa.md` ← [`kotlin-daemon.md`](kotlin-daemon.md) — kotlin-daemon
- [ ] `compiler/k2-compiler-migration-guide-fa.md` ← [`compiler/k2-compiler-migration-guide.md`](compiler/k2-compiler-migration-guide.md) — k2-compiler-migration-guide
- [ ] `compiler/command-line-fa.md` ← [`compiler/command-line.md`](compiler/command-line.md) — Command-line compiler
- [ ] `compiler/compiler-reference-fa.md` ← [`compiler/compiler-reference.md`](compiler/compiler-reference.md) — Compiler options
- [ ] `compiler/compiler-execution-strategy-fa.md` ← [`compiler/compiler-execution-strategy.md`](compiler/compiler-execution-strategy.md) — compiler-execution-strategy
- [ ] `compiler-plugins/compiler-plugins-overview-fa.md` ← [`compiler-plugins/compiler-plugins-overview.md`](compiler-plugins/compiler-plugins-overview.md) — Overview
- [ ] `compiler-plugins/all-open-plugin-fa.md` ← [`compiler-plugins/all-open-plugin.md`](compiler-plugins/all-open-plugin.md) — All-open
- [ ] `compiler-plugins/kapt-fa.md` ← [`compiler-plugins/kapt.md`](compiler-plugins/kapt.md) — kapt
- [ ] `compiler-plugins/lombok-fa.md` ← [`compiler-plugins/lombok.md`](compiler-plugins/lombok.md) — Lombok
- [ ] `compiler-plugins/no-arg-plugin-fa.md` ← [`compiler-plugins/no-arg-plugin.md`](compiler-plugins/no-arg-plugin.md) — No-arg
- [ ] `compiler-plugins/power-assert-fa.md` ← [`compiler-plugins/power-assert.md`](compiler-plugins/power-assert.md) — Power-assert
- [ ] `compiler-plugins/sam-with-receiver-plugin-fa.md` ← [`compiler-plugins/sam-with-receiver-plugin.md`](compiler-plugins/sam-with-receiver-plugin.md) — SAM with receiver
- [ ] `compiler-plugins/custom-compiler-plugins-fa.md` ← [`compiler-plugins/custom-compiler-plugins.md`](compiler-plugins/custom-compiler-plugins.md) — custom-compiler-plugins
- [ ] `compose-compiler-migration-guide-fa.md` ← [`compose-compiler-migration-guide.md`](compose-compiler-migration-guide.md) — Compiler migration guide
- [ ] `compose-compiler-options-fa.md` ← [`compose-compiler-options.md`](compose-compiler-options.md) — Compiler options
- [ ] `ksp/ksp-overview-fa.md` ← [`ksp/ksp-overview.md`](ksp/ksp-overview.md) — KSP overview
- [ ] `ksp/ksp-quickstart-fa.md` ← [`ksp/ksp-quickstart.md`](ksp/ksp-quickstart.md) — Getting started
- [ ] `ksp/ksp-multiplatform-fa.md` ← [`ksp/ksp-multiplatform.md`](ksp/ksp-multiplatform.md) — ksp-multiplatform
- [ ] `ksp/ksp-kapt-migration-fa.md` ← [`ksp/ksp-kapt-migration.md`](ksp/ksp-kapt-migration.md) — ksp-kapt-migration
- [ ] `ksp/ksp-incremental-fa.md` ← [`ksp/ksp-incremental.md`](ksp/ksp-incremental.md) — ksp-incremental
- [ ] `ksp/ksp-multi-round-fa.md` ← [`ksp/ksp-multi-round.md`](ksp/ksp-multi-round.md) — ksp-multi-round
- [ ] `ksp/ksp-reference-fa.md` ← [`ksp/ksp-reference.md`](ksp/ksp-reference.md) — Reference for Java annotation processor authors
- [ ] `ksp/ksp-kotlin-model-fa.md` ← [`ksp/ksp-kotlin-model.md`](ksp/ksp-kotlin-model.md) — ksp-kotlin-model
- [ ] `ksp/ksp-command-line-fa.md` ← [`ksp/ksp-command-line.md`](ksp/ksp-command-line.md) — KSP from the command line
- [ ] `ksp/ksp-why-ksp-fa.md` ← [`ksp/ksp-why-ksp.md`](ksp/ksp-why-ksp.md) — ksp-why-ksp

### مرحلهٔ هشت: توسعهٔ وب، Kotlin/JS و Wasm (26 فایل)

شاخهٔ تخصصی؛ پس از مراحل پایه.

- [ ] `web-overview-fa.md` ← [`web-overview.md`](web-overview.md) — web-overview
- [ ] `js/js-overview-fa.md` ← [`js/js-overview.md`](js/js-overview.md) — Overview
- [ ] `js/js-get-started-fa.md` ← [`js/js-get-started.md`](js/js-get-started.md) — js-get-started
- [ ] `js/js-project-setup-fa.md` ← [`js/js-project-setup.md`](js/js-project-setup.md) — js-project-setup
- [ ] `js/running-kotlin-js-fa.md` ← [`js/running-kotlin-js.md`](js/running-kotlin-js.md) — running-kotlin-js
- [ ] `js/dev-server-continuous-compilation-fa.md` ← [`js/dev-server-continuous-compilation.md`](js/dev-server-continuous-compilation.md) — dev-server-continuous-compilation
- [ ] `js/js-debugging-fa.md` ← [`js/js-debugging.md`](js/js-debugging.md) — js-debugging
- [ ] `js/js-running-tests-fa.md` ← [`js/js-running-tests.md`](js/js-running-tests.md) — js-running-tests
- [ ] `js/js-frameworks-fa.md` ← [`js/js-frameworks.md`](js/js-frameworks.md) — js-frameworks
- [ ] `js/js-ir-compiler-fa.md` ← [`js/js-ir-compiler.md`](js/js-ir-compiler.md) — js-ir-compiler
- [ ] `js/js-plain-objects-fa.md` ← [`js/js-plain-objects.md`](js/js-plain-objects.md) — js-plain-objects
- [ ] `js/js-react-fa.md` ← [`js/js-react.md`](js/js-react.md) — js-react
- [ ] `wasm/wasm-overview-fa.md` ← [`wasm/wasm-overview.md`](wasm/wasm-overview.md) — Overview
- [ ] `wasm/wasm-get-started-fa.md` ← [`wasm/wasm-get-started.md`](wasm/wasm-get-started.md) — wasm-get-started
- [ ] `wasm/wasm-wasi-fa.md` ← [`wasm/wasm-wasi.md`](wasm/wasm-wasi.md) — wasm-wasi
- [ ] `wasm/wasm-debugging-fa.md` ← [`wasm/wasm-debugging.md`](wasm/wasm-debugging.md) — wasm-debugging
- [ ] `wasm/wasm-js-interop-fa.md` ← [`wasm/wasm-js-interop.md`](wasm/wasm-js-interop.md) — wasm-js-interop
- [ ] `wasm/wasm-configuration-fa.md` ← [`wasm/wasm-configuration.md`](wasm/wasm-configuration.md) — wasm-configuration
- [ ] `js/browser-api-dom-fa.md` ← [`js/browser-api-dom.md`](js/browser-api-dom.md) — browser-api-dom
- [ ] `js/js-interop-fa.md` ← [`js/js-interop.md`](js/js-interop.md) — js-interop
- [ ] `js/dynamic-type-fa.md` ← [`js/dynamic-type.md`](js/dynamic-type.md) — dynamic-type
- [ ] `js/using-packages-from-npm-fa.md` ← [`js/using-packages-from-npm.md`](js/using-packages-from-npm.md) — using-packages-from-npm
- [ ] `js/js-to-kotlin-interop-fa.md` ← [`js/js-to-kotlin-interop.md`](js/js-to-kotlin-interop.md) — js-to-kotlin-interop
- [ ] `js/js-modules-fa.md` ← [`js/js-modules.md`](js/js-modules.md) — js-modules
- [ ] `js/js-reflection-fa.md` ← [`js/js-reflection.md`](js/js-reflection.md) — js-reflection
- [ ] `js/typesafe-html-dsl-fa.md` ← [`js/typesafe-html-dsl.md`](js/typesafe-html-dsl.md) — typesafe-html-dsl

### مرحلهٔ نه: Kotlin/Native و interop بومی (26 فایل)

شاخهٔ تخصصی؛ پس از مراحل پایه و ابزار ساخت.

- [ ] `native/native-overview-fa.md` ← [`native/native-overview.md`](native/native-overview.md) — Overview
- [ ] `native/native-get-started-fa.md` ← [`native/native-get-started.md`](native/native-get-started.md) — native-get-started
- [ ] `native/native-libraries-fa.md` ← [`native/native-libraries.md`](native/native-libraries.md) — native-libraries
- [ ] `native/native-platform-libs-fa.md` ← [`native/native-platform-libs.md`](native/native-platform-libs.md) — native-platform-libs
- [ ] `native/native-memory-manager-fa.md` ← [`native/native-memory-manager.md`](native/native-memory-manager.md) — native-memory-manager
- [ ] `native/native-arc-integration-fa.md` ← [`native/native-arc-integration.md`](native/native-arc-integration.md) — Integration with ARC
- [ ] `native/native-migration-guide-fa.md` ← [`native/native-migration-guide.md`](native/native-migration-guide.md) — Migration guide
- [ ] `native/native-binary-options-fa.md` ← [`native/native-binary-options.md`](native/native-binary-options.md) — Binary options
- [ ] `native/native-debugging-fa.md` ← [`native/native-debugging.md`](native/native-debugging.md) — native-debugging
- [ ] `native/native-target-support-fa.md` ← [`native/native-target-support.md`](native/native-target-support.md) — Target and host support
- [ ] `native/native-improving-compilation-time-fa.md` ← [`native/native-improving-compilation-time.md`](native/native-improving-compilation-time.md) — Improving compilation time
- [ ] `native/native-llvm-passes-fa.md` ← [`native/native-llvm-passes.md`](native/native-llvm-passes.md) — Customizing LLVM passes
- [ ] `native/native-binary-licenses-fa.md` ← [`native/native-binary-licenses.md`](native/native-binary-licenses.md) — License files
- [ ] `native/native-faq-fa.md` ← [`native/native-faq.md`](native/native-faq.md) — native-faq
- [ ] `native/native-objc-interop-fa.md` ← [`native/native-objc-interop.md`](native/native-objc-interop.md) — native-objc-interop
- [ ] `native/apple-framework-fa.md` ← [`native/apple-framework.md`](native/apple-framework.md) — apple-framework
- [ ] `native/native-swift-export-fa.md` ← [`native/native-swift-export.md`](native/native-swift-export.md) — Swift export
- [ ] `native/native-c-interop-fa.md` ← [`native/native-c-interop.md`](native/native-c-interop.md) — native-c-interop
- [ ] `native/mapping-primitive-data-types-from-c-fa.md` ← [`native/mapping-primitive-data-types-from-c.md`](native/mapping-primitive-data-types-from-c.md) — Primitive data types
- [ ] `native/mapping-struct-union-types-from-c-fa.md` ← [`native/mapping-struct-union-types-from-c.md`](native/mapping-struct-union-types-from-c.md) — Struct and union types
- [ ] `native/mapping-function-pointers-from-c-fa.md` ← [`native/mapping-function-pointers-from-c.md`](native/mapping-function-pointers-from-c.md) — Function pointers
- [ ] `native/mapping-strings-from-c-fa.md` ← [`native/mapping-strings-from-c.md`](native/mapping-strings-from-c.md) — Strings
- [ ] `native/native-dynamic-libraries-fa.md` ← [`native/native-dynamic-libraries.md`](native/native-dynamic-libraries.md) — Create a dynamic library – tutorial
- [ ] `native/native-app-with-c-and-libcurl-fa.md` ← [`native/native-app-with-c-and-libcurl.md`](native/native-app-with-c-and-libcurl.md) — native-app-with-c-and-libcurl
- [ ] `native/native-definition-file-fa.md` ← [`native/native-definition-file.md`](native/native-definition-file.md) — native-definition-file
- [ ] `native/native-lib-import-stability-fa.md` ← [`native/native-lib-import-stability.md`](native/native-lib-import-stability.md) — External library import

### مرحلهٔ ده: توسعهٔ Android (1 فایل)

ورودی رسمی مستندات Kotlin برای Android.

- [ ] `android-overview-fa.md` ← [`android-overview.md`](android-overview.md) — Android development

### مرحلهٔ یازده: توسعه با هوش مصنوعی (6 فایل)

پس از Backend و ابزارهای ساخت نتیجهٔ بهتری دارد.

- [ ] `ai/spring-boot-claude-fa.md` ← [`ai/spring-boot-claude.md`](ai/spring-boot-claude.md) — Create a Kotlin app with Spring Boot and Claude – tutorial
- [ ] `ai/kotlin-with-ai-fa.md` ← [`ai/kotlin-with-ai.md`](ai/kotlin-with-ai.md) — Overview
- [ ] `ai/kotlin-ai-apps-development-overview-fa.md` ← [`ai/kotlin-ai-apps-development-overview.md`](ai/kotlin-ai-apps-development-overview.md) — Develop AI-powered apps
- [ ] `ai/spring-ai-guide-fa.md` ← [`ai/spring-ai-guide.md`](ai/spring-ai-guide.md) — Build an AI chatbot with Spring AI – tutorial
- [ ] `ai/ai-for-development-fa.md` ← [`ai/ai-for-development.md`](ai/ai-for-development.md) — AI tools
- [ ] `ai/kotlin-ai-skills-fa.md` ← [`ai/kotlin-ai-skills.md`](ai/kotlin-ai-skills.md) — Kotlin AI skills

### مرحلهٔ دوازده: تحلیل داده و Kotlin Notebook (14 فایل)

شاخهٔ تخصصی برای داده و محاسبات تعاملی.

- [ ] `data-analysis-overview-fa.md` ← [`data-analysis-overview.md`](data-analysis-overview.md) — Overview
- [ ] `data-analysis/data-analysis-work-with-data-sources-fa.md` ← [`data-analysis/data-analysis-work-with-data-sources.md`](data-analysis/data-analysis-work-with-data-sources.md) — data-analysis-work-with-data-sources
- [ ] `data-analysis/data-analysis-work-with-api-fa.md` ← [`data-analysis/data-analysis-work-with-api.md`](data-analysis/data-analysis-work-with-api.md) — data-analysis-work-with-api
- [ ] `data-analysis/data-analysis-connect-to-db-fa.md` ← [`data-analysis/data-analysis-connect-to-db.md`](data-analysis/data-analysis-connect-to-db.md) — data-analysis-connect-to-db
- [ ] `data-analysis/data-analysis-visualization-fa.md` ← [`data-analysis/data-analysis-visualization.md`](data-analysis/data-analysis-visualization.md) — With Kandy
- [ ] `data-analysis/lets-plot-fa.md` ← [`data-analysis/lets-plot.md`](data-analysis/lets-plot.md) — With Lets-Plot for Kotlin
- [ ] `data-analysis/data-analysis-libraries-fa.md` ← [`data-analysis/data-analysis-libraries.md`](data-analysis/data-analysis-libraries.md) — Libraries for data analysis
- [ ] `kotlin-notebook-overview-fa.md` ← [`kotlin-notebook-overview.md`](kotlin-notebook-overview.md) — Kotlin Notebook overview
- [ ] `data-analysis/get-started-with-kotlin-notebooks-fa.md` ← [`data-analysis/get-started-with-kotlin-notebooks.md`](data-analysis/get-started-with-kotlin-notebooks.md) — Introduction to Kotlin Notebook
- [ ] `data-analysis/kotlin-notebook-set-up-env-fa.md` ← [`data-analysis/kotlin-notebook-set-up-env.md`](data-analysis/kotlin-notebook-set-up-env.md) — 1. Set up an environment
- [ ] `data-analysis/kotlin-notebook-create-fa.md` ← [`data-analysis/kotlin-notebook-create.md`](data-analysis/kotlin-notebook-create.md) — 2. Create your first Kotlin Notebook
- [ ] `data-analysis/kotlin-notebook-add-dependencies-fa.md` ← [`data-analysis/kotlin-notebook-add-dependencies.md`](data-analysis/kotlin-notebook-add-dependencies.md) — 3. Add dependencies to a Kotlin Notebook
- [ ] `data-analysis/kotlin-notebook-share-fa.md` ← [`data-analysis/kotlin-notebook-share.md`](data-analysis/kotlin-notebook-share.md) — Share a Kotlin Notebook
- [ ] `data-analysis/data-analysis-notebooks-output-formats-fa.md` ← [`data-analysis/data-analysis-notebooks-output-formats.md`](data-analysis/data-analysis-notebooks-output-formats.md) — Output formats in Kotlin notebooks

### مرحلهٔ سیزده: ابزارهای توسعه، مستندسازی و API (9 فایل)

برای حرفه‌ای‌ترشدن گردش‌کار توسعه و انتشار.

- [ ] `scripting/custom-script-deps-tutorial-fa.md` ← [`scripting/custom-script-deps-tutorial.md`](scripting/custom-script-deps-tutorial.md) — Kotlin custom scripting
- [ ] `kotlin-ide-fa.md` ← [`kotlin-ide.md`](kotlin-ide.md) — IDEs for Kotlin development
- [ ] `run-code-snippets-fa.md` ← [`run-code-snippets.md`](run-code-snippets.md) — run-code-snippets
- [ ] `kotlin-lsp-fa.md` ← [`kotlin-lsp.md`](kotlin-lsp.md) — Kotlin Language Server
- [ ] `kotlin-doc-fa.md` ← [`kotlin-doc.md`](kotlin-doc.md) — KDoc
- [ ] `kotlin-osgi-fa.md` ← [`kotlin-osgi.md`](kotlin-osgi.md) — OSGi
- [ ] `kotlin-and-ci-fa.md` ← [`kotlin-and-ci.md`](kotlin-and-ci.md) — TeamCity
- [ ] `code-style-migration-guide-fa.md` ← [`code-style-migration-guide.md`](code-style-migration-guide.md) — Migrate to Kotlin code style with IntelliJ IDEA
- [ ] `api-references-fa.md` ← [`api-references.md`](api-references.md) — Overview

### مرحلهٔ چهارده: تکامل زبان، پایداری و امنیت (9 فایل)

برای درک تصمیم‌های طراحی و نگه‌داری پروژه‌ها.

- [ ] `roadmap-fa.md` ← [`roadmap.md`](roadmap.md) — roadmap
- [ ] `kotlin-language-features-and-proposals-fa.md` ← [`kotlin-language-features-and-proposals.md`](kotlin-language-features-and-proposals.md) — Language features and proposals
- [ ] `kotlin-evolution-principles-fa.md` ← [`kotlin-evolution-principles.md`](kotlin-evolution-principles.md) — Language evolution principles
- [ ] `components-stability-fa.md` ← [`components-stability.md`](components-stability.md) — components-stability
- [ ] `components-stability-pre-1.4-fa.md` ← [`components-stability-pre-1.4.md`](components-stability-pre-1.4.md) — components-stability-pre-1.4
- [ ] `releases-fa.md` ← [`releases.md`](releases.md) — releases
- [ ] `eap-fa.md` ← [`eap.md`](eap.md) — Participate
- [ ] `configure-build-for-eap-fa.md` ← [`configure-build-for-eap.md`](configure-build-for-eap.md) — configure-build-for-eap
- [ ] `security-fa.md` ← [`security.md`](security.md) — security

### مرحلهٔ پانزده: تاریخچهٔ نسخه‌ها و راهنماهای سازگاری (41 فایل)

مرجع تاریخی است؛ لازم نیست برای یادگیری روزمره همه را پشت‌سرهم بخوانید.

- [ ] `whatsnew/whatsnew2420-fa.md` ← [`whatsnew/whatsnew2420.md`](whatsnew/whatsnew2420.md) — Kotlin 2.4.20
- [ ] `whatsnew/whatsnew-eap-fa.md` ← [`whatsnew/whatsnew-eap.md`](whatsnew/whatsnew-eap.md) — Kotlin 2.5.0-Beta1
- [ ] `whatsnew/whatsnew24-fa.md` ← [`whatsnew/whatsnew24.md`](whatsnew/whatsnew24.md) — Kotlin 2.4.0
- [ ] `compatibility-guides/compatibility-guide-24-fa.md` ← [`compatibility-guides/compatibility-guide-24.md`](compatibility-guides/compatibility-guide-24.md) — Compatibility guide
- [ ] `whatsnew/whatsnew2320-fa.md` ← [`whatsnew/whatsnew2320.md`](whatsnew/whatsnew2320.md) — Kotlin 2.3.20
- [ ] `whatsnew/whatsnew23-fa.md` ← [`whatsnew/whatsnew23.md`](whatsnew/whatsnew23.md) — Kotlin 2.3.0
- [ ] `compatibility-guides/compatibility-guide-23-fa.md` ← [`compatibility-guides/compatibility-guide-23.md`](compatibility-guides/compatibility-guide-23.md) — Compatibility guide
- [ ] `whatsnew/whatsnew2220-fa.md` ← [`whatsnew/whatsnew2220.md`](whatsnew/whatsnew2220.md) — Kotlin 2.2.20
- [ ] `whatsnew/whatsnew22-fa.md` ← [`whatsnew/whatsnew22.md`](whatsnew/whatsnew22.md) — Kotlin 2.2.0
- [ ] `compatibility-guides/compatibility-guide-22-fa.md` ← [`compatibility-guides/compatibility-guide-22.md`](compatibility-guides/compatibility-guide-22.md) — Compatibility guide
- [ ] `whatsnew/whatsnew2120-fa.md` ← [`whatsnew/whatsnew2120.md`](whatsnew/whatsnew2120.md) — Kotlin 2.1.20
- [ ] `whatsnew/whatsnew21-fa.md` ← [`whatsnew/whatsnew21.md`](whatsnew/whatsnew21.md) — Kotlin 2.1.0
- [ ] `compatibility-guides/compatibility-guide-21-fa.md` ← [`compatibility-guides/compatibility-guide-21.md`](compatibility-guides/compatibility-guide-21.md) — Compatibility guide
- [ ] `whatsnew/whatsnew2020-fa.md` ← [`whatsnew/whatsnew2020.md`](whatsnew/whatsnew2020.md) — Kotlin 2.0.20
- [ ] `whatsnew/whatsnew20-fa.md` ← [`whatsnew/whatsnew20.md`](whatsnew/whatsnew20.md) — Kotlin 2.0.0
- [ ] `compatibility-guides/compatibility-guide-20-fa.md` ← [`compatibility-guides/compatibility-guide-20.md`](compatibility-guides/compatibility-guide-20.md) — Compatibility guide
- [ ] `whatsnew/whatsnew1920-fa.md` ← [`whatsnew/whatsnew1920.md`](whatsnew/whatsnew1920.md) — Kotlin 1.9.20
- [ ] `whatsnew/whatsnew19-fa.md` ← [`whatsnew/whatsnew19.md`](whatsnew/whatsnew19.md) — Kotlin 1.9.0
- [ ] `compatibility-guides/compatibility-guide-19-fa.md` ← [`compatibility-guides/compatibility-guide-19.md`](compatibility-guides/compatibility-guide-19.md) — Compatibility guide
- [ ] `whatsnew/whatsnew1820-fa.md` ← [`whatsnew/whatsnew1820.md`](whatsnew/whatsnew1820.md) — Kotlin 1.8.20
- [ ] `whatsnew/whatsnew18-fa.md` ← [`whatsnew/whatsnew18.md`](whatsnew/whatsnew18.md) — Kotlin 1.8.0
- [ ] `compatibility-guides/compatibility-guide-18-fa.md` ← [`compatibility-guides/compatibility-guide-18.md`](compatibility-guides/compatibility-guide-18.md) — Compatibility guide
- [ ] `whatsnew/whatsnew1720-fa.md` ← [`whatsnew/whatsnew1720.md`](whatsnew/whatsnew1720.md) — Kotlin 1.7.20
- [ ] `whatsnew/whatsnew17-fa.md` ← [`whatsnew/whatsnew17.md`](whatsnew/whatsnew17.md) — Kotlin 1.7.0
- [ ] `compatibility-guides/compatibility-guide-1720-fa.md` ← [`compatibility-guides/compatibility-guide-1720.md`](compatibility-guides/compatibility-guide-1720.md) — compatibility-guide-1720
- [ ] `compatibility-guides/compatibility-guide-17-fa.md` ← [`compatibility-guides/compatibility-guide-17.md`](compatibility-guides/compatibility-guide-17.md) — compatibility-guide-17
- [ ] `whatsnew/whatsnew1620-fa.md` ← [`whatsnew/whatsnew1620.md`](whatsnew/whatsnew1620.md) — Kotlin 1.6.20
- [ ] `whatsnew/whatsnew16-fa.md` ← [`whatsnew/whatsnew16.md`](whatsnew/whatsnew16.md) — Kotlin 1.6.0
- [ ] `compatibility-guides/compatibility-guide-16-fa.md` ← [`compatibility-guides/compatibility-guide-16.md`](compatibility-guides/compatibility-guide-16.md) — Compatibility guide
- [ ] `whatsnew/whatsnew1530-fa.md` ← [`whatsnew/whatsnew1530.md`](whatsnew/whatsnew1530.md) — Kotlin 1.5.30
- [ ] `whatsnew/whatsnew1520-fa.md` ← [`whatsnew/whatsnew1520.md`](whatsnew/whatsnew1520.md) — Kotlin 1.5.20
- [ ] `whatsnew/whatsnew15-fa.md` ← [`whatsnew/whatsnew15.md`](whatsnew/whatsnew15.md) — Kotlin 1.5.0
- [ ] `compatibility-guides/compatibility-guide-15-fa.md` ← [`compatibility-guides/compatibility-guide-15.md`](compatibility-guides/compatibility-guide-15.md) — Compatibility guide
- [ ] `whatsnew/whatsnew1430-fa.md` ← [`whatsnew/whatsnew1430.md`](whatsnew/whatsnew1430.md) — Kotlin 1.4.30
- [ ] `whatsnew/whatsnew1420-fa.md` ← [`whatsnew/whatsnew1420.md`](whatsnew/whatsnew1420.md) — Kotlin 1.4.20
- [ ] `whatsnew/whatsnew14-fa.md` ← [`whatsnew/whatsnew14.md`](whatsnew/whatsnew14.md) — Kotlin 1.4.0
- [ ] `compatibility-guides/compatibility-guide-14-fa.md` ← [`compatibility-guides/compatibility-guide-14.md`](compatibility-guides/compatibility-guide-14.md) — Compatibility guide
- [ ] `whatsnew/whatsnew13-fa.md` ← [`whatsnew/whatsnew13.md`](whatsnew/whatsnew13.md) — Kotlin 1.3
- [ ] `compatibility-guides/compatibility-guide-13-fa.md` ← [`compatibility-guides/compatibility-guide-13.md`](compatibility-guides/compatibility-guide-13.md) — Compatibility guide
- [ ] `whatsnew/whatsnew12-fa.md` ← [`whatsnew/whatsnew12.md`](whatsnew/whatsnew12.md) — Kotlin 1.2
- [ ] `whatsnew/whatsnew11-fa.md` ← [`whatsnew/whatsnew11.md`](whatsnew/whatsnew11.md) — Kotlin 1.1

### مرحلهٔ شانزده: منابع تکمیلی و جامعه (22 فایل)

مطالعهٔ آزاد پس از مسیر اصلی یا در کنار آن.

- [ ] `learning-materials-overview-fa.md` ← [`learning-materials-overview.md`](learning-materials-overview.md) — Overview
- [ ] `kotlin-hands-on-fa.md` ← [`kotlin-hands-on.md`](kotlin-hands-on.md) — kotlin-hands-on
- [ ] `kotlin-tips-fa.md` ← [`kotlin-tips.md`](kotlin-tips.md) — kotlin-tips
- [ ] `koans-fa.md` ← [`koans.md`](koans.md) — koans
- [ ] `books-fa.md` ← [`books.md`](books.md) — books
- [ ] `advent-of-code-fa.md` ← [`advent-of-code.md`](advent-of-code.md) — Advent of Code puzzles
- [ ] `edu-tools-learner-fa.md` ← [`edu-tools-learner.md`](edu-tools-learner.md) — Learn Kotlin
- [ ] `edu-tools-educator-fa.md` ← [`edu-tools-educator.md`](edu-tools-educator.md) — Teach Kotlin
- [ ] `faq-fa.md` ← [`faq.md`](faq.md) — faq
- [ ] `gsoc-overview-fa.md` ← [`gsoc-overview.md`](gsoc-overview.md) — Overview
- [ ] `gsoc-2026-fa.md` ← [`gsoc-2026.md`](gsoc-2026.md) — GSoC 2026
- [ ] `gsoc-2025-fa.md` ← [`gsoc-2025.md`](gsoc-2025.md) — GSoC 2025
- [ ] `gsoc-2024-fa.md` ← [`gsoc-2024.md`](gsoc-2024.md) — GSoC 2024
- [ ] `gsoc-2023-fa.md` ← [`gsoc-2023.md`](gsoc-2023.md) — GSoC 2023
- [ ] `competitive-programming-fa.md` ← [`competitive-programming.md`](competitive-programming.md) — competitive-programming
- [ ] `contribute-fa.md` ← [`contribute.md`](contribute.md) — contribute
- [ ] `kug-guidelines-fa.md` ← [`kug-guidelines.md`](kug-guidelines.md) — kug-guidelines
- [ ] `kotlin-night-guidelines-fa.md` ← [`kotlin-night-guidelines.md`](kotlin-night-guidelines.md) — kotlin-night-guidelines
- [ ] `slack-code-of-conduct-fa.md` ← [`slack-code-of-conduct.md`](slack-code-of-conduct.md) — slack-code-of-conduct
- [ ] `kotlin-brand-assets-fa.md` ← [`kotlin-brand-assets.md`](kotlin-brand-assets.md) — kotlin-brand-assets
- [ ] `kotlin-pdf-fa.md` ← [`kotlin-pdf.md`](kotlin-pdf.md) — kotlin-pdf
- [ ] `test-page-fa.md` ← [`test-page.md`](test-page.md) — test-page

## نگه‌داری ماهانهٔ منبع

در شنبهٔ اول هر ماه، پیش از ترجمه، snapshot رسمی را دوباره مقایسه کنید. فایل‌های انگلیسی تازه یا تغییرکرده را وارد کنید، ترجمه‌های متأثر را با 🔄 مشخص کنید و تاریخ شمسی/commit بالای همین فایل را به‌روز کنید. فایل فارسی نباید با sync خودکار جایگزین شود.



