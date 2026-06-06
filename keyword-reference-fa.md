[//]: # (title: Keywords and operators)

## کلمات کلیدی سخت (Hard keywords)

توکن‌های زیر همیشه به‌عنوان کلمهٔ کلیدی تفسیر می‌شوند و نمی‌توان از آن‌ها به‌عنوان شناسه استفاده کرد:

- `as`
    
    - برای [تبدیل نوع](typecasts.md#unsafe-cast-operator) استفاده می‌شود.
    - یک [نام مستعار برای import](packages-fa.md#imports) مشخص می‌کند.
- `as?` برای [تبدیل نوع امن](typecasts.md#unsafe-cast-operator) استفاده می‌شود.
- `break` [اجرای یک حلقه را متوقف می‌کند](returns.md).
- `class` یک [کلاس](classes.md) را تعریف می‌کند.
- `continue` [به مرحلهٔ بعدی نزدیک‌ترین حلقهٔ دربرگیرنده می‌رود](returns.md).
- `do` شروع یک [حلقهٔ do/while](control-flow.md#while-loops) است (حلقه‌ای با شرط پس از اجرا).
- `else` شاخه‌ای از یک [عبارت if](control-flow.md#if-expression) را تعریف می‌کند که زمانی اجرا می‌شود که شرط نادرست باشد.
- `false` مقدار «نادرست» از [نوع Boolean](booleans-fa.md) را مشخص می‌کند.
- `for` شروع یک [حلقهٔ for](control-flow.md#for-loops) است.
- `fun` یک [تابع](functions.md) را تعریف می‌کند.
- `if` شروع یک [عبارت if](control-flow.md#if-expression) است.
- `in`
    - شیئی را که در یک [حلقهٔ for](control-flow.md#for-loops) پیمایش می‌شود مشخص می‌کند.
    - به‌عنوان یک عملگر میانی برای بررسی اینکه یک مقدار متعلق به [یک بازه](ranges.md)،  
        یک کالکشن، یا موجودیت دیگری است که [متد «contains» را تعریف کرده](operator-overloading.md#in-operator) استفاده می‌شود.
    - در [عبارات when](control-flow.md#when-expressions-and-statements) نیز برای همین منظور استفاده می‌شود.
    - یک پارامتر نوع را به‌عنوان [contravariant](generics.md#declaration-site-variance) علامت‌گذاری می‌کند.
- `!in`
    - به‌عنوان عملگر برای بررسی اینکه یک مقدار به [یک بازه](ranges.md)،  
        یک کالکشن، یا موجودیت دیگری که [متد «contains» را تعریف کرده](operator-overloading.md#in-operator) تعلق ندارد استفاده می‌شود.
    - در [عبارات when](control-flow.md#when-expressions-and-statements) نیز برای همین منظور استفاده می‌شود.
- `interface` یک [اینترفیس](interfaces.md) را تعریف می‌کند.
- `is`
    - بررسی می‌کند که [یک مقدار دارای نوع خاصی هست یا نه](typecasts.md#is-and-is-operators).
    - در [عبارات when](control-flow.md#when-expressions-and-statements) نیز برای همین منظور استفاده می‌شود.
- `!is`
    - بررسی می‌کند که [یک مقدار دارای نوع خاصی نیست](typecasts.md#is-and-is-operators).
    - در [عبارات when](control-flow.md#when-expressions-and-statements) نیز برای همین منظور استفاده می‌شود.
- `null` یک ثابت است که نمایانگر مرجعی است که به هیچ شیئی اشاره نمی‌کند.
- `object` [یک کلاس و نمونهٔ آن را هم‌زمان](object-declarations.md) تعریف می‌کند.
- `package` [پکیج فایل جاری](packages-fa.md) را مشخص می‌کند.
- `return` [از نزدیک‌ترین تابع یا تابع ناشناس خارج می‌شود](returns.md).
- `super`
    - به [پیاده‌سازی متد یا property در کلاس والد](inheritance.md#calling-the-superclass-implementation) اشاره می‌کند.
    - [سازندهٔ کلاس والد را از یک سازندهٔ ثانویه فراخوانی می‌کند](classes.md#inheritance).
- `this`
    - به [گیرندهٔ فعلی](this-expressions.md) اشاره می‌کند.
    - [سازندهٔ دیگری از همان کلاس را از یک سازندهٔ ثانویه فراخوانی می‌کند](classes.md#constructors-and-initializer-blocks).
- `throw` [یک استثنا پرتاب می‌کند](exceptions.md).
- `true` مقدار «درست» از [نوع Boolean](booleans-fa.md) را مشخص می‌کند.
- `try` شروع یک [بلاک مدیریت استثنا](exceptions.md) است.
- `typealias` یک [نام مستعار برای نوع](type-aliases.md) تعریف می‌کند.
- `typeof` برای استفادهٔ آینده رزرو شده است.
- `val` یک [property فقط‌خواندنی](properties.md) یا [متغیر محلی](basic-syntax-fa.md#variables) تعریف می‌کند.
- `var` یک [property قابل‌تغییر](properties.md) یا [متغیر محلی](basic-syntax-fa.md#variables) تعریف می‌کند.
- `when` شروع یک [عبارت when](control-flow.md#when-expressions-and-statements) است (یکی از شاخه‌های داده‌شده را اجرا می‌کند).
- `while` شروع یک [حلقهٔ while](control-flow.md#while-loops) است (حلقه‌ای با شرط قبل از اجرا).

## کلمات کلیدی نرم (Soft keywords)

توکن‌های زیر در زمینه‌هایی که قابل‌استفاده هستند به‌عنوان کلمهٔ کلیدی عمل می‌کنند و در زمینه‌های دیگر  
می‌توانند به‌عنوان شناسه استفاده شوند:

- `by`
    - [پیاده‌سازی یک اینترفیس را به شیء دیگری واگذار می‌کند](delegation.md).
    - [پیاده‌سازی accessorهای یک property را به شیء دیگری واگذار می‌کند](delegated-properties.md).
        
- `catch` شروع بلاکی است که [یک نوع خاص از استثنا را مدیریت می‌کند](exceptions.md).
- `constructor` یک [سازندهٔ اصلی یا ثانویه](classes.md#constructors-and-initializer-blocks) را تعریف می‌کند.
- `delegate` به‌عنوان [هدف استفادهٔ annotation](annotations-fa.md#annotation-use-site-targets) استفاده می‌شود.
- `dynamic` به یک [نوع پویا](dynamic-type.md) در کد Kotlin/JS اشاره می‌کند.
- `field` به‌عنوان [هدف استفادهٔ annotation](annotations-fa.md#annotation-use-site-targets) استفاده می‌شود.
- `file` به‌عنوان [هدف استفادهٔ annotation](annotations-fa.md#annotation-use-site-targets) استفاده می‌شود.
- `finally` شروع بلاکی است که [همیشه هنگام خروج از بلاک try اجرا می‌شود](exceptions.md).
- `get`
    - [getter یک property](properties.md) را تعریف می‌کند.
    - به‌عنوان [هدف استفادهٔ annotation](annotations-fa.md#annotation-use-site-targets) استفاده می‌شود.
- `import` [یک اعلان را از پکیج دیگر به فایل جاری وارد می‌کند](packages-fa.md).
- `init` شروع یک [initializer block](classes.md#constructors-and-initializer-blocks) است.
- `param` به‌عنوان [هدف استفادهٔ annotation](annotations-fa.md#annotation-use-site-targets) استفاده می‌شود.
- `property` به‌عنوان [هدف استفادهٔ annotation](annotations-fa.md#annotation-use-site-targets) استفاده می‌شود.
- `receiver` به‌عنوان [هدف استفادهٔ annotation](annotations-fa.md#annotation-use-site-targets) استفاده می‌شود.
- `set`
    - [setter یک property](properties.md) را تعریف می‌کند.
    - به‌عنوان [هدف استفادهٔ annotation](annotations-fa.md#annotation-use-site-targets) استفاده می‌شود.
- `setparam` به‌عنوان [هدف استفادهٔ annotation](annotations-fa.md#annotation-use-site-targets) استفاده می‌شود.
- `value` همراه با کلمهٔ کلیدی `class` یک [inline class](inline-classes.md) را تعریف می‌کند.
- `where` [قیود یک پارامتر نوع generic](generics.md#upper-bounds) را مشخص می‌کند.

## کلمات کلیدی modifier

توکن‌های زیر در لیست modifierهای اعلان‌ها به‌عنوان کلمهٔ کلیدی عمل می‌کنند و در زمینه‌های دیگر  
می‌توانند به‌عنوان شناسه استفاده شوند:

- `abstract` یک کلاس یا عضو را به‌عنوان [abstract](classes.md#abstract-classes) علامت‌گذاری می‌کند.
- `actual` یک پیاده‌سازی وابسته به پلتفرم را در [پروژه‌های چندسکویی](https://kotlinlang.org/docs/multiplatform/multiplatform-expect-actual.html) مشخص می‌کند.
- `annotation` یک [کلاس annotation](annotations-fa.md) تعریف می‌کند.
- `companion` یک [companion object](object-declarations.md#companion-objects) تعریف می‌کند.
- `const` یک property را به‌عنوان [ثابت در زمان کامپایل](properties.md#compile-time-constants) علامت‌گذاری می‌کند.
- `crossinline` [return غیرمحلی در یک lambda که به تابع inline پاس داده شده](inline-functions.md#returns) را ممنوع می‌کند.
- `data` به کامپایلر دستور می‌دهد [اعضای استاندارد یک کلاس](data-classes.md) را تولید کند.
- `enum` یک [enum](enum-classes.md) تعریف می‌کند.
- `expect` یک اعلان را به‌عنوان [وابسته به پلتفرم](https://kotlinlang.org/docs/multiplatform/multiplatform-expect-actual.html) علامت‌گذاری می‌کند که انتظار می‌رود در ماژول‌های پلتفرم پیاده‌سازی شود.
- `external` یک اعلان را به‌عنوان پیاده‌سازی‌شده خارج از Kotlin علامت‌گذاری می‌کند (قابل‌دسترسی از طریق [JNI](java-interop.md#using-jni-with-kotlin) یا در [JavaScript](js-interop.md#external-modifier)).
- `final` [override شدن یک عضو](inheritance.md#overriding-methods) را ممنوع می‌کند.
- `infix` اجازه می‌دهد یک تابع با [سینتکس infix](functions.md#infix-notation) فراخوانی شود.
- `inline` به کامپایلر می‌گوید [تابع و lambdaهای پاس‌داده‌شده به آن را در محل فراخوانی inline کند](inline-functions.md).
- `inner` امکان اشاره به نمونهٔ کلاس بیرونی را از یک [کلاس تو‌در‌تو](nested-classes.md) فراهم می‌کند.
- `internal` یک اعلان را به‌عنوان [قابل‌مشاهده در ماژول جاری](visibility-modifiers-fa.md) علامت‌گذاری می‌کند.
- `lateinit` اجازه می‌دهد یک [property غیرnullable خارج از سازنده مقداردهی شود](properties.md#late-initialized-properties-and-variables).
- `noinline` [inline شدن یک lambda که به تابع inline پاس داده شده](inline-functions.md#noinline) را غیرفعال می‌کند.
- `open` اجازه می‌دهد [از یک کلاس ارث‌بری شود یا یک عضو override شود](classes.md#inheritance).
- `operator` یک تابع را به‌عنوان [overload کردن یک عملگر یا پیاده‌سازی یک قرارداد](operator-overloading.md) علامت‌گذاری می‌کند.
- `out` یک پارامتر نوع را به‌عنوان [covariant](generics.md#declaration-site-variance) علامت‌گذاری می‌کند.
- `override` یک عضو را به‌عنوان [override عضو کلاس والد](inheritance.md#overriding-methods) علامت‌گذاری می‌کند.
- `private` یک اعلان را به‌عنوان [قابل‌مشاهده در کلاس یا فایل جاری](visibility-modifiers-fa.md) علامت‌گذاری می‌کند.
- `protected` یک اعلان را به‌عنوان [قابل‌مشاهده در کلاس جاری و زیرکلاس‌های آن](visibility-modifiers-fa.md) علامت‌گذاری می‌کند.
- `public` یک اعلان را به‌عنوان [قابل‌مشاهده در همه‌جا](visibility-modifiers-fa.md) علامت‌گذاری می‌کند.
- `reified` یک پارامتر نوع در تابع inline را به‌عنوان [قابل‌دسترسی در زمان اجرا](inline-functions.md#reified-type-parameters) علامت‌گذاری می‌کند.
- `sealed` یک [sealed class](sealed-classes.md) تعریف می‌کند (کلاسی با ارث‌بری محدود).
- `suspend` یک تابع یا lambda را به‌عنوان suspend علامت‌گذاری می‌کند (قابل‌استفاده به‌عنوان [coroutine](coroutines-overview.md)).
- `tailrec` یک تابع را به‌عنوان [tail-recursive](functions.md#tail-recursive-functions) علامت‌گذاری می‌کند (که به کامپایلر اجازه می‌دهد بازگشت را با iteration جایگزین کند).
- `vararg` اجازه می‌دهد [تعداد متغیری از آرگومان‌ها برای یک پارامتر ارسال شود](functions.md#variable-number-of-arguments-varargs).

## شناسه‌های ویژه

شناسه‌های زیر توسط کامپایلر در زمینه‌های خاص تعریف می‌شوند و در زمینه‌های دیگر  
می‌توانند مانند شناسه‌های عادی استفاده شوند:

- `field` در داخل accessor یک property برای اشاره به [backing field آن property](properties.md#backing-fields) استفاده می‌شود.
- `it` در داخل یک lambda برای [اشارهٔ ضمنی به پارامتر آن](lambdas.md#it-implicit-name-of-a-single-parameter) استفاده می‌شود.
## عملگرها و نمادهای ویژه

Kotlin از عملگرها و نمادهای ویژهٔ زیر پشتیبانی می‌کند:

- `+`, `-`, `*`, `/`, `%` — عملگرهای ریاضی
    - `*` همچنین برای [ارسال یک آرایه به پارامتر vararg](functions.md#variable-number-of-arguments-varargs) استفاده می‌شود.
- `=`
    - عملگر انتساب.
    - برای مشخص‌کردن [مقادیر پیش‌فرض پارامترها](functions.md#parameters-with-default-values) استفاده می‌شود.
- `+=`, `-=`, `*=`, `/=`, `%=` — [عملگرهای انتساب ترکیبی](operator-overloading.md#augmented-assignments).
- `++`, `--` — [عملگرهای افزایش و کاهش](operator-overloading.md#increments-and-decrements).
- `&&`, `||`, `!` — عملگرهای منطقی «و»، «یا» و «نقیض» (برای عملیات بیتی، از [توابع infix متناظر](numbers-fa.md#operations-on-numbers) استفاده کنید).
- `==`, `!=` — [عملگرهای برابری](operator-overloading.md#equality-and-inequality-operators) (برای انواع غیر primitive به فراخوانی `equals()` تبدیل می‌شوند).
- `===`, `!==` — [عملگرهای برابری ارجاعی](equality.md#referential-equality).
- `<`, `>`, `<=`, `>=` — [عملگرهای مقایسه](operator-overloading.md#comparison-operators) (برای انواع غیر primitive به فراخوانی `compareTo()` تبدیل می‌شوند).
- `[`, `]` — [عملگر دسترسی اندیسی](operator-overloading.md#indexed-access-operator) (به فراخوانی‌های `get` و `set` تبدیل می‌شوند).
- `!!` [تضمین می‌کند که یک expression غیرnullable است](null-safety.md#not-null-assertion-operator).
- `?.` یک [فراخوانی امن](null-safety.md#safe-call-operator) انجام می‌دهد (اگر گیرنده non-nullable باشد، متد را فراخوانی یا property را دسترسی می‌دهد).
- `?:` اگر مقدار سمت چپ null باشد، مقدار سمت راست را برمی‌گرداند ([عملگر الویس](null-safety.md#elvis-operator)).
- `::` یک [ارجاع به عضو](reflection.md#function-references) یا یک [ارجاع به کلاس](reflection.md#class-references) ایجاد می‌کند.
- `..`, `..<` [بازه‌ها](ranges.md) را ایجاد می‌کنند.
- `:` یک نام را از نوع آن در یک اعلان جدا می‌کند.
- `?` یک نوع را به‌عنوان [nullable](null-safety.md#nullable-types-and-non-nullable-types) علامت‌گذاری می‌کند.
- `->`
    - پارامترها و بدنهٔ یک [lambda expression](lambdas.md#lambda-expression-syntax) را جدا می‌کند.
    - پارامترها و اعلان نوع بازگشتی را در یک [function type](lambdas.md#function-types) جدا می‌کند.
    - شرط و بدنهٔ یک شاخه از [عبارت when](control-flow.md#when-expressions-and-statements) را جدا می‌کند.
- `@`
    - معرفی یک [annotation](annotations-fa.md#usage).
    - معرفی یا ارجاع به یک [label حلقه](returns.md#break-and-continue-labels).
    - معرفی یا ارجاع به یک [label lambda](returns.md#return-to-labels).
    - ارجاع به یک [expression `this` از scope بیرونی](this-expressions.md#qualified-this).
    - ارجاع به یک [superclass بیرونی](inheritance.md#calling-the-superclass-implementation).
- `;` چند دستور را در یک خط از هم جدا می‌کند.
- `$` به یک متغیر یا expression در یک [string template](strings-fa.md#string-templates) اشاره می‌کند.
- `_`
    - جایگزین یک پارامتر استفاده‌نشده در یک [lambda expression](lambdas.md#underscore-for-unused-variables).
    - جایگزین یک پارامتر استفاده‌نشده در یک [destructuring declaration](destructuring-declarations.md#underscore-for-unused-variables).

برای تقدم عملگرها، به [این مرجع](https://kotlinlang.org/docs/reference/grammar.html#expressions) در گرامر Kotlin مراجعه کنید.