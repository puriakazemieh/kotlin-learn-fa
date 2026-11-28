---
cssclasses:
  - persian-rtl
---

# کلاس‌ها (Classes)

کاتلین با پشتیبانی از کلاس‌ها و اشیاء (objects)، از برنامه‌نویسی شیءگرا پشتیبانی می‌کند. اشیاء برای ذخیره‌سازی داده‌ها در برنامهٔ شما سودمند هستند. کلاس‌ها به شما امکان می‌دهند مجموعه‌ای از ویژگی‌ها و مشخصات را برای یک شیء اعلان کنید. هنگامی که اشیایی را از روی یک کلاس می‌سازید، در زمان و تلاش خود صرفه‌جویی می‌کنید زیرا نیازی نیست هر بار این ویژگی‌ها را از نو اعلان کنید.

برای اعلان یک کلاس، از کلمهٔ کلیدی `class` استفاده کنید:

```kotlin
class Customer
```

## ویژگی‌ها (Properties)

مشخصات شیء یک کلاس را می‌توان در قالب ویژگی‌ها (properties) اعلان کرد. شما می‌توانید ویژگی‌های یک کلاس را به دو شیوه اعلان کنید:

* درون پرانتزهای `()` بعد از نام کلاس:
```kotlin
class Contact(val id: Int, var email: String)
```

* درون بدنهٔ کلاس که با آکولادهای `{}` مشخص می‌شود:
```kotlin
class Contact(val id: Int, var email: String) {
    val category: String = ""
}
```

پیشنهاد می‌کنیم ویژگی‌ها را به‌صورت فقط‌خواندنی (`val`) اعلان کنید، مگر اینکه واقعاً نیاز باشد پس از ساخت نمونه‌ای از کلاس، مقدار آن‌ها تغییر کند.

می‌توانید ویژگی‌ها را درون پرانتز بدون `val` یا `var` اعلان کنید، اما این متغیرها پس از ساخته شدن نمونه دیگر به عنوان ویژگی در دسترس نخواهند بود (صرفاً پارامتر سازنده هستند).

