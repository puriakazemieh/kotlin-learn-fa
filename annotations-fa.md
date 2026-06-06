[//]: # (title: Annotations)




و Annotationها ابزاری برای الصاق متادیتا به کد هستند. برای تعریف یک annotation، modifier `annotation` را قبل از یک کلاس قرار دهید:

```kotlin
annotation class Fancy
```

ویژگی‌های اضافی آنوتیشن را می‌توان با آنوتِیت کردن کلاسِ آنوتیشن توسط «متا-آنوتیشن‌ها» (meta-annotations) مشخص کرد:

- در واقع [`@Target`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.annotation/-target/index.html) انواع عناصری که می‌توانند با این آنوتیشن نشانه‌گذاری شوند را مشخص می‌کند (مانند کلاس‌ها، توابع، ویژگی‌ها و عبارت‌ها)؛
- در واقع [`@Retention`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.annotation/-retention/index.html) مشخص می‌کند که آیا آنوتیشن در فایل‌های کلاسِ کامپایل شده ذخیره شود و آیا در زمان اجرا از طریق reflection قابل مشاهده باشد یا خیر (به‌طور پیش‌فرض، هر دو مورد true هستند)؛
- در واقع [`@Repeatable`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.annotation/-repeatable/index.html) اجازه می‌دهد تا از یک آنوتیشن بر روی یک عنصر واحد به دفعات استفاده شود؛
- در واقع [`@MustBeDocumented`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.annotation/-must-be-documented/index.html) مشخص می‌کند که آنوتیشن بخشی از API عمومی است و باید در امضای کلاس یا متد که در مستندات تولید شده API نشان داده می‌شود، گنجانده شود.

```kotlin
@Target(AnnotationTarget.CLASS, AnnotationTarget.FUNCTION,
        AnnotationTarget.TYPE_PARAMETER, AnnotationTarget.VALUE_PARAMETER,
        AnnotationTarget.EXPRESSION)
@Retention(AnnotationRetention.SOURCE)
@MustBeDocumented
annotation class Fancy
```

## نحوه استفاده

```kotlin
@Fancy class Foo {
    @Fancy fun baz(@Fancy foo: Int): Int {
        return (@Fancy 1)
    }
}
```

اگر نیاز دارید سازنده اصلی (primary constructor) یک کلاس را آنوتِیت کنید، باید کلمه کلیدی `constructor` را به اعلان سازنده اضافه کرده و آنوتیشن‌ها را قبل از آن قرار دهید:

```kotlin
class Foo @Inject constructor(dependency: MyDependency) { ... }
```

همچنین می‌توانید اکسسورهای ویژگی (property accessors) را آنوتِیت کنید:

```kotlin
class Foo {
    var x: MyDependency? = null
        @Inject set
}
```

## سازنده‌ها (Constructors)

آنوتیشن‌ها می‌توانند سازنده‌هایی داشته باشند که پارامتر می‌گیرند.

```kotlin
annotation class Special(val why: String)

@Special("example") class Foo {}
```

انواع پارامترهای مجاز عبارتند از:

- انواعی که متناظر با انواع اولیه (primitive) در جاوا هستند (مانند Int، Long و غیره)
- رشته‌ها (Strings)
- کلاس‌ها (`Foo::class`)
- Enumها
- سایر آنوتیشن‌ها
- آرایه‌هایی از انواع لیست شده در بالا

پارامترهای آنوتیشن نمی‌توانند انواع نال‌پذیر (nullable) داشته باشند، زیرا JVM از ذخیره `null` به عنوان مقدار یک صفتِ آنوتیشن پشتیبانی نمی‌کند.

اگر از یک آنوتیشن به عنوان پارامتر آنوتیشن دیگری استفاده شود، نام آن با کاراکتر `@` شروع نمی‌شود:

```kotlin
annotation class ReplaceWith(val expression: String)

annotation class Deprecated(
        val message: String,
        val replaceWith: ReplaceWith = ReplaceWith(""))

@Deprecated("This function is deprecated, use === instead", ReplaceWith("this === other"))
```

اگر نیاز دارید یک کلاس را به عنوان آرگومان یک آنوتیشن مشخص کنید، از یک کلاس کاتلین ([KClass](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.reflect/-k-class/index.html)) استفاده کنید. کامپایلر کاتلین به‌طور خودکار آن را به یک کلاس جاوا تبدیل می‌کند تا کد جاوا بتواند به‌طور معمول به آنوتیشن‌ها و آرگومان‌ها دسترسی داشته باشد.

```kotlin

import kotlin.reflect.KClass

annotation class Ann(val arg1: KClass<*>, val arg2: KClass<out Any>)

@Ann(String::class, Int::class) class MyClass
```

## نمونه‌سازی (Instantiation)

در جاوا، نوعِ آنوتیشن شکلی از یک اینترفیس است، بنابراین می‌توانید آن را پیاده‌سازی کرده و از یک نمونه (instance) استفاده کنید. به عنوان جایگزینی برای این مکانیزم، کاتلین به شما اجازه می‌دهد تا سازنده یک کلاس آنوتیشن را در کدهای دلخواه فراخوانی کرده و به‌طور مشابه از نمونه حاصل استفاده کنید.

```kotlin
annotation class InfoMarker(val info: String)

fun processInfo(marker: InfoMarker): Unit = TODO()

fun main(args: Array<String>) {
    if (args.isNotEmpty())
        processInfo(getAnnotationReflective(args))
    else
        processInfo(InfoMarker("default"))
}
```

درباره نمونه‌سازی کلاس‌های آنوتیشن در [این KEEP](https://github.com/Kotlin/KEEP/blob/master/proposals/annotation-instantiation.md) بیشتر بیاموزید.

## لامبداها (Lambdas)

آنوتیشن‌ها را می‌توان روی لامبداها نیز استفاده کرد. آن‌ها روی متد `invoke()` که بدنه لامبدا در آن تولید می‌شود، اعمال خواهند شد. این برای فریم‌ورک‌هایی مانند [Quasar](https://docs.paralleluniverse.co/quasar/) که از آنوتیشن‌ها برای کنترل همزمانی استفاده می‌کنند، مفید است.

```kotlin
annotation class Suspendable

val f = @Suspendable { Fiber.sleep(10) }
```

## اهداف محل استفاده از آنوتیشن (Annotation use-site targets)

هنگامی که یک ویژگی (property) یا یک پارامتر سازنده اصلی را آنوتِیت می‌کنید، عناصر جاوای متعددی از عنصر متناظر کاتلین تولید می‌شوند، و بنابراین مکان‌های احتمالی متعددی برای قرارگیری آنوتیشن در بایت‌کد جاوای تولید شده وجود دارد. برای تعیین دقیق نحوه تولید آنوتیشن، از نحو (syntax) زیر استفاده کنید:

```kotlin
class Example(
		@field:Ann val foo,          // فقط فیلد جاوا را آنوتِیت کن
         @get:Ann val bar,           // فقط getter جاوا را آنوتِیت کن
        @param:Ann val quux    // فقط پارامتر سازنده جاوا را آنوتِیت کن
        )   
```

همین نحو را می‌توان برای آنوتِیت کردن کل فایل استفاده کرد. برای این کار، یک آنوتیشن با هدف `file` را در بالاترین سطح فایل، قبل از دستور package یا قبل از تمام importها (اگر فایل در پکیج پیش‌فرض است) قرار دهید:

```kotlin
@file:JvmName("Foo")

package org.jetbrains.demo
```

اگر چندین آنوتیشن با هدف یکسان دارید، می‌توانید با اضافه کردن براکت بعد از هدف و قرار دادن تمام آنوتیشن‌ها داخل براکت، از تکرار هدف خودداری کنید (به جز برای متا-هدف `all`):

```kotlin
class Example {
     @set:[Inject VisibleForTesting]
     var collaborator: Collaborator
}
```

لیست کامل اهداف محل استفاده (use-site targets) پشتیبانی شده عبارت است از:

- `file`
- `field`
- `property` (آنوتیشن‌های با این هدف برای جاوا قابل مشاهده نیستند)
- `get` (گتر ویژگی)
- `set` (ستر ویژگی)
- `all` (یک متا-هدف آزمایشی برای ویژگی‌ها، برای هدف و نحوه استفاده [بخش پایین](#متا-هدف-all) را ببینید)
- `receiver` (پارامتر گیرنده یک تابع الحاقی یا ویژگی الحاقی)

    برای آنوتِیت کردن پارامتر گیرنده یک تابع الحاقی، از نحو زیر استفاده کنید

    ```kotlin
    fun @receiver:Fancy String.myExtension() { ... }
    ```

- `param` (پارامتر سازنده)
- `setparam` (پارامتر ستر ویژگی)
- `delegate` (فیلدی که نمونه delegate را برای یک ویژگی delegate شده ذخیره می‌کند)

### پیش‌فرض‌ها در صورت عدم تعیین هدف محل استفاده

اگر هدف محل استفاده را مشخص نکنید، هدف بر اساس آنوتیشن `@Target` از آنوتیشنی که استفاده می‌شود انتخاب می‌گردد. اگر چندین هدفِ قابل اعمال وجود داشته باشد، اولین هدفِ قابل اعمال از لیست زیر استفاده می‌شود:
- `param`
- `property`
- `field`

بیایید از [آنوتیشن `@Email` از Jakarta Bean Validation](https://jakarta.ee/specifications/bean-validation/3.0/apidocs/jakarta/validation/constraints/email) استفاده کنیم:

```java
@Target(value={METHOD,FIELD,ANNOTATION_TYPE,CONSTRUCTOR,PARAMETER,TYPE_USE})
public @interface Email { }
```

با این آنوتیشن، مثال زیر را در نظر بگیرید:

```kotlin
data class User(
	val username: String,// @Email معادل @param:Email است
    @Email val email: String
	     ) {
    // @Email معادل @field:Email است
    @Email val secondaryEmail: String? = null
}
```

کاتلین 2.2.0 یک قانون پیش‌فرض آزمایشی معرفی کرد که باید انتشار آنوتیشن‌ها به پارامترها، فیلدها و ویژگی‌ها را پیش‌بینی‌پذیرتر کند.

با قانون جدید، اگر چندین هدف قابل اعمال وجود داشته باشد، یک یا چند مورد به صورت زیر انتخاب می‌شوند:

- اگر هدف پارامتر سازنده (`param`) قابل اعمال باشد، استفاده می‌شود.
- اگر هدف ویژگی (`property`) قابل اعمال باشد، استفاده می‌شود.
- اگر هدف فیلد (`field`) در حالی که `property` قابل اعمال نیست، قابل اعمال باشد، `field` استفاده می‌شود.

با استفاده از همان مثال:

```kotlin
data class User(
		val username: String,// @Email اکنون معادل @param:Email @field:Email است
         @Email val email: String
         ) {
    // @Email هنوز معادل @field:Email است
    @Email val secondaryEmail: String? = null
}
```

اگر چندین هدف وجود داشته باشد و هیچ‌کدام از `param` ،`property` یا `field` قابل اعمال نباشند، آنوتیشن نامعتبر است.

برای فعال کردن قانون پیش‌فرض جدید، از خط زیر در تنظیمات Gradle خود استفاده کنید:

```kotlin
// build.gradle.kts
kotlin {
    compilerOptions {
        freeCompilerArgs.add("-Xannotation-default-target=param-property")
    }
}
```

هر زمان که بخواهید از رفتار قدیمی استفاده کنید، می‌توانید:

- در یک مورد خاص، هدف لازم را صریحاً مشخص کنید، مثلاً استفاده از `@param:Annotation` به جای `@Annotation`.
- برای کل پروژه، از این فلگ در فایل build گریدل خود استفاده کنید:

    ```kotlin
    // build.gradle.kts
    kotlin {
        compilerOptions {
            freeCompilerArgs.add("-Xannotation-default-target=first-only")
        }
    }
    ```

### متا-هدف `all`

<primary-label ref="experimental-opt-in"/>

هدف `all` اعمال یک آنوتیشن یکسان را نه تنها به پارامتر و ویژگی یا فیلد، بلکه به گتر و ستر متناظر نیز آسان‌تر می‌کند.

به‌طور خاص، آنوتیشن علامت‌گذاری شده با `all` در صورت امکان به موارد زیر منتشر می‌شود:

- به پارامتر سازنده (`param`) اگر ویژگی در سازنده اصلی تعریف شده باشد.
- به خود ویژگی (`property`).
- به فیلد پشتیبان (`field`) اگر ویژگی دارای آن باشد.
- به گتر (`get`).
- به پارامتر ستر (`setparam`) اگر ویژگی به صورت `var` تعریف شده باشد.
- به هدف مختص جاوای `RECORD_COMPONENT` اگر کلاس دارای آنوتیشن `@JvmRecord` باشد.

بیایید از [آنوتیشن `@Email` از Jakarta Bean Validation](https://jakarta.ee/specifications/bean-validation/3.0/apidocs/jakarta/validation/constraints/email) استفاده کنیم که به صورت زیر تعریف شده است:

```java
@Target(value={METHOD,FIELD,ANNOTATION_TYPE,CONSTRUCTOR,PARAMETER,TYPE_USE})
public @interface Email { }
```

در مثال زیر، این آنوتیشن `@Email` به تمام اهداف مربوطه اعمال می‌شود:

```kotlin
data class User(
    val username: String,
    // @Email را به param، field و get اعمال می‌کند
    @all:Email val email: String,
    // @Email را به param، field، get و setparam اعمال می‌کند
    @all:Email var name: String,
) {
    // @Email را به field و getter اعمال می‌کند (نه به param چون در سازنده نیست)
    @all:Email val secondaryEmail: String? = null
}
```

شما می‌توانید از متا-هدف `all` برای هر ویژگی، هم داخل و هم خارج از سازنده اصلی استفاده کنید.

#### محدودیت‌ها

هدف `all` با محدودیت‌هایی همراه است:

- آنوتیشن را به انواع (types)، گیرنده‌های احتمالی الحاقی (extension receivers)، یا گیرنده‌ها یا پارامترهای کانتکست (context receivers) منتشر نمی‌کند.
- نمی‌توان از آن با چندین آنوتیشن استفاده کرد:
    ```kotlin
    @all:[A B] // forbidden, use @all:A @all:B
    val x: Int = 5
    ```
- نمی‌توان از آن با [ویژگی‌های delegate شده](delegated-properties.md) استفاده کرد.

#### نحوه فعال‌سازی

برای فعال کردن متا-هدف `all` در پروژه خود، از گزینه کامپایلر زیر در خط فرمان استفاده کنید:

```Bash
-Xannotation-target-all
```

یا آن را به بلوک `compilerOptions {}` در فایل build گریدل خود اضافه کنید:

```kotlin
// build.gradle.kts
kotlin {
    compilerOptions {
        freeCompilerArgs.add("-Xannotation-target-all")
    }
}
```

## آنوتیشن‌های جاوا

آنوتیشن‌های جاوا ۱۰۰٪ با کاتلین سازگار هستند:

```kotlin
import org.junit.Test
import org.junit.Assert.*
import org.junit.Rule
import org.junit.rules.*

class Tests {
    // اعمال آنوتیشن @Rule به گترِ ویژگی
    @get:Rule val tempFolder = TemporaryFolder()

    @Test fun simple() {
        val f = tempFolder.newFile()
        assertEquals(42, getTheAnswer())
    }
}
```

از آنجایی که ترتیب پارامترها برای آنوتیشن نوشته شده در جاوا تعریف نشده است، نمی‌توانید از نحو فراخوانی معمولی تابع برای ارسال آرگومان‌ها استفاده کنید. در عوض، باید از نحو آرگومان‌های نام‌دار (named argument) استفاده کنید:

``` java
// Java
public @interface Ann {
    int intValue();
    String stringValue();
}
```

```kotlin
// Kotlin
@Ann(intValue = 1, stringValue = "abc") class C
```

درست مانند جاوا، یک مورد خاص پارامتر `value` است؛ مقدار آن را می‌توان بدون نام صریح مشخص کرد:

``` java
// Java
public @interface AnnWithValue {
    String value();
}
```

```kotlin
// Kotlin
@AnnWithValue("abc") class C
```

### آرایه‌ها به عنوان پارامترهای آنوتیشن

اگر آرگومان `value` در جاوا دارای نوع آرایه باشد، در کاتلین به یک پارامتر `vararg` تبدیل می‌شود:

``` java
// Java
public @interface AnnWithArrayValue {
    String[] value();
}
```

```kotlin
// Kotlin
@AnnWithArrayValue("abc", "foo", "bar") class C
```

برای سایر آرگومان‌هایی که نوع آرایه دارند، باید از نحو تحت‌اللفظی آرایه (array literal) یا `arrayOf(...)` استفاده کنید:

``` java
// Java
public @interface AnnWithArrayMethod {
    String[] names();
}
```

```kotlin
@AnnWithArrayMethod(names = ["abc", "foo", "bar"])
class C
```

### دسترسی به ویژگی‌های یک نمونه آنوتیشن

مقادیر یک نمونه آنوتیشن به عنوان ویژگی (property) در کد کاتلین در دسترس هستند:

``` java
// Java
public @interface Ann {
    int value();
}
```

```kotlin
// Kotlin
fun foo(ann: Ann) {
    val i = ann.value
}
```

### قابلیت عدم تولید اهداف آنوتیشن JVM 1.8+

اگر یک آنوتیشن کاتلین دارای `TYPE` در میان اهداف کاتلین خود باشد، این آنوتیشن به `java.lang.annotation.ElementType.TYPE_USE` در لیست اهداف آنوتیشن جاوا نگاشت می‌شود. این دقیقاً مانند نحوه نگاشت هدف کاتلین `TYPE_PARAMETER` به هدف جاوای `java.lang.annotation.ElementType.TYPE_PARAMETER` است. این موضوع برای کلاینت‌های اندرویدی با سطح API کمتر از ۲۶ که این اهداف را در API خود ندارند، یک مشکل است.

برای جلوگیری از تولید اهداف آنوتیشن `TYPE_USE` و `TYPE_PARAMETER` از آرگومان جدید کامپایلر `-Xno-new-java-annotation-targets` استفاده کنید.

## آنوتیشن‌های تکرارپذیر (Repeatable annotations)

درست مانند [در جاوا](https://docs.oracle.com/javase/tutorial/java/annotations/repeating.html)، کاتلین دارای آنوتیشن‌های تکرارپذیر است که می‌توانند چندین بار به یک عنصر کد واحد اعمال شوند. برای تکرارپذیر کردن آنوتیشن خود، اعلان آن را با متا-آنوتیشن [`@kotlin.annotation.Repeatable`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.annotation/-repeatable/) علامت‌گذاری کنید. این کار باعث می‌شود که هم در کاتلین و هم در جاوا تکرارپذیر باشد. آنوتیشن‌های تکرارپذیر جاوا نیز از سمت کاتلین پشتیبانی می‌شوند.

تفاوت اصلی با طرح استفاده شده در جاوا، نبودِ یک «آنوتیشنِ حاوی» (containing annotation) است که کامپایلر کاتلین آن را به‌طور خودکار با یک نام از پیش تعریف شده تولید می‌کند. برای آنوتیشن در مثال زیر، آنوتیشن حاویِ `@Tag.Container` را تولید خواهد کرد:

```kotlin
@Repeatable
annotation class Tag(val name: String)

// کامپایلر آنوتیشن حاوی @Tag.Container را تولید می‌کند
```

می‌توانید با اعمال متا-آنوتیشن [`@kotlin.jvm.JvmRepeatable`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.jvm/-jvm-repeatable/) و ارسال یک کلاس آنوتیشن حاوی که صریحاً اعلان شده به عنوان آرگومان، یک نام سفارشی برای آنوتیشن حاوی تنظیم کنید:

```kotlin
@JvmRepeatable(Tags::class)
annotation class Tag(val name: String)

annotation class Tags(val value: Array<Tag>)
```

برای استخراج آنوتیشن‌های تکرارپذیر کاتلین یا جاوا از طریق reflection، از تابع [`KAnnotatedElement.findAnnotations()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.reflect.full/find-annotations.html) استفاده کنید.

درباره آنوتیشن‌های تکرارپذیر کاتلین در [این KEEP](https://github.com/Kotlin/KEEP/blob/master/proposals/repeatable-annotations.md) بیشتر بیاموزید.





---
# محتوای شخصی:


### 📌  ویژگی‌های اضافی آنوتیشن

|annotation|معنی خیلی خلاصه|
|---|---|
|`@Target`|کجا می‌توان این annotation را استفاده کرد|
|`@Retention`|تا چه مرحله‌ای باقی بماند|
|`@Repeatable`|می‌شود چند بار استفاده شود یا نه|
|`@MustBeDocumented`|در مستندات API نمایش داده شود یا نه|

### 📌 جدول use-site targetهای annotation در Kotlin

|use-site target|در Java روی چی اعمال می‌شود|توضیح ساده|کاربردهای رایج|
|---|---|---|---|
|`file`|خودِ فایل (کلاس تولیدشده)|annotation روی کل فایل Kotlin|`@JvmName`، تنظیمات فایل|
|`field`|فیلد کلاس|annotation روی متغیر private|JPA، Validation، Serialization|
|`property`|❌ فقط Kotlin (در Java دیده نمی‌شود)|annotation روی property منطقی|ابزارهای Kotlin|
|`get`|متد getter|annotation روی `getX()`|Jackson، Bean Validation|
|`set`|متد setter|annotation روی `setX()`|Validation، Frameworkها|
|`param`|پارامتر سازنده|annotation روی constructor parameter|DI (Hilt/Dagger)، Validation|
|`setparam`|پارامتر setter|annotation روی پارامتر setter|Validation|
|`receiver`|پارامتر receiver متد|annotation روی receiver تابع extension|DSLها، APIهای خاص|
|`delegate`|فیلد delegate|annotation روی شیء delegate|delegated propertyها|
|`all` _(experimental)_|param + field + get + setparam|اعمال annotation روی همه‌ی بخش‌ها|ساده‌سازی Validation|

### 🧠 یک راهنمای خیلی سریع

- ❓ فریم‌ورک Java annotation را نمی‌بیند؟  
    ➜ احتمالاً باید از `@field:` یا `@get:` استفاده کنی
- ❓ Dependency Injection کار نمی‌کند؟  
    ➜ معمولاً `@param:` لازم است
- ❓ فقط خود Kotlin مهم است؟  
    ➜ `@property:` کافی است
- ❓ می‌خواهی همه‌جا اعمال شود؟  
    ➜ `@all:` (اگر فعالش کرده باشی)



