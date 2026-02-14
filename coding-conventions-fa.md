---
tags:
  - fa
---
[//]: # (title: Coding conventions)

قراردادهای کدنویسی که به‌طور عمومی شناخته‌شده و آسان برای دنبال‌کردن هستند، برای هر زبان برنامه‌نویسی حیاتی‌اند.  
در اینجا، راهنماهایی دربارهٔ سبک کد و سازمان‌دهی کد برای پروژه‌هایی که از کاتلین استفاده می‌کنند ارائه می‌دهیم.

## پیکربندی سبک در IDE

دو IDE محبوب برای کاتلین — [IntelliJ IDEA](https://www.jetbrains.com/idea/) و [Android Studio](https://developer.android.com/studio/) —  
پشتیبانی قدرتمندی از قالب‌بندی کد ارائه می‌دهند. می‌توانید آن‌ها را طوری پیکربندی کنید که کد شما را به‌صورت خودکار مطابق با  
سبک کد مشخص‌شده قالب‌بندی کنند.

### اعمال راهنمای سبک

1. به **Settings/Preferences | Editor | Code Style | Kotlin** بروید.
2. روی **Set from...** کلیک کنید.
3. گزینهٔ **Kotlin style guide** را انتخاب کنید.

### بررسی اینکه کد شما از راهنمای سبک پیروی می‌کند

1. به **Settings/Preferences | Editor | Inspections | General** بروید.
    
2. بررسی **Incorrect formatting** را فعال کنید.  
    بازرسی‌های اضافی که مسائل دیگر توصیف‌شده در راهنمای سبک (مانند قراردادهای نام‌گذاری) را بررسی می‌کنند، به‌طور پیش‌فرض فعال هستند.
    

<!-- Replace with an external link when the guide is moved -->

برای اطلاعات بیشتر، راهنمای [Migrate to Kotlin code style with IntelliJ IDEA](code-style-migration-guide.md) را ببینید.

## سازمان‌دهی کد منبع

### ساختار دایرکتوری

در پروژه‌های خالص کاتلین، ساختار دایرکتوری پیشنهادی از ساختار پکیج پیروی می‌کند و پکیج ریشهٔ مشترک حذف می‌شود.  
برای مثال، اگر تمام کد پروژه در پکیج `org.example.kotlin` و زیربسته‌های آن باشد، فایل‌های دارای پکیج `org.example.kotlin` باید مستقیماً  
زیر ریشهٔ سورس قرار گیرند، و فایل‌های `org.example.kotlin.network.socket` باید در زیر‌دایرکتوری `network/socket` از ریشهٔ سورس باشند.

> روی JVM: در پروژه‌هایی که کاتلین همراه با جاوا استفاده می‌شود، فایل‌های سورس کاتلین باید در همان ریشهٔ سورس فایل‌های جاوا قرار گیرند  
> و از همان ساختار دایرکتوری پیروی کنند: هر فایل باید در دایرکتوری متناظر با عبارت package خود ذخیره شود.

{style="note"}

### نام فایل‌های سورس

اگر یک فایل کاتلین شامل یک کلاس یا اینترفیس واحد باشد (احتمالاً همراه با اعلان‌های سطح‌بالای مرتبط)، نام آن باید  
هم‌نام کلاس باشد و پسوند `.kt` داشته باشد. این قانون برای همهٔ انواع کلاس‌ها و اینترفیس‌ها صدق می‌کند.  
اگر یک فایل شامل چند کلاس باشد یا فقط اعلان‌های سطح‌بالا داشته باشد، نامی انتخاب کنید که محتوای فایل را توصیف کند  
و فایل را متناسب با آن نام‌گذاری کنید. از [CamelCase بزرگ](https://en.wikipedia.org/wiki/Camel_case) استفاده کنید، یعنی  
حرف اول هر کلمه بزرگ باشد. برای مثال: `ProcessDeclarations.kt`.

نام فایل باید بیانگر کاری باشد که کد داخل آن انجام می‌دهد. بنابراین، از استفاده از واژه‌های بی‌معنی مانند `Util`  
در نام فایل‌ها خودداری کنید.

#### پروژه‌های چندسکویی (Multiplatform)

در پروژه‌های چندسکویی، فایل‌هایی که اعلان‌های سطح‌بالا در سورس‌ست‌های وابسته به پلتفرم دارند، باید پسوندی مرتبط  
با نام سورس‌ست داشته باشند. برای مثال:

- **jvm**Main/kotlin/Platform.**jvm**.kt
- **android**Main/kotlin/Platform.**android**.kt
- **ios**Main/kotlin/Platform.**ios**.kt

برای سورس‌ست مشترک، فایل‌هایی که اعلان‌های سطح‌بالا دارند نباید پسوند داشته باشند. برای مثال: `commonMain/kotlin/Platform.kt`.

##### جزئیات فنی {initial-collapse-state="collapsed" collapsible="true"}

ما توصیه می‌کنیم در پروژه‌های چندسکویی از این الگوی نام‌گذاری فایل پیروی کنید، به‌دلیل محدودیت‌های JVM:  
JVM اجازهٔ داشتن اعضای سطح‌بالا (توابع، پراپرتی‌ها) را نمی‌دهد.

برای حل این مسئله، کامپایلر Kotlin JVM کلاس‌های پوششی (که «file facade» نامیده می‌شوند) ایجاد می‌کند که  
اعضای سطح‌بالا را در خود نگه می‌دارند. نام داخلی این کلاس‌ها از نام فایل مشتق می‌شود.

از طرف دیگر، JVM اجازهٔ وجود چند کلاس با نام کاملاً یکسان (FQN) را نمی‌دهد. این موضوع می‌تواند به وضعیتی منجر شود  
که یک پروژهٔ کاتلین نتواند به JVM کامپایل شود:
```kotlin
root
|- commonMain/kotlin/myPackage/Platform.kt // شامل 'fun count() { }'
|- jvmMain/kotlin/myPackage/Platform.kt // شامل 'fun multiply() { }'

```


در اینجا هر دو فایل `Platform.kt` در یک پکیج قرار دارند، بنابراین کامپایلر Kotlin JVM دو file facade تولید می‌کند  
که هر دو FQN برابر `myPackage.PlatformKt` دارند. این باعث خطای «Duplicate JVM classes» می‌شود.

ساده‌ترین راه برای جلوگیری از این مشکل، تغییر نام یکی از فایل‌ها مطابق با راهنمای بالا است. این الگوی نام‌گذاری  
ضمن حفظ خوانایی کد، از تداخل نام‌ها جلوگیری می‌کند.

> دو سناریو وجود دارد که ممکن است این توصیه‌ها زائد به نظر برسند، اما همچنان توصیه می‌کنیم از آن‌ها پیروی کنید:
> 
> - پلتفرم‌های غیر-JVM با مشکل تکرار file facade مواجه نمی‌شوند. با این حال، این الگوی نام‌گذاری به حفظ  
>     یکنواختی نام فایل‌ها کمک می‌کند.
>     
> - روی JVM، اگر فایل‌های سورس اعلان سطح‌بالا نداشته باشند، file facade تولید نمی‌شود و با تداخل نام مواجه نخواهید شد.
>     
>     با این حال، این الگوی نام‌گذاری می‌تواند از موقعیت‌هایی جلوگیری کند که یک بازآرایی ساده  
>     یا افزودن یک تابع سطح‌بالا باعث همان خطای «Duplicate JVM classes» شود.
>     

{style="tip"}

### سازمان‌دهی فایل سورس

قرار دادن چند اعلان (کلاس‌ها، توابع سطح‌بالا یا پراپرتی‌ها) در یک فایل سورس کاتلین تشویق می‌شود،  
به‌شرطی که این اعلان‌ها از نظر معنایی به هم مرتبط باشند و اندازهٔ فایل معقول بماند  
(از چند صد خط تجاوز نکند).

به‌طور خاص، هنگام تعریف توابع extension برای یک کلاس که برای همهٔ کاربران آن کلاس مرتبط‌اند،  
آن‌ها را در همان فایل کلاس قرار دهید.  
وقتی توابع extension فقط برای یک کاربر خاص معنا دارند، آن‌ها را کنار کد همان کاربر قرار دهید.  
از ایجاد فایل‌هایی که فقط برای نگه‌داشتن همهٔ extensionهای یک کلاس هستند، خودداری کنید.

### چیدمان کلاس

محتوای یک کلاس باید به ترتیب زیر قرار گیرد:

1. اعلان پراپرتی‌ها و بلاک‌های مقداردهی اولیه
2. سازنده‌های ثانویه
3. اعلان متدها
4. و companion object

متدها را به‌صورت الفبایی یا بر اساس سطح دسترسی مرتب نکنید و متدهای معمولی را از متدهای extension جدا نکنید.  
در عوض، موارد مرتبط را کنار هم قرار دهید تا کسی که کلاس را از بالا به پایین می‌خواند بتواند  
منطق اجرا را دنبال کند. یک ترتیب (سطح‌بالا اول یا برعکس) انتخاب کنید و به آن پایبند بمانید.

کلاس‌های تو‌در‌تو را کنار کدی قرار دهید که از آن‌ها استفاده می‌کند. اگر کلاس‌ها برای استفادهٔ خارجی در نظر گرفته شده‌اند  
و داخل کلاس مرجع نمی‌شوند، آن‌ها را در انتها، بعد از companion object قرار دهید.

### چیدمان پیاده‌سازی اینترفیس

هنگام پیاده‌سازی یک اینترفیس، اعضای پیاده‌سازی‌شده را به همان ترتیبی قرار دهید که در اینترفیس آمده‌اند  
(در صورت نیاز، با متدهای private اضافی که برای پیاده‌سازی استفاده می‌شوند در میان آن‌ها).

### چیدمان overloadها

همیشه overloadها را کنار هم در یک کلاس قرار دهید.

## قوانین نام‌گذاری

قوانین نام‌گذاری پکیج و کلاس در کاتلین بسیار ساده‌اند:

- نام پکیج‌ها همیشه با حروف کوچک نوشته می‌شوند و از underscore استفاده نمی‌کنند (`org.example.project`).  
    استفاده از نام‌های چندکلمه‌ای معمولاً توصیه نمی‌شود، اما در صورت نیاز می‌توانید کلمات را به هم بچسبانید  
    یا از camel case استفاده کنید (`org.example.myProject`).
- نام کلاس‌ها و objectها از CamelCase بزرگ استفاده می‌کنند:

```kotlin
open class DeclarationProcessor { /*...*/ }

object EmptyDeclarationProcessor : DeclarationProcessor() { /*...*/ }
```

### نام توابع

نام توابع، پراپرتی‌ها و متغیرهای محلی با حرف کوچک شروع می‌شود و از camel case بدون underscore استفاده می‌کند:

```kotlin
fun processDeclarations() { /*...*/ }
var declarationCount = 1
```

استثنا: توابع factory که برای ایجاد نمونه از کلاس‌ها استفاده می‌شوند می‌توانند همان نام نوع بازگشتی انتزاعی را داشته باشند:

```kotlin
interface Foo { /*...*/ }

class FooImpl : Foo { /*...*/ }

fun Foo(): Foo { return FooImpl() }
```

### ### نام متدهای تست

در تست‌ها (و **فقط** در تست‌ها)، می‌توانید از نام متدهایی با فاصله استفاده کنید که داخل backtick قرار می‌گیرند.  
توجه داشته باشید که این نوع نام‌گذاری فقط از API level 30 به بعد در Android runtime پشتیبانی می‌شود.  
همچنین استفاده از underscore در نام متدها در کد تست مجاز است.

```kotlin
class MyTestCase {
    @Test fun `ensure everything works`() { /*...*/ }

    @Test fun ensureEverythingWorks_onAndroid() { /*...*/ }
}
```

### نام پراپرتی‌ها

نام ثابت‌ها (پراپرتی‌های علامت‌گذاری‌شده با `const`، یا پراپرتی‌های `val` سطح‌بالا یا object بدون getter سفارشی  
که داده‌های کاملاً immutable نگه می‌دارند) باید با حروف بزرگ و underscore جدا شوند و از  
[screaming snake case](https://en.wikipedia.org/wiki/Snake_case) پیروی کنند:

```kotlin
const val MAX_COUNT = 8
val USER_NAME_FIELD = "UserName"
```

نام پراپرتی‌های سطح‌بالا یا object که اشیایی با رفتار یا دادهٔ mutable نگه می‌دارند باید از camel case استفاده کنند:

```kotlin
val mutableCollection: MutableSet<String> = HashSet()
```

نام پراپرتی‌هایی که به singletonها اشاره می‌کنند می‌توانند از همان سبک نام‌گذاری اعلان‌های `object` استفاده کنند:

```kotlin
val PersonComparator: Comparator<Person> = /*...*/
```

برای ثابت‌های enum، استفاده از نام‌های کاملاً بزرگ با underscore  
(`enum class Color { RED, GREEN }`) یا CamelCase بزرگ، بسته به کاربرد، هر دو قابل قبول است.

### نام پراپرتی‌های پشتیبان (backing properties)

اگر یک کلاس دو پراپرتی داشته باشد که از نظر مفهومی یکسان‌اند اما یکی بخشی از API عمومی است  
و دیگری جزئیات پیاده‌سازی، از underscore به‌عنوان پیشوند برای پراپرتی private استفاده کنید:

```kotlin
class C {
    private val _elementList = mutableListOf<Element>()

    val elementList: List<Element>
        get() = _elementList
}
```

### انتخاب نام‌های خوب

نام کلاس معمولاً یک اسم یا عبارت اسمی است که توضیح می‌دهد کلاس «چیست»: `List`، `PersonReader`.

نام متد معمولاً یک فعل یا عبارت فعلی است که توضیح می‌دهد متد «چه کاری انجام می‌دهد»: `close`، `readPersons`.  
نام باید مشخص کند که آیا متد شیء را تغییر می‌دهد یا یک شیء جدید برمی‌گرداند.  
برای مثال، `sort` یک مجموعه را درجا مرتب می‌کند، در حالی که `sorted` یک نسخهٔ مرتب‌شدهٔ جدید برمی‌گرداند.

نام‌ها باید هدف موجودیت را به‌وضوح بیان کنند، بنابراین بهتر است از واژه‌های بی‌معنی  
(`Manager`، `Wrapper`) در نام‌ها اجتناب کنید.

وقتی از یک مخفف در نام اعلان استفاده می‌کنید، این قوانین را دنبال کنید:

- برای مخفف‌های دوحرفی، هر دو حرف را بزرگ بنویسید. مثال: `IOStream`.
- برای مخفف‌های طولانی‌تر از دو حرف، فقط حرف اول را بزرگ بنویسید. مثال: `XmlFormatter` یا `HttpInputStream`.
    

## قالب‌بندی

### تورفتگی (Indentation)

از چهار فاصله (space) برای تورفتگی استفاده کنید. از tab استفاده نکنید.

برای آکولادها، آکولاد باز را در انتهای خطی قرار دهید که سازه شروع می‌شود و آکولاد بسته را  
در خطی جداگانه و هم‌تراز با شروع سازه قرار دهید.

```kotlin
if (elements != null) {
    for (element in elements) {
        // ...
    }
}
```

> در کاتلین، سمی‌کالن‌ها اختیاری هستند و بنابراین شکست خط‌ها اهمیت دارند. طراحی زبان  
> بر پایهٔ آکولادهای سبک جاوا است و اگر از سبک قالب‌بندی متفاوتی استفاده کنید،  
> ممکن است با رفتارهای غیرمنتظره مواجه شوید.

{style="note"}

### فاصله‌گذاری افقی

- اطراف عملگرهای دوتایی فاصله بگذارید (`a + b`). استثنا: اطراف عملگر بازه (`0..i`) فاصله نگذارید.
- اطراف عملگرهای یک‌تایی فاصله نگذارید (`a++`).
- بین کلیدواژه‌های کنترل جریان (`if`، `when`، `for`، `while`) و پرانتز باز فاصله بگذارید.
- قبل از پرانتز باز در اعلان سازندهٔ اصلی، اعلان متد یا فراخوانی متد فاصله نگذارید.

```kotlin
class A(val x: Int)

fun foo(x: Int) { ... }

fun bar() {
    foo(1)
}
```

- هرگز بعد از `(` یا `[` و قبل از `]` یا `)` فاصله نگذارید.
- اطراف `.` یا `?.` فاصله نگذارید: `foo.bar().filter { it > 2 }.joinToString()`، `foo?.bar()`.
- بعد از `//` یک فاصله بگذارید: `// This is a comment`.
- اطراف براکت‌های زاویه‌ای در پارامترهای نوع فاصله نگذارید: `class Map<K, V> { ... }`.
- اطراف `::` فاصله نگذارید: `Foo::class`، `String::length`.
- قبل از `?` در نوع nullable فاصله نگذارید: `String?`.

به‌طور کلی، از هرگونه تراز افقی اجتناب کنید. تغییر نام یک شناسه به نامی با طول متفاوت  
نباید قالب‌بندی اعلان یا استفاده‌های آن را تغییر دهد.

### دونقطه (:)

در موارد زیر قبل از `:` فاصله بگذارید:

- وقتی برای جدا کردن نوع و supertype استفاده می‌شود.
- هنگام واگذاری به سازندهٔ کلاس والد یا سازندهٔ دیگر همان کلاس.
- بعد از کلیدواژهٔ `object`.

وقتی `:` بین اعلان و نوع آن قرار می‌گیرد، قبل از آن فاصله نگذارید.

همیشه بعد از `:` یک فاصله بگذارید.

```kotlin
abstract class Foo<out T : Any> : IFoo {
    abstract fun foo(a: Int): T
}

class FooImpl : Foo() {
    constructor(x: String) : this(x) { /*...*/ }

    val x = object : IFoo { /*...*/ } 
}
```

### هدر کلاس‌ها

کلاس‌هایی با پارامترهای کم در سازندهٔ اصلی می‌توانند در یک خط نوشته شوند:

```kotlin
class Person(id: Int, name: String)
```

کلاس‌هایی با هدر طولانی‌تر باید طوری قالب‌بندی شوند که هر پارامتر سازنده در یک خط جداگانه با تورفتگی باشد.  
همچنین پرانتز بسته باید در خطی جدید قرار گیرد. اگر از وراثت استفاده می‌کنید، فراخوانی سازندهٔ والد یا  
فهرست اینترفیس‌ها باید در همان خط پرانتز بسته قرار گیرد:

```kotlin
class Person(
    id: Int,
    name: String,
    surname: String
) : Human(id, name) { /*...*/ }
```

برای چند اینترفیس، فراخوانی سازندهٔ والد ابتدا قرار می‌گیرد و سپس هر اینترفیس در یک خط جداگانه:

```kotlin
class Person(
    id: Int,
    name: String,
    surname: String
) : Human(id, name),
    KotlinMaker { /*...*/ }
```

برای کلاس‌هایی با فهرست supertype طولانی، بعد از دونقطه شکست خط ایجاد کنید و همهٔ نام‌ها را هم‌تراز کنید:

```kotlin
class MyFavouriteVeryLongClassHolder :
    MyLongHolder<MyFavouriteVeryLongClass>(),
    SomeOtherInterface,
    AndAnotherOne {

    fun foo() { /*...*/ }
}
```

برای جدا کردن واضح هدر کلاس و بدنه وقتی هدر طولانی است، یا یک خط خالی بعد از هدر قرار دهید  
(مانند مثال بالا) یا آکولاد باز را در خطی جداگانه بگذارید:

```kotlin
class MyFavouriteVeryLongClassHolder :
    MyLongHolder<MyFavouriteVeryLongClass>(),
    SomeOtherInterface,
    AndAnotherOne 
{
    fun foo() { /*...*/ }
}
```

برای پارامترهای سازنده از تورفتگی معمول (چهار فاصله) استفاده کنید تا پراپرتی‌های سازنده  
هم‌تورفتگی پراپرتی‌های بدنهٔ کلاس را داشته باشند.

### ترتیب modifierها

اگر یک اعلان چند modifier دارد، همیشه آن‌ها را به ترتیب زیر بنویسید:

```kotlin
public / protected / private / internal
expect / actual
final / open / abstract / sealed / const
external
override
lateinit
tailrec
vararg
suspend
inner
enum / annotation / fun // as a modifier in `fun interface` 
companion
inline / value
infix
operator
data
```

همهٔ annotationها را قبل از modifierها قرار دهید:

```kotlin
@Named("Foo")
private val foo: Foo
```

مگر اینکه در حال نوشتن یک کتابخانه باشید، modifierهای زائد (مثل `public`) را حذف کنید.

### Annotationها

در Annotationها را در خطوط جداگانه قبل از اعلان مربوطه و با همان تورفتگی قرار دهید:

```kotlin
@Target(AnnotationTarget.PROPERTY)
annotation class JsonExclude
```

در Annotationهای بدون آرگومان می‌توانند در همان خط قرار گیرند:

```kotlin
@JsonExclude @JvmField
var x: String
```

یک annotation تکی بدون آرگومان می‌تواند در همان خط اعلان قرار گیرد:

```kotlin
@Test fun foo() { /*...*/ }
```

### Annotationهای فایل

در Annotationهای فایل بعد از کامنت فایل (در صورت وجود) و قبل از عبارت `package` قرار می‌گیرند  
و با یک خط خالی از `package` جدا می‌شوند (برای تأکید بر اینکه هدف آن‌ها فایل است نه پکیج).

```kotlin
/** License, copyright and whatever */
@file:JvmName("FooBar")

package foo.bar
```

### توابع

اگر امضای تابع در یک خط جا نمی‌شود، از نحو زیر استفاده کنید:

```kotlin
fun longMethodName(
    argument: ArgumentType = defaultValue,
    argument2: AnotherArgumentType,
): ReturnType {
    // body
}
```

برای پارامترهای تابع از تورفتگی معمول (چهار فاصله) استفاده کنید تا با پارامترهای سازنده سازگار باشد.

برای توابعی که بدنهٔ آن‌ها فقط یک عبارت است، از expression body استفاده کنید:

```kotlin
fun foo(): Int {     // bad
    return 1 
}

fun foo() = 1        // good
```

### بدنه‌های عبارتی (Expression bodies)

اگر تابع دارای بدنهٔ عبارتی است و خط اول آن در همان خط اعلان جا نمی‌شود،  
علامت `=` را در خط اول بگذارید و بدنه را چهار فاصله تورفته کنید:

```kotlin
fun f(x: String, y: String, z: String) =
    veryLongFunctionCallWithManyWords(andLongParametersToo(), x, y, z)
```

### پراپرتی‌ها

برای پراپرتی‌های بسیار سادهٔ فقط‌خواندنی، قالب‌بندی تک‌خطی را در نظر بگیرید:

```kotlin
val isEmpty: Boolean get() = size == 0
```

برای پراپرتی‌های پیچیده‌تر، همیشه `get` و `set` را در خطوط جداگانه قرار دهید:

```kotlin
val foo: String
    get() { /*...*/ }
```

برای پراپرتی‌هایی با مقداردهی اولیهٔ طولانی، بعد از `=` شکست خط ایجاد کنید  
و مقداردهی اولیه را چهار فاصله تورفته کنید:

```kotlin
private val defaultCharset: Charset? =
    EncodingRegistry.getInstance().getDefaultCharsetForPropertiesFiles(file)
```

### دستورات کنترل جریان

اگر شرط یک دستور `if` یا `when` چندخطی است، همیشه از آکولاد برای بدنه استفاده کنید.  
هر خط بعدی شرط را نسبت به شروع دستور چهار فاصله تورفته کنید.  
پرانتز بستهٔ شرط را همراه با آکولاد باز در یک خط جداگانه قرار دهید:

```kotlin
if (!component.isSyncing &&
    !hasAnyKotlinRuntimeInScope(module)
) {
    return createKotlinNotConfiguredPanel(module)
}
```

کلیدواژه‌های `else`، `catch`، `finally` و همچنین `while` در حلقهٔ `do-while`  
را در همان خط آکولاد بستهٔ قبلی قرار دهید:

```kotlin
if (condition) {
    // body
} else {
    // else part
}

try {
    // body
} finally {
    // cleanup
}
```

در دستور `when`، اگر یک شاخه بیش از یک خط است، برای خوانایی آن را با یک خط خالی  
از شاخه‌های مجاور جدا کنید:

```kotlin
private fun parsePropertyValue(propName: String, token: Token) {
    when (token) {
        is Token.ValueToken ->
            callback.visitValue(propName, token.value)

        Token.LBRACE -> { // ...
        }
    }
}
```

شاخه‌های کوتاه را بدون آکولاد در همان خط شرط قرار دهید:

```kotlin
when (foo) {
    true -> bar() // good
    false -> { baz() } // bad
}
```

### فراخوانی متدها

در فهرست آرگومان‌های طولانی، بعد از پرانتز باز شکست خط ایجاد کنید.  
آرگومان‌ها را چهار فاصله تورفته کنید و آرگومان‌های مرتبط را در یک خط گروه‌بندی کنید:

```kotlin
drawSquare(
    x = 10, y = 10,
    width = 100, height = 100,
    fill = true
)
```

اطراف علامت `=` بین نام آرگومان و مقدار آن فاصله بگذارید.

### شکستن زنجیرهٔ فراخوانی‌ها

هنگام شکستن زنجیرهٔ فراخوانی‌ها، کاراکتر `.` یا عملگر `?.` را در خط بعدی  
و با یک تورفتگی قرار دهید:

```kotlin
val anchor = owner
    ?.firstChild!!
    .siblings(forward = true)
    .dropWhile { it is PsiComment || it is PsiWhiteSpace }
```

معمولاً اولین فراخوانی در زنجیره یک شکست خط قبل از خود دارد،  
اما اگر کد خواناتر می‌شود، حذف آن اشکالی ندارد.

### لامبداها

در عبارات لامبدا، اطراف آکولادها و اطراف فلش (`->`) فاصله بگذارید.  
اگر یک فراخوانی فقط یک لامبدا می‌گیرد، تا حد امکان آن را خارج از پرانتز ارسال کنید:

```kotlin
list.filter { it > 10 }
```

اگر برای لامبدا برچسب (label) تعیین می‌کنید، بین label و آکولاد باز فاصله نگذارید:

```kotlin
fun foo() {
    ints.forEach lit@{
        // ...
    }
}
```

در لامبداهای چندخطی، نام پارامترها را در خط اول بگذارید،  
سپس فلش و خط جدید:

```kotlin
appendCommaSeparated(properties) { prop ->
    val propertyValue = prop.get(obj)  // ...
}
```

اگر فهرست پارامترها خیلی طولانی است، فلش را در خط جداگانه قرار دهید:

```kotlin
foo {
    context: Context,
    environment: Env
    ->
    context.configureEnv(environment)
}
```

### کامای انتهایی (Trailing commas)

کامای انتهایی، کامایی است که بعد از آخرین عنصر در یک فهرست قرار می‌گیرد:

```kotlin
class Person(
    val firstName: String,
    val lastName: String,
    val age: Int, // trailing comma
)
```

استفاده از کامای انتهایی (trailing comma) چند مزیت دارد:

- تفاوت‌های نسخه‌سازی (diff) در سیستم کنترل نسخه را تمیزتر می‌کند — چون تمام تمرکز روی مقدار تغییرکرده است.
- اضافه کردن و تغییر ترتیب عناصر را آسان می‌کند — چون وقتی عناصر را جابه‌جا می‌کنید لازم نیست کاما را اضافه یا حذف کنید.
- تولید کد را ساده‌تر می‌کند؛ مثلاً برای مقداردهی اولیهٔ آبجکت‌ها. عنصر آخر هم می‌تواند کاما داشته باشد.

کاماهای انتهایی کاملاً اختیاری هستند — کد شما بدون آن‌ها هم درست کار می‌کند. راهنمای سبک کاتلین استفاده از کامای انتهایی را در محل اعلان (declaration site) تشویق می‌کند و در محل فراخوانی (call site) آن را به اختیار شما می‌گذارد.

برای فعال کردن کامای انتهایی در formatterِ IntelliJ IDEA، به **Settings/Preferences | Editor | Code Style | Kotlin** بروید،  
تب **Other** را باز کنید و گزینهٔ **Use trailing comma** را انتخاب کنید.

Enumerationها

```kotlin
enum class Direction {
    NORTH,
    SOUTH,
    WEST,
    EAST, // trailing comma
}
```

#### آرگومان‌های مقدار (Value arguments)

```kotlin
fun shift(x: Int, y: Int) { /*...*/ }
shift(
    25,
    20, // trailing comma
)
val colors = listOf(
    "red",
    "green",
    "blue", // trailing comma
)
```

#### پراپرتی‌ها و پارامترهای کلاس

```kotlin
class Customer(
    val name: String,
    val lastName: String, // trailing comma
)
class Customer(
    val name: String,
    lastName: String, // trailing comma
)
```

#### پارامترهای مقدار در تابع

```kotlin
fun powerOf(
    number: Int, 
    exponent: Int, // trailing comma
) { /*...*/ }
constructor(
    x: Comparable<Number>,
    y: Iterable<Number>, // trailing comma
) {}
fun print(
    vararg quantity: Int,
    description: String, // trailing comma
) {}
```

#### پارامترها با نوع اختیاری (شامل setterها)

```kotlin
val sum: (Int, Int, Int) -> Int = fun(
    x,
    y,
    z, // trailing comma
): Int {
    return x + y + x
}
println(sum(8, 8, 8))
```

#### پسوند ایندکس‌گذاری (Indexing suffix)

```kotlin
class Surface {
    operator fun get(x: Int, y: Int) = 2 * x + 4 * y - 10
}
fun getZValue(mySurface: Surface, xValue: Int, yValue: Int) =
    mySurface[
        xValue,
        yValue, // trailing comma
    ]
```

#### پارامترها در لامبداها

```kotlin
fun main() {
    val x = {
            x: Comparable<Number>,
            y: Iterable<Number>, // trailing comma
        ->
        println("1")
    }
    println(x)
}
```

#### ورودی

```kotlin
fun isReferenceApplicable(myReference: KClass<*>) = when (myReference) {
    Comparable::class,
    Iterable::class,
    String::class, // trailing comma
        -> true
    else -> false
}
```

#### لیترال‌های مجموعه (در annotationها)

```kotlin
annotation class ApplicableFor(val services: Array<String>)
@ApplicableFor([
    "serializer",
    "balancer",
    "database",
    "inMemoryCache", // trailing comma
])
fun run() {}
```

#### آرگومان‌های نوع (Type arguments)

```kotlin
fun <T1, T2> foo() {}
fun main() {
    foo<
            Comparable<Number>,
            Iterable<Number>, // trailing comma
            >()
}
```

#### پارامترهای نوع (Type parameters)

```kotlin
class MyMap<
        MyKey,
        MyValue, // trailing comma
        > {}
```

#### اعلان‌های destructuring 

```kotlin
data class Car(val manufacturer: String, val model: String, val year: Int)
val myCar = Car("Tesla", "Y", 2019)
val (
    manufacturer,
    model,
    year, // trailing comma
) = myCar
val cars = listOf<Car>()
fun printMeanValue() {
    var meanValue: Int = 0
    for ((
        _,
        _,
        year, // trailing comma
    ) in cars) {
        meanValue += year
    }
    println(meanValue/cars.size)
}
printMeanValue()
```

## کامنت‌های مستندسازی (Documentation comments)

برای کامنت‌های مستندسازی طولانی‌تر، `/**` آغازین را در یک خط جداگانه قرار دهید و هر خط بعدی را با یک ستاره شروع کنید:

```kotlin
/**
 * This is a documentation comment
 * on multiple lines.
 */
```

کامنت‌های کوتاه می‌توانند در یک خط قرار گیرند:

```kotlin
/** This is a short documentation comment. */
```

به‌طور کلی، از تگ‌های `@param` و `@return` اجتناب کنید. در عوض، توضیح پارامترها و مقدار بازگشتی را  
مستقیماً داخل کامنت مستندسازی بیاورید و هرجا از پارامترها نام بردید، به آن‌ها لینک بدهید.  
از `@param` و `@return` فقط وقتی استفاده کنید که توضیح طولانی باشد و در متن اصلی جا نشود.

```kotlin
// از این کار پرهیز کنید:

/**
 * مقدار مطلق عدد داده‌شده را برمی‌گرداند.
 * @param number عددی که باید مقدار مطلقش برگردانده شود.
 * @return مقدار مطلق.
 */
fun abs(number: Int): Int { /*...*/ }

// به جای آن این کار را انجام دهید:

/**
 * مقدار مطلق [number] داده‌شده را برمی‌گرداند.
 */
fun abs(number: Int): Int { /*...*/ }

```

## ## از سازه‌های زائد اجتناب کنید

به‌طور کلی، اگر یک سازهٔ نحوی در کاتلین اختیاری است و IDE آن را به‌عنوان مورد زائد علامت می‌زند،  
باید آن را از کد حذف کنید. عناصر نحوی غیرضروری را فقط برای «وضوح» در کد نگه ندارید.

### نوع بازگشتی Unit

اگر تابعی `Unit` برمی‌گرداند، نوع بازگشتی باید حذف شود:

```kotlin
fun foo() { // ": Unit" is omitted here

}
```

### سمی‌کالن‌ها

تا حد ممکن سمی‌کالن‌ها را حذف کنید.

### قالب‌های رشته‌ای (String templates)

وقتی یک متغیر ساده را داخل قالب رشته‌ای قرار می‌دهید از آکولاد استفاده نکنید. فقط برای عبارت‌های طولانی‌تر از آکولاد استفاده کنید:

```kotlin
println("$name has ${children.size} children")
```

از [multi-dollar string interpolation](strings.md#multi-dollar-string-interpolation)  
استفاده کنید تا کاراکتر `$` به‌عنوان متن معمولی در رشته در نظر گرفته شود:

```kotlin
val KClass<*>.jsonSchema : String
    get() = $$"""
        {
            "$schema": "https://json-schema.org/draft/2020-12/schema",
            "$id": "https://example.com/product.schema.json",
            "$dynamicAnchor": "meta",
            "title": "$${simpleName ?: qualifiedName ?: "unknown"}",
            "type": "object"
        }
        """
```

## استفادهٔ idiomatic از قابلیت‌های زبان

### تغییرناپذیری (Immutability)

به استفاده از داده‌های immutable نسبت به mutable ترجیح بدهید. همیشه متغیرهای محلی و پراپرتی‌ها را تا زمانی که بعد از مقداردهی اولیه تغییر نمی‌کنند  
به‌جای `var` با `val` اعلان کنید.

همیشه از اینترفیس‌های immutable مجموعه‌ها (`Collection`، `List`، `Set`، `Map`) برای اعلان مجموعه‌هایی استفاده کنید  
که تغییر داده نمی‌شوند. هنگام استفاده از توابع کارخانه‌ای برای ساخت نمونهٔ مجموعه‌ها، تا حد امکان از توابعی استفاده کنید  
که نوع‌های immutable برمی‌گردانند:

```kotlin
// بد: استفاده از نوع mutable برای مقداری که تغییر نخواهد کرد
fun validateValue(actualValue: String, allowedValues: HashSet<String>) { ... }

// خوب: استفاده از نوع immutable به جای آن
fun validateValue(actualValue: String, allowedValues: Set<String>) { ... }

// بد: arrayListOf() یک ArrayList<T> برمی‌گرداند که mutable است
val allowedValues = arrayListOf("a", "b", "c")

// خوب: listOf() یک List<T> برمی‌گرداند
val allowedValues = listOf("a", "b", "c")

```

### مقادیر پیش‌فرض پارامترها (Default parameter values)

به اعلان توابع با مقدار پیش‌فرض پارامترها نسبت به اعلان توابع overload شده ترجیح بدهید.

```kotlin
// Bad
fun foo() = foo("a")
fun foo(a: String) { /*...*/ }

// Good
fun foo(a: String = "a") { /*...*/ }
```

### ### نام مستعار نوع‌ها (Type aliases)

اگر یک نوع تابعی یا یک نوع با پارامترهای نوع دارید که چند بار در کد استفاده می‌شود، تعریف type alias را ترجیح بدهید:

```kotlin
typealias MouseClickHandler = (Any, MouseEvent) -> Unit
typealias PersonIndex = Map<String, Person>
```
اگر از type alias خصوصی یا داخلی برای جلوگیری از تداخل نام استفاده می‌کنید، رویکرد `import ... as ...` را که در  
[Packages and Imports](packages.md) آمده است ترجیح بدهید.

### پارامترهای لامبدا

در لامبداهایی که کوتاه هستند و تو‌در‌تو نیستند، توصیه می‌شود از قرارداد `it` به‌جای اعلان صریح پارامتر استفاده کنید.  
در لامبداهای تو‌در‌تو که پارامتر دارند، همیشه پارامترها را صریح اعلان کنید.

### returnها در لامبدا

از چندین return برچسب‌دار (labeled) در یک لامبدا اجتناب کنید. ساختار لامبدا را طوری بازنویسی کنید که یک نقطهٔ خروج داشته باشد.  
اگر این کار ممکن نیست یا به‌اندازهٔ کافی واضح نیست، لامبدا را به یک تابع بی‌نام (anonymous function) تبدیل کنید.

برای آخرین عبارت در لامبدا از labeled return استفاده نکنید.

### آرگومان‌های نام‌گذاری‌شده (Named arguments)

وقتی یک متد چند پارامتر از یک نوع primitive یکسان می‌گیرد، یا پارامترهای `Boolean` دارد، از نحو آرگومان نام‌گذاری‌شده استفاده کنید،  
مگر اینکه معنی همهٔ پارامترها از متن کاملاً واضح باشد.

```kotlin
drawSquare(x = 10, y = 10, width = 100, height = 100, fill = true)
```

### عبارات شرطی
به استفاده از شکل expression برای `try`، `if` و `when` ترجیح بدهید.

```kotlin
return if (x) foo() else bar()
```

```kotlin
return when(x) {
    0 -> "zero"
    else -> "nonzero"
}
```

این موارد بر حالت‌های زیر ترجیح دارند:

```kotlin
if (x)
    return foo()
else
    return bar()
```

```kotlin
when(x) {
    0 -> return "zero"
    else -> return "nonzero"
}
```

### if در برابر when

برای شرایط دوحالته، به‌جای `when` از `if` استفاده کنید.  
مثلاً این شکل با `if`:

```kotlin
if (x == null) ... else ...
```

به‌جای این شکل با `when`:

```kotlin
when (x) {
    null -> // ...
    else -> // ...
}
```

اگر سه گزینه یا بیشتر وجود دارد، `when` را ترجیح بدهید.

### شرط‌های نگهبان (Guard conditions) در when expression

هنگام ترکیب چند عبارت بولی در `when` (در حالت guard conditions)، از پرانتز استفاده کنید:

```kotlin
when (status) {
    is Status.Ok if (status.info.isEmpty() || status.info.id == null) -> "no information"
}
```

به‌جای:

```kotlin
when (status) {
    is Status.Ok if status.info.isEmpty() || status.info.id == null -> "no information"
}
```

### Booleanهای nullable در شرط‌ها

اگر لازم است از `Boolean?` در شرط استفاده کنید، از بررسی‌های `if (value == true)` یا `if (value == false)` استفاده کنید.

### حلقه‌ها (Loops)

به استفاده از توابع مرتبه‌بالا (`filter`، `map` و غیره) نسبت به حلقه‌ها ترجیح بدهید. استثنا: `forEach`  
(مگر اینکه گیرندهٔ `forEach` nullable باشد یا `forEach` بخشی از یک زنجیرهٔ طولانی‌تر باشد؛ در غیر این صورت، حلقهٔ `for` معمولی را ترجیح بدهید).

وقتی بین یک عبارت پیچیده با چند تابع مرتبه‌بالا و یک حلقه انتخاب می‌کنید، هزینهٔ عملیات را در هر حالت درک کنید  
و ملاحظات کارایی را در نظر داشته باشید.

### حلقه روی بازه‌ها (Ranges)

برای حلقه روی یک بازهٔ باز، از عملگر `..<` استفاده کنید:

```kotlin
for (i in 0..n - 1) { /*...*/ }  // bad
for (i in 0..<n) { /*...*/ }  // good
```

### رشته‌ها (Strings)

به قالب‌های رشته‌ای نسبت به الحاق رشته‌ها (string concatenation) ترجیح بدهید.

به رشته‌های چندخطی نسبت به جاسازی `\n` در رشته‌های معمولی ترجیح بدهید.

برای حفظ تورفتگی در رشته‌های چندخطی، از `trimIndent` استفاده کنید وقتی خروجی نیازی به تورفتگی داخلی ندارد،  
یا از `trimMargin` وقتی تورفتگی داخلی لازم است:

```kotlin
fun main() {
//sampleStart
    println("""
     Not
     trimmed
     text
     """
    )

    println("""
     Trimmed
     text
     """.trimIndent()
    )

    println()

    val a = """Trimmed to margin text:
            |if(a > 1) {
            |    return a
            |}""".trimMargin()

   println(a)
//sampleEnd
}
```
{kotlin-runnable="true"}
تفاوت بین [Java and Kotlin multiline strings](java-to-kotlin-idioms-strings.md#use-multiline-strings) را یاد بگیرید.

### تابع در برابر پراپرتی

در برخی سناریوها، توابع بدون آرگومان ممکن است با پراپرتی‌های فقط‌خواندنی قابل جایگزینی باشند.  
با اینکه معنا مشابه است، قراردادهای سبکی وجود دارد که مشخص می‌کند کِی پراپرتی را به تابع ترجیح بدهید.

پراپرتی را به تابع ترجیح بدهید وقتی الگوریتم زیرین:

- خطا (exception) پرتاب نمی‌کند.
- محاسبه‌اش ارزان است (یا در اولین اجرا cache می‌شود).
- تا وقتی وضعیت شیء تغییر نکرده، در فراخوانی‌های مختلف همان نتیجه را برمی‌گرداند.

### توابع extension

از توابع extension زیاد استفاده کنید. هر وقت تابعی عمدتاً روی یک شیء کار می‌کند،  
آن را به شکل extension function با receiver همان شیء در نظر بگیرید.  
برای کم کردن آلودگی API، سطح دسترسی توابع extension را تا جای ممکن محدود کنید.  
در صورت نیاز، از extensionهای محلی، extensionهای عضو، یا extensionهای سطح‌بالا با visibility خصوصی استفاده کنید.

### توابع infix

فقط وقتی یک تابع را `infix` اعلام کنید که روی دو شیء کار می‌کند که نقش مشابهی دارند.  
نمونه‌های خوب: `and`، `to`، `zip`.  
نمونهٔ بد: `add`.

اگر متدی receiver را تغییر می‌دهد، آن را `infix` اعلام نکنید.

### توابع factory

اگر برای یک کلاس تابع factory تعریف می‌کنید، از دادن همان نام کلاس به آن خودداری کنید.  
نامی متمایز را ترجیح بدهید که روشن کند چرا رفتار تابع factory خاص است.  
فقط اگر واقعاً معنای ویژه‌ای وجود ندارد، می‌توانید از همان نام کلاس استفاده کنید.

```kotlin
class Point(val x: Double, val y: Double) {
    companion object {
        fun fromPolar(angle: Double, radius: Double) = Point(...)
    }
}
```

اگر یک شیء چند سازندهٔ overload شده دارد که سازنده‌های متفاوتِ superclass را فراخوانی نمی‌کنند  
و قابل کاهش به یک سازنده با پارامترهای پیش‌فرض نیستند، بهتر است آن سازنده‌های overload را با توابع factory جایگزین کنید.

### نوع‌های پلتفرمی (Platform types)

یک تابع/متد عمومی که عبارتی از نوع پلتفرمی برمی‌گرداند باید نوع کاتلین خود را صریح مشخص کند:

```kotlin
fun apiCall(): String = MyJavaApi.getProperty("name")
```

هر پراپرتی (سطح پکیج یا سطح کلاس) که با عبارتی از نوع پلتفرمی مقداردهی اولیه می‌شود باید نوع کاتلین خود را صریح مشخص کند:

```kotlin
class Person {
    val name: String = MyJavaApi.getProperty("name")
}
```

یک مقدار محلی که با عبارتی از نوع پلتفرمی مقداردهی اولیه می‌شود می‌تواند نوع داشته باشد یا نداشته باشد:

```kotlin
fun main() {
    val name = MyJavaApi.getProperty("name")
    println(name)
}
```

### توابع scope: apply/with/run/also/let

کاتلین مجموعه‌ای از توابع فراهم می‌کند تا یک بلوک کد را در کانتکست یک شیء اجرا کنید: `let`، `run`، `with`، `apply` و `also`.  
برای راهنمای انتخاب تابع مناسب، به [Scope Functions](scope-functions.md) مراجعه کنید.

## قراردادهای کدنویسی برای کتابخانه‌ها

هنگام نوشتن کتابخانه‌ها، توصیه می‌شود از مجموعه قوانین اضافی زیر پیروی کنید تا پایداری API تضمین شود:

- همیشه سطح دسترسی اعضا را صریح مشخص کنید (تا اعلان‌ها به‌طور ناخواسته به API عمومی تبدیل نشوند).
- همیشه نوع بازگشتی توابع و نوع پراپرتی‌ها را صریح مشخص کنید (تا با تغییر پیاده‌سازی، نوع بازگشتی ناخواسته تغییر نکند).
- برای همهٔ اعضای عمومی، کامنت‌های [KDoc](kotlin-doc.md) بنویسید، به‌جز overrideهایی که به مستندسازی جدید نیاز ندارند  
    (برای پشتیبانی از تولید مستندات کتابخانه).

برای یادگیری بیشتر دربارهٔ بهترین روش‌ها و ایده‌هایی که هنگام طراحی API کتابخانه باید در نظر بگیرید،  
بخش [Library authors' guidelines](api-guidelines-introduction.md) را ببینید.
