# رودمپ ترجمه داکیومنت‌های کاتلین به فارسی 🚀

این فایل برای پیگیری وضعیت ترجمه داکیومنت‌های کاتلین به زبان فارسی ایجاد شده است. این لیست شامل تمامی بخش‌های موجود در پروژه (Core، Platforms، Tools و ...) می‌باشد.

---

## 🤖 پرامپت بهینه برای ترجمه (AI Instruction)

برای حفظ یکپارچگی در ترجمه توسط هوش مصنوعی، از پرامپت زیر استفاده کنید:

> **Project:** Kotlin-Learn-Fa  
> **Context:** ترجمه و بومی‌سازی مستندات رسمی کاتلین.  
> **Instruction:**  
> ۱. **اصطلاحات فنی:** استفاده از معادل‌های رایج (Property -> ویژگی، Expression -> عبارت، Statement -> دستور). اصطلاح انگلیسی در اولین بار داخل پرانتز بیاید.  
> ۲. **کلمات کلیدی:** عدم ترجمه کلمات کلیدی (`val`, `var`, `fun`...) و قرار دادن آن‌ها در backtick.  
> ۳. **مدیریت لینک‌ها:** اگر فایل `-fa.md` در پروژه هست، به آن لینک بده؛ در غیر این صورت به آدرس کامل در `kotlinlang.org/docs/` ارجاع بده.  
> ۴. **نگارش:** رعایت نیم‌فاصله و لحن حرفه‌ای/فنی الزامی است.  
> ۵. **ساختار:** استفاده از جداول و بلاک‌های کد استاندارد برای نمایش بهتر در Obsidian و موبایل.

---

## 🏗️ وضعیت کلی و رودمپ پیشنهادی

### ۱. تور کاتلین (Kotlin Tour) - شروع سریع
آموزش‌های مرحله به مرحله برای یادگیری سریع زبان. (مسیر: `tour/`)

- [ ] [خوش‌آمدگویی](tour/kotlin-tour-welcome.md)
- [ ] [سلام دنیا](tour/kotlin-tour-hello-world.md)
- [ ] [تایپ‌های پایه](tour/kotlin-tour-basic-types.md)
- [ ] [مجموعه‌ها](tour/kotlin-tour-collections.md)
- [ ] [کنترل جریان](tour/kotlin-tour-control-flow.md)
- [ ] [توابع](tour/kotlin-tour-functions.md)
- [ ] [کلاس‌ها](tour/kotlin-tour-classes.md)
- [ ] [ایمنی نال](tour/kotlin-tour-null-safety.md)
- [ ] [بخش‌های پیشرفته (Intermediate)](tour/) (شامل ۱۰ فایل دیگر)

---

### ۲. مبانی کاتلین (Kotlin Basics)
این بخش الفبای زبان کاتلین است.

- [x] [سینتکس پایه](basic-syntax.md) (basic-syntax-fa.md)
- [x] [اصطلاحات کاتلین](idioms.md) (idioms-fa.md)
- [x] [قراردادهای کدنویسی](coding-conventions.md) (coding-conventions-fa.md)
- [x] [بررسی کلی تایپ‌ها](types-overview.md) (types-overview-fa.md)
- [x] [اعداد](numbers.md) (numbers-fa.md)
- [x] [مقادیر منطقی](booleans.md) (booleans-fa.md)
- [x] [کاراکترها](characters.md) (characters-fa.md)
- [x] [رشته‌ها](strings.md) (strings-fa.md)
- [x] [آرایه‌ها](arrays.md) (arrays-fa.md)
- [x] [اعداد صحیح بدون علامت](unsigned-integer-types.md) (unsigned-integer-types-fa.md)
- [x] [ساختارهای کنترلی](control-flow.md) (control-flow-fa.md)
- [x] [بازگشت و پرش](returns.md) (returns-fa.md)
- [x] [پکیج‌ها و ایمپورت‌ها](packages.md) (packages-fa.md)

---

### ۳. کلاس‌ها و اشیاء (Classes and Objects)
درک عمیق شیءگرایی در کاتلین.