> [!note]
> * محتوایی که درون پرانتزهای `()` قرار می‌گیرد، **سرآیند کلاس (class header)** نامیده می‌شود.
> * هنگام اعلان ویژگی‌های کلاس، می‌توانید از [کاما در انتهای خط](../coding-conventions-fa.md#trailing-commas) (trailing comma) استفاده کنید.

دقیقاً همانند پارامترهای توابع، ویژگی‌های کلاس نیز می‌توانند مقادیر پیش‌فرض داشته باشند:

```kotlin
class Contact(val id: Int, var email: String = "example@gmail.com") {
    val category: String = "work"
}
```

## ساخت نمونه (Create instance)

برای ساخت یک شیء از روی یک کلاس، با استفاده از یک **سازنده (constructor)** یک **نمونه (instance)** از آن کلاس اعلان می‌کنید.

به‌طور پیش‌فرض، کاتلین به صورت خودکار یک سازنده با پارامترهایی که در سرآیند کلاس اعلان شده‌اند ایجاد می‌کند.

برای نمونه:

```kotlin
class Contact(val id: Int, var email: String)

fun main() {
    val contact = Contact(1, "mary@gmail.com")
}
```

در این مثال:

* `Contact` یک کلاس است.
* `contact` نمونه‌ای از کلاس `Contact` است.
* `id` و `email` ویژگی‌های کلاس هستند.
* `id` و `email` به همراه سازندهٔ پیش‌فرض برای ساخت شیء `contact` استفاده شده‌اند.

کلاس‌های کاتلین می‌توانند چندین سازنده داشته باشند، از جمله سازنده‌هایی که خودتان تعریف می‌کنید. برای آشنایی بیشتر با نحوهٔ اعلان چندین سازنده، [سازنده‌ها](../classes.md#constructors-and-initializer-blocks) را ببینید.

## دسترسی به ویژگی‌ها (Access properties)

برای دسترسی به ویژگی یک نمونه، نام ویژگی را بعد از نام نمونه و با یک نقطه `.` بنویسید:

```kotlin
class Contact(val id: Int, var email: String)

fun main() {
    val contact = Contact(1, "mary@gmail.com")
    
    // چاپ مقدار ویژگی: email
    println(contact.email)           
    // mary@gmail.com

    // به‌روزرسانی مقدار ویژگی: email
    contact.email = "jane@gmail.com"
    
    // چاپ مقدار جدید ویژگی: email
    println(contact.email)           
    // jane@gmail.com
}
```

> [!tip]
> برای قرار دادن مقدار یک ویژگی در یک رشته، می‌توانید از الگوهای رشته‌ای (`$`) استفاده کنید.
> برای نمونه:
> ```kotlin
> println("Their email address is: ${contact.email}")
> ```

## توابع عضو (Member functions)

علاوه بر اعلان ویژگی‌ها به عنوان بخشی از مشخصات شیء، می‌توانید رفتار یک شیء را با **توابع عضو (member functions)** تعریف کنید.

در کاتلین، توابع عضو باید درون بدنهٔ کلاس اعلان شوند. برای فراخوانی یک تابع عضو روی یک نمونه، نام تابع را بعد از نام نمونه و با یک نقطه `.` بنویسید. برای نمونه:

```kotlin
class Contact(val id: Int, var email: String) {
    fun printId() {
        println(id)
    }
}

fun main() {
    val contact = Contact(1, "mary@gmail.com")
    // فراخوانی تابع عضو printId()
    contact.printId()           
    // 1
}
```

## کلاس‌های داده (Data classes)

کاتلین دارای **کلاس‌های داده (data classes)** است که به ویژه برای ذخیره‌سازی داده‌ها سودمند هستند. کلاس‌های داده عملکردی مشابه کلاس‌های معمولی دارند، اما به طور خودکار به همراه توابع عضو اضافی ارائه می‌شوند. این توابع عضو به شما امکان می‌دهند به سادگی نمونه را در قالبی خوانا چاپ کنید، نمونه‌های یک کلاس را با هم مقایسه نمایید، از نمونه‌ها کپی بگیرید و کارهای دیگر انجام دهید. از آنجا که این توابع به طور خودکار در دسترس هستند، نیازی نیست برای هر یک از کلاس‌های خود وقت صرف نوشتن کدهای تکراری (boilerplate) کنید.

برای اعلان یک کلاس داده، از کلمهٔ کلیدی `data` استفاده کنید:

```kotlin
data class User(val name: String, val id: Int)
```

کامپایلر کاتلین هنگام تولید توابع عضو، تنها از ویژگی‌هایی استفاده می‌کند که درون [سازندهٔ اصلی (primary constructor)](../classes.md#primary-constructor) تعریف شده‌اند. اگر ویژگی‌هایی را درون بدنهٔ کلاس داده اعلان کنید، آن‌ها در خروجی توابع تولیدشده لحاظ نخواهند شد.

کاربردی‌ترین توابع عضو از پیش تعریف‌شده برای کلاس‌های داده عبارتند از:

| **تابع** | **توضیحات** |
|---|---|
| `toString()` | رشته‌ای خوانا از نمونهٔ کلاس و ویژگی‌های آن چاپ می‌کند. |
| `equals()` یا `==` | نمونه‌های یک کلاس را با یکدیگر مقایسه می‌کند. |
| `copy()` | با کپی کردن یک نمونه، نمونه‌ای جدید از کلاس می‌سازد که می‌تواند برخی ویژگی‌های متفاوت داشته باشد. |

در بخش‌های زیر مثال‌هایی از نحوهٔ استفاده از هر تابع آورده شده است:

* [چاپ به صورت رشته](#چاپ-به-صورت-رشته-print-as-string)
* [مقایسهٔ نمونه‌ها](#مقایسه-نمونهها-compare-instances)
* [کپی کردن نمونه](#کپی-کردن-نمونه-copy-instance)

### چاپ به صورت رشته (Print as string)

برای چاپ رشته‌ای خوانا از نمونهٔ یک کلاس، می‌توانید صریحاً تابع `toString()` را صدا بزنید، یا از توابع چاپ (`println()` و `print()`) استفاده کنید که به طور خودکار `toString()` را برای شما فراخوانی می‌کنند:

```kotlin
data class User(val name: String, val id: Int)

fun main() {
    //sampleStart
    val user = User("Alex", 1)
    
    // به طور خودکار از تابع toString() استفاده می‌کند تا خروجی خوانا باشد
    println(user)            
    // User(name=Alex, id=1)
    //sampleEnd
}
```

این قابلیت به ویژه هنگام اشکال‌زدایی (debugging) یا ایجاد لاگ‌ها بسیار سودمند است.

### مقایسهٔ نمونه‌ها (Compare instances)

برای مقایسهٔ نمونه‌های کلاس داده، از عملگر برابری `==` استفاده کنید:

```kotlin
data class User(val name: String, val id: Int)

fun main() {
    //sampleStart
    val user = User("Alex", 1)
    val secondUser = User("Alex", 1)
    val thirdUser = User("Max", 2)

    // مقایسه user با کاربر دوم
    println("user == secondUser: ${user == secondUser}") 
    // user == secondUser: true
    
    // مقایسه user با کاربر سوم
    println("user == thirdUser: ${user == thirdUser}")   
    // user == thirdUser: false
    //sampleEnd
}
```

### کپی کردن نمونه (Copy instance)

برای ساخت یک کپی دقیق از نمونهٔ یک کلاس داده، تابع `copy()` را روی آن نمونه فراخوانی کنید.

برای ساخت کپی از نمونهٔ یک کلاس داده **و** تغییر دادن برخی ویژگی‌های آن، تابع `copy()` را روی نمونه فراخوانی کرده **و** مقادیر جایگزین را به عنوان پارامتر تابع ارسال کنید.

برای نمونه:

```kotlin
data class User(val name: String, val id: Int)

fun main() {
    //sampleStart
    val user = User("Alex", 1)

    // ساخت کپی دقیق از user
    println(user.copy())       
    // User(name=Alex, id=1)

    // ساخت کپی از user با نام جدید "Max"
    println(user.copy("Max"))  
    // User(name=Max, id=1)

    // ساخت کپی از user با شناسه جدید 3
    println(user.copy(id = 3)) 
    // User(name=Alex, id=3)
    //sampleEnd
}
```

ساختن کپی از یک نمونه امن‌تر از تغییر مستقیم نمونهٔ اصلی است، زیرا کدهایی که به نمونهٔ اصلی وابسته هستند، تحت تأثیر شیء کپی‌شده و تغییرات اعمال‌شده بر آن قرار نمی‌گیرند.

برای اطلاعات بیشتر دربارهٔ کلاس‌های داده، [کلاس‌های داده](../data-classes.md) را ببینید.

فصل پایانی این تور مقدماتی دربارهٔ [ایمنی در برابر null](kotlin-tour-null-safety.md) در کاتلین است.

## تمرین

### اعلان یک کلاس داده

یک کلاس داده به نام `Employee` با دو ویژگی تعریف کنید: یکی برای نام (`name`) و دیگری برای حقوق (`salary`). دقت کنید که ویژگی حقوق باید تغییرپذیر (`var`) باشد، در غیر این صورت در پایان سال افزایش حقوق دریافت نخواهید کرد! تابع `main` نحوهٔ استفاده از این کلاس داده را نشان می‌دهد.

```kotlin
// Write your code here

fun main() {
    val emp = Employee("Mary", 20)
    println(emp)
    emp.salary += 10
    println(emp)
}
```

> [!example]- راه‌حل نمونه
> ```kotlin
> data class Employee(val name: String, var salary: Int)
> 
> fun main() {
>     val emp = Employee("Mary", 20)
>     println(emp)
>     emp.salary += 10
>     println(emp)
> }
> ```

### اعلان کلاس‌های دادهٔ تو در تو

کلاس‌های دادهٔ اضافی مورد نیاز برای کامپایل شدن کد زیر را اعلان کنید.

```kotlin
data class Person(val name: Name, val address: Address, val ownsAPet: Boolean = true)
// Write your code here
// data class Name(...)

fun main() {
    val person = Person(
        Name("John", "Smith"),
        Address("123 Fake Street", City("Springfield", "US")),
        ownsAPet = false
    )
}
```

> [!example]- راه‌حل نمونه
> ```kotlin
> data class Person(val name: Name, val address: Address, val ownsAPet: Boolean = true)
> data class Name(val first: String, val last: String)
> data class Address(val street: String, val city: City)
> data class City(val name: String, val countryCode: String)
> 
> fun main() {
>     val person = Person(
>         Name("John", "Smith"),
>         Address("123 Fake Street", City("Springfield", "US")),
>         ownsAPet = false
>     )
> }
> ```

### تولید کارمندان تصادفی با کلاس

برای آزمودن کد خود، به یک تولیدکننده نیاز دارید که بتواند کارمندان تصادفی ایجاد کند. کلاسی به نام `RandomEmployeeGenerator` با فهرستی ثابت از نام‌های احتمالی (درون بدنهٔ کلاس) تعریف کنید. کلاس را با حداقل و حداکثر حقوق (درون سرآیند کلاس) پیکربندی کنید. در بدنهٔ کلاس، تابع `generateEmployee()` را تعریف کنید. مجدداً تابع `main` نحوهٔ استفاده از این کلاس را نشان می‌دهد.

> [!tip]
> در این تمرین، بسته‌ای را وارد (import) می‌کنید تا بتوانید از تابع [`Random.nextInt()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.random/-random/next-int.html) استفاده کنید. برای اطلاعات بیشتر دربارهٔ وارد کردن بسته‌ها، [پکیج‌ها و ایمپورت‌ها](../packages-fa.md) را ببینید.

> [!tip]- راهنمایی ۱
> لیست‌ها دارای یک تابع افزونه (extension) به نام [`.random()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/random.html) هستند که یک آیتم تصادفی از درون لیست برمی‌گرداند.

> [!tip]- راهنمایی ۲
> عبارت `Random.nextInt(from = ..., until = ...)` یک عدد صحیح (`Int`) تصادفی درون بازهٔ تعیین‌شده تولید می‌کند.

```kotlin
import kotlin.random.Random

data class Employee(val name: String, var salary: Int)

// Write your code here

fun main() {
    val empGen = RandomEmployeeGenerator(10, 30)
    println(empGen.generateEmployee())
    println(empGen.generateEmployee())
    println(empGen.generateEmployee())
    empGen.minSalary = 50
    empGen.maxSalary = 100
    println(empGen.generateEmployee())
}
```

> [!example]- راه‌حل نمونه
> ```kotlin
> import kotlin.random.Random
> 
> data class Employee(val name: String, var salary: Int)
> 
> class RandomEmployeeGenerator(var minSalary: Int, var maxSalary: Int) {
>     val names = listOf("John", "Mary", "Ann", "Paul", "Jack", "Elizabeth")
>     fun generateEmployee() =
>         Employee(names.random(),
>             Random.nextInt(from = minSalary, until = maxSalary))
> }
> 
> fun main() {
>     val empGen = RandomEmployeeGenerator(10, 30)
>     println(empGen.generateEmployee())
>     println(empGen.generateEmployee())
>     println(empGen.generateEmployee())
>     empGen.minSalary = 50
>     empGen.maxSalary = 100
>     println(empGen.generateEmployee())
> }
> ```

[گام پیشین](kotlin-tour-functions-fa.md) · [گام بعدی](kotlin-tour-null-safety.md)

---

## تمرین و مرور

این بخش برای تثبیت و مرور مفاهیم کلاس‌ها و شیءگرایی در کاتلین اضافه شده است.

### پنج پرسش بازیابی فعال

1. تفاوت اعلان یک پارامتر با `val`/`var` در سرآیند کلاس در مقایسه با اعلان آن بدون `val`/`var` چیست؟
   > [!check]- پاسخ
   > اگر پارامتری در سرآیند کلاس با `val` یا `var` اعلان شود، به یک ویژگی (property) عمومی آن کلاس تبدیل می‌شود و پس از ساخت نمونه در دسترس خواهد بود. اما اگر بدون `val` یا `var` اعلان شود، صرفاً یک پارامتر ورودی سازنده است و از بیرون نمونه به عنوان یک ویژگی قابل دسترسی نخواهد بود.

2. کلاس‌های داده (Data Classes) در کاتلین چه تفاوت مهمی با کلاس‌های معمولی دارند و کامپایلر چه توابعی را برای آن‌ها به طور خودکار تولید می‌کند؟
   > [!check]- پاسخ
   > کلاس‌های داده با کلمهٔ کلیدی `data` تعریف می‌شوند و برای ذخیره‌سازی داده طراحی شده‌اند. کامپایلر کاتلین به صورت خودکار توابع مفیدی مانند `toString()` (برای نمایش خوانا)، `equals()` و عملگر `==` (برای مقایسه بر اساس مقادیر)، `hashCode()` و `copy()` (برای کپی نمونه با امکان تغییر ویژگی‌ها) را بر اساس ویژگی‌های سازندهٔ اصلی برای آن‌ها تولید می‌کند.

3. چرا کامپایلر کاتلین ویژگی‌هایی را که درون بدنهٔ کلاس داده `{}` تعریف می‌شوند در توابع تولیدشده (`toString`، `equals` و `copy`) دخالت نمی‌دهد؟
   > [!check]- پاسخ
   > زیرا کامپایلر کاتلین تنها ویژگی‌هایی را که در سازندهٔ اصلی (Primary Constructor) در سرآیند کلاس اعلان شده‌اند به عنوان شناسه و هویت اصلی داده در نظر می‌گیرد. ویژگی‌های داخل بدنه به عنوان فیلدهای کمکی در نظر گرفته شده و در متدهای خودکار `equals` یا `copy` لحاظ نمی‌شوند.

4. متد `copy()` در کلاس‌های داده چگونه کار می‌کند و چرا استفاده از آن نسبت به تغییر مستقیم متغیرها امن‌تر است؟
   > [!check]- پاسخ
   > متد `copy()` یک نمونهٔ جدید از شیء با مقادیر یکسان می‌سازد و این امکان را می‌دهد که با ارسال آرگومان‌های نام‌دار، مقادیر برخی از ویژگی‌ها را در نمونهٔ جدید تغییر دهید. این روش بسیار امن‌تر از تغییر مستقیم متغیرهاست زیرا اصل تغییرناپذیری (Immutability) را حفظ می‌کند و سایر بخش‌های برنامه که به نمونهٔ اصلی وابسته هستند، با تغییرات ناخواسته روبه‌رو نمی‌شوند.

5. نحوهٔ تعریف توابع عضو (Member Functions) در کلاس‌های کاتلین و دسترسی به ویژگی‌های کلاس درون آن توابع چگونه است؟
   > [!check]- پاسخ
   > توابع عضو مستقیماً درون بدنهٔ کلاس (بین آکولادهای `{}`) تعریف می‌شوند و می‌توانند مستقیماً و بدون نیاز به پیشوند به ویژگی‌های اعلان‌شده در سرآیند یا بدنهٔ کلاس دسترسی داشته باشند. برای فراخوانی آن‌ها روی یک نمونه نیز از عملگر نقطه `.` استفاده می‌شود (مانند `contact.printId()`).

### سه تمرین تکمیلی

1. **تمرین تعریف کلاس دادهٔ محصول:** یک کلاس داده به نام `Product` با ویژگی‌های `id` (فقط‌خواندنی `val` از نوع `Int`)، `name` (از نوع `String`) و `price` (از نوع `Double`) بسازید. یک نمونه از آن ایجاد کرده، سپس با استفاده از تابع `copy()` محصولی جدید با همان مشخصات اما با ۲۰ درصد تخفیف در قیمت ایجاد کنید و هر دو را چاپ نمایید.
   > [!tip]- راهنمایی
   > برای کپی با قیمت تخفیف‌خورده، از آرگومان نام‌دار `copy(price = original.price * 0.8)` استفاده کنید.
   > [!example]- راه‌حل نمونه
   > ```kotlin
   > data class Product(val id: Int, val name: String, val price: Double)
   > 
   > fun main() {
   >     val original = Product(101, "Laptop", 1000.0)
   >     val discounted = original.copy(price = original.price * 0.8)
   >     println("محصول اصلی: $original")
   >     println("محصول با تخفیف: $discounted")
   > }
   > ```

2. **تمرین کلاس مستطیل با توابع عضو:** کلاسی معمولی به نام `Rectangle` بسازید که دو ویژگی `width` و `height` از نوع `Double` در سرآیند داشته باشد. درون بدنهٔ کلاس دو تابع عضو به نام‌های `area()` (برای محاسبه مساحت) و `perimeter()` (برای محاسبه محیط) تعریف کنید. در تابع `main` نمونه‌ای با ابعاد ۵ و ۳ ساخته و مساحت و محیط را چاپ کنید.
   > [!tip]- راهنمایی
   > می‌توانید توابع `area()` و `perimeter()` را به صورت توابع تک‌عبارتی (`=`) درون بدنهٔ کلاس بنویسید.
   > [!example]- راه‌حل نمونه
   > ```kotlin
   > class Rectangle(val width: Double, val height: Double) {
   >     fun area(): Double = width * height
   >     fun perimeter(): Double = 2 * (width + height)
   > }
   > 
   > fun main() {
   >     val rect = Rectangle(5.0, 3.0)
   >     println("مساحت: ${rect.area()}") // 15.0
   >     println("محیط: ${rect.perimeter()}") // 16.0
   > }
   > ```

3. **تمرین مدیریت حساب بانکی با اعتبارسنجی:** کلاسی به نام `BankAccount` با ویژگی `accountNumber: String` و ویژگی متغیر `var balance: Double = 0.0` بنویسید. دو متد `deposit(amount: Double)` و `withdraw(amount: Double): Boolean` اضافه کنید؛ متد برداشت تنها در صورتی وجه را کم کند و `true` برگرداند که موجودی کافی باشد، در غیر این صورت `false` بازگرداند.
   > [!tip]- راهنمایی
   > در متد `withdraw` با یک شرط `if (balance >= amount)` بررسی لازم را انجام دهید.
   > [!example]- راه‌حل نمونه
   > ```kotlin
   > class BankAccount(val accountNumber: String, var balance: Double = 0.0) {
   >     fun deposit(amount: Double) {
   >         balance += amount
   >     }
   >     
   >     fun withdraw(amount: Double): Boolean {
   >         return if (balance >= amount) {
   >             balance -= amount
   >             true
   >         } else {
   >             false
   >         }
   >     }
   > }
   > 
   > fun main() {
   >     val account = BankAccount("IR1234", 100.0)
   >     account.deposit(50.0)
   >     println("موجودی پس از واریز: ${account.balance}") // 150.0
   >     val success = account.withdraw(200.0)
   >     println("برداشت موفق بود؟ $success (موجودی: ${account.balance})") // false
   > }
   > ```

### دو خطای رایج

1. **مقایسهٔ دو نمونه از کلاس معمولی به جای کلاس داده:** اگر کلمهٔ کلیدی `data` را قبل از `class` نگذارید، کاتلین متد `equals()` را بر اساس برابری ارجاعی (آدرس حافظه) بررسی می‌کند نه بر اساس مقادیر؛ بنابراین `User("Ali", 1) == User("Ali", 1)` برای کلاس‌های معمولی مقدار `false` می‌دهد، اما در کلاس‌های داده مقدار `true` بازمی‌گرداند.
2. **تعریف ویژگی‌های حیاتی درون بدنهٔ کلاس داده به جای سازندهٔ اصلی:** اگر ویژگی مهمی درون بدنهٔ کلاس داده قرار گیرد، در متدهای `copy()` و `equals()` و `toString()` نادیده گرفته می‌شود که می‌تواند باعث باگ‌های نامحسوس در مقایسه یا شبیه‌سازی اشیاء شود.