- [ ] [کلاس‌ها](classes.md)
- [ ] [ارث‌بری](inheritance.md)
- [ ] [اینترفیس‌ها](interfaces.md)
- [ ] [اینترفیس‌های عملکردی (SAM)](fun-interfaces.md)
- [x] [اصلاح‌کننده‌های دسترسی](visibility-modifiers.md) (visibility-modifiers-fa.md)
- [ ] [اکستنشن‌ها](extensions.md)
- [ ] [دیتا کلاس‌ها](data-classes.md)
- [ ] [کلاس‌های مهر و موم شده (Sealed)](sealed-classes.md)
- [ ] [جنریک‌ها](generics.md)
- [ ] [کلاس‌های درونی و تو در تو](nested-classes.md)
- [ ] [کلاس‌های انام (Enum)](enum-classes.md)
- [ ] [کلاس‌های اینلاین](inline-classes.md)
- [ ] [اشیاء و عبارت‌های شیء](object-declarations.md)
- [ ] [واگذاری (Delegation)](delegation.md)
- [ ] [پروپرتی‌های واگذار شده](delegated-properties.md)
- [ ] [مستعار تایپ (Type aliases)](type-aliases.md)

---

### ۴. توابع و لمبداها (Functions and Lambdas)
- [ ] [توابع](functions.md)
- [ ] [لمبداها](lambdas.md)
- [ ] [توابع اینلاین](inline-functions.md)
- [ ] [اورلود کردن اپراتورها](operator-overloading.md)
- [ ] [پارامترهای کانتکست (Context parameters)](context-parameters.md)

---

### ۵. مفاهیم پیشرفته و کاربردی (Concepts)
- [ ] [ایمنی نال (Null safety)](null-safety.md)
- [ ] [استثناها (Exceptions)](exceptions.md)
- [x] [انوتیشن‌ها (Annotations)](annotations-fa.md)
- [ ] [رفلکشن (Reflection)](reflection.md)
- [ ] [توابع اسکوپ (Scope functions)](scope-functions.md)
- [ ] [کست کردن تایپ‌ها (Type casts)](typecasts.md)
- [ ] [عبارت this](this-expressions.md)
- [ ] [برابری (Equality)](equality.md)

---

### ۶. مجموعه‌ها (Collections)
- [ ] [بررسی کلی مجموعه‌ها](collections-overview.md)
- [ ] [ساخت مجموعه‌ها](constructing-collections.md)
- [ ] [ایتریتورها](iterators.md)
- [ ] [بازه‌ها (Ranges)](ranges.md)
- [ ] [سیکوئنس‌ها (Sequences)](sequences.md)
- [ ] [عملیات مجموعه‌ها](collection-operations.md) (شامل فیلتر، گروه‌بندی، مرتب‌سازی و ...)

---

### ۷. کوروتین‌ها (Coroutines)
- [ ] [بررسی کلی کوروتین‌ها](coroutines-overview.md)

---

### ۸. ابزارهای ساخت و پلاگین‌ها (Build Tools)
- [ ] [گردل (Gradle)](gradle/) (شامل ۸ فایل در پوشه `gradle/`)
- [ ] [میون (Maven)](maven.md)
- [ ] [کامپایلر خط فرمان](command-line.md)
- [ ] [کی‌اس‌پی (KSP)](ksp/) (شامل ۱۱ فایل در پوشه `ksp/`)
- [ ] [کپت (Kapt)](kapt.md)

---

### ۹. پلتفرم‌های کاتلین (Multiplatform & Platforms)
- [ ] **Kotlin/JVM:** (شامل ۱۴ فایل در پوشه `jvm/`)
- [ ] **Kotlin/JS:** (شامل ۲۰ فایل در پوشه `js/`)
- [ ] **Kotlin/Native:** (شامل ۲۶ فایل در پوشه `native/`)
- [ ] **Kotlin/Wasm:** (شامل ۶ فایل در پوشه `wasm/`)

---

### ۱۰. تحلیل داده و اسکریپت‌نویسی (Data Analysis & Scripting)
- [ ] [تحلیل داده با کاتلین](data-analysis/) (شامل ۱۲ فایل در پوشه `data-analysis/`)
- [ ] [اسکریپت‌نویسی](scripting/)

---

### ۱۱. موارد دیگر (Miscellaneous)
- [ ] [تازه‌های کاتلین (What's New)](whatsnew/)
- [ ] [راهنمای سازگاری (Compatibility)](compatibility-guides/)
- [x] [واژه‌نامه (Glossary)](glossary-fa.md)
- [x] [مرجع کلمات کلیدی](keyword-reference.md) (keyword-reference-fa.md)

---

💡 **نکته:** ترتیب پیشنهادی برای ترجمه: مبانی -> کلاس‌ها -> مجموعه‌ها -> پلتفرم‌ها.
