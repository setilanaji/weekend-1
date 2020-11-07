# Rangkuman Week 1

## Git
### Introduction
Git adalah **open-source version control system(VCS)** yang tersedia secara **gratis**. Seperti hal nya VCS pada umumnya, git dapat membantu team pengembangan sofware untuk **mengelola setiap perubahan source code** dalam project.

Git akan melakukan pengecekan isi dalam setiap file dalam project. Dan ketika pengguna setuju untuk menyimpan perubahan(**git commit**)  tersebut akan tersimpan ke history dalam file **.git**. 

terdapat tiga status file:
- **commited**: data sudah tersimpan
- **staged**: file telah mengalami perubahan
- **modified**: perubahan dalam file belum ditandai

Operasi Git sebaian besar dapat bekerja secara local. Untuk melakukannya umumnya melalui **Command Line** karena lebih simpel, mudah dan tidak perlu melakukan instalasi third party tool.

### Basic
Berikut beberapa command dan contoh penggunaannya:
- **git init** : menginiliasasi repositori git baru
- **git clone** : digunakan untk meng copy repositori
- **git add** : menambah file ke status staged
- **git commit** : untuk menyimpan data perubahan ke direktori git
- **git status** : menampilkan daftar file yang berubah lengkap dengan status nya.
- **git push** : mengirim data commit ke remote repository
- **git checkout** : untuk berpindah ke branch lain
- **git remote** : untuk mengkoneksikan antara reppositori lokal dan server secara remote
- **git branch** : bisa berfungsi untuk menampilkan, menambah, atau menghapus daftar branch
- **git pull** : menggabungkan semua perubahan terakhir di remote repository ke local repository
  
## SDLC
### Introduction
SDLC atau **Software Development Life Cycle** merupakan proses yang digunakan pada industri pengembangan software untuk menghasilkan aplikasi berkualitas tinggi sesuai tujuan dan ekspetasi dari customer. Biasanya berisi rencana yang secara detil bagaimana untuk membuat, merawat, menggantikan dan memperbarui aplikasi tersebut. Contohnya adalah: Waterfall dan Agile

SDLC berisi beberapa tahapan sebagai berikut:
1. Planning
2. Defining
3. Designing
4. Building
5. Testing
6. Deployment
7. Maintenance


## Figma

[Figma](https://www.figma.com/) adalah free vector graphic editor sekaligus prototyping tool berbasis web.

## Kotlin Basic
### Basic Syntax
* **Package** harus ditulis di paling atas dalam file
* **Variable** terdapat dua jenis variable: `val` dan `var`. val memilik sifat read only atau tidak dapat diubah. Sedangakan var dapat diubah. 
* **comment** seperti bahasa modern pada umumnya. Kotlin memggunakan seingle-line(sampai akhir line) dan multi-line(bisa block) comment.

### Idiom
* **Data class** kotlin memiliki keyword data untuk membuat sebuah class yang khusus menyimpan data.
* **Built-in method** Kotlin memiliki berbagai built-in method yang memudahkan programmer dalam meng-coding, seperti: `.toList()`, `.filter{}`, `.map{}`
* **Mutable dan Immutable** Untuk setiap jenis collection pada kotlin, memiliki dua sifat yaitu: mutable(dapat berubah) dan imutable(tidak dapat diubah/fixed). Dimana dalam penginiliasian nya tinggal ditambah mutable didepan tipe collection tersebut. sebagai contoh: `MutableList` yang berarti List tersebut dapat berubah size nya dan isinya.
Bila bersifat tak dapat diubah berarti ditulis `List` saja.
    ```Kotlin
    val list: MutableList<String> = mutableListOf<String>()
    val listTwo: List<String> = listOf<String>()
* **Lazy property** keyword `lazy` digunakan untuk me-load value pada variable satu kali saja saat di panggil, dan hasilnya akan disimpan ke cache.
  ```Kotlin
    val lazyValue: String by lazy {
        println("computed!")
        "Hello"
    }
* **Extension Function** berguna untuk menambahkan function baru ke class yang sudah ada diluar class tersebut.
    ```Kotlin
    // Mengubah b
    fun String.toProperCase() : String {
        return this.split(" ").map { it.capitalize() }.joinToString(" ")
    }

* **Singleton** Untuk membuat singleton dalam kotlin, cukup menggunakan keyword `object`
    ```Kotlin
    object Util {
        init { println("Singleton instance...") }

        private const val DATA = "Anonymouse"

        fun printName() = println(DATA)
    }

### Code Convention
* **Directory Structure** direkomendasikan untuk semua code dalam project disimpan dalam package `domain.company.appname` 
* **Source file name** untuk nama setiap file disimpan menggunakan aturan `PascalCase`
* **Nama untuk class dan object** menggunakan aturan `PascalCase`
* **Nama untuk function dan variable** menggunakan aturan `CamelCase`
* **Nama untuk variable constant** menggunakan `MACRO_CASE`
> Nama `class` biasanya berupa kata benda. sedangkan nama `function` atau method menggunakan kata kerja.

### Basic Types
* **Numbers** 
    - `Byte` yang menampung nilai dari -128 sampai 127.
        ```Kotlin
        val byte: Byte = 1
    - `Short` yang menampung nilai dari -32,768 sampai 32,767.
        ```Kotlin
        val short: Short = 10
    - `Int` yang menampung nilai dari -2,147,483,648 sampai 2,147,483,647.
        ```Kotlin
        val int = 10
    - `Long` yang menampung nilai dari -9,223,372,036,854,775,808 sampai 9,223,372,036,854,775,807.
        ```Kotlin
        val long = 1000L 
    - `Float` yang menampung nilai dari -2,147,483,648.0 sampai 2,147,483,647.0.
        ```Kotlin
        val float = 1000.0F
    - `Double` yang menampung nilai dari -9,223,372,036,854,775,808.0 sampai 9,223,372,036,854,775,807.0.
        ```Kotlin
        val double = 1000.0
* 

### Control FLow
* **When expression** Dalam kotlin `when` merupakan pengganti `switch case statement` yang lebih simpel daripada bahasa lain.
    ```Kotlin
    val x = (0..25).random()
    when (x) {
        1 -> print("x == 1")
        else -> { print("x isn’t 1") }
    }
## Kotlin Class & Objects
### Classes and Inheritance
* **Constructor** dalam Kotlin, class dapat memiliki satu primary constructor dan satu atau lebih contructor tambahan
    ```Kotlin
    class Person(val name: String) {
        val children = mutableListOf<Person>()
        constructor(name: String, parent: Person) : this(name) {
        parent.children.add(this)
        }
    }
    val parent = Person("Abi")
    val child = Person("Fulan", parent)
* **Inheritance** untuk melakukan inheritance dalam `class` kotlin perlu ditambahkan keyword `open`
    ```Kotlin
    open class Person(val name: String) {
        var age = 0
    }
    
    class Adult(name: String) : Person(name) {
        init {
            age = 18
        }
    }
### Properties dan File
* **Getter dan Setter** berfungsi untuk melakukan enkapsulasi. Setter hanya bisa dilakukan pada mutable variable atau `var`, sedangkan getter dapat dilakukan ke semua jenis. 
    ```Kotlin
    class Student {
        var name: String = ""
        get() {
            println("Getting name")
            return field
        }
        set(value) {
            println("Changing name")
            field = value
        }
* **Backing field** dibuat untuk menghindari recursive call dan mengakibatkan StackOverflow exception karena memanggil setter dalam setter.
    ```Kotlin
    class User{
        var firstName : String  
            get() = field
            set(value) {field = value}
    
        var lastName : String  
            get() = field
            set(value) {field = value}
    }
* **Backing properties** berfungsi untuk mengakses field properti dalam scope getter dan setter
    ```Kotlin
    class Human {
        private val _age: Int = 20
        val age: Int
            get() {
                return _age
            }

        val printAge = {
            println("Age is: $_age")
        }
    }
* **Late initialized properti dan variable** penggunaan keyword `lateinit` bertujuan bila tidak ingin meng inisialisasi properti saat deklarasi tapi juga dalam waktu yang sama tidak ingin menggunakan null check pada properti tersebut setiap kali kita menggunakan properti tersebut.
    ```Kotlin
    lateinit var variable : CustomClass
## Function & Lambda
`Function` dalam Kotlin di deklarasikan menggunakan keyword `fun` :
```Kotlin
fun double(x: Int): Int {
    return 2 * x
}
``` 
Parameter dalam `function` di tulis menggunakan notasi Pascal seperti: `name: Type` . Parameter dipisah menggunakan koma:
```Kotlin
fun powerOf(number: Int, exponent: Int) { /*...*/ }
``` 
untuk default argument dan named argument masih terlihat seperti bahasa modern pada umumnya.

Jika function tidak mengembalikan value, maka tipe yang di kembalikan berupa `Unit`. Value ini tidak di kembalikan secara explicit:
```Kotlin
fun printHello(name: String?): Unit {
    if (name != null)
        println("Hello $name")
    else
        println("Hi there!")
    // `return Unit` atau `return` bersifat opsional
}
```
Saat function mengembalikan satu nilai saja maka kurung kurawal bisa di hilangkan dan body di tulis setelah simbol =
```Kotlin
fun double(x: Int): Int = x * 2
```
## Kotlin Collection
### Iterator
### Sequence
### Transformation
### Grouping
### Ordering
### Aggregate operation

## Kotlin Language Construct
### Destruction Declarations
Destructuring declaration menghasilkan multiple variable dalam satu waktu. Sebagai contoh:
```Kotlin
val (name, age) = person

println(name)
println(age)
```
Variable `name` dan `age` dapat digunakan secara independen.

Destructuring declaration juga bisa digunakan dalam `for-loop`. seperti:
```Kotlin
for ((a, b) in collection) { ... }
```
Bila tidak membutuhkan sebuah variable dala proses destructuring maka bisa menggantinya dengan menuliskan underscore:
```Kotlin
val (_, status) = getResult()
```
Bisa juga digunakan untuk parameter lamda. Jika sebuah lamda memiliki parameter dengan tipe `Pair` (atau `Map.Entry`):
```Kotlin
map.mapValues { entry -> "${entry.value}!" }
map.mapValues { (key, value) -> "$value!" }
```
### Type check and Cast
### Null Safety
### Exception
### Annotation

### Scope Function
Scope function pada Kotlin merupakan fungsi-fungsi yang mengijikan untuk mengubah scope atau range dari sebuah variable. Terdapat lima jenis fungsi dalam standard library Kotlin yaitu: `apply`, `run`, `with`, `let`, `also`
```Kotlin
fun myFun() {
    val outside = 6.2831853071
    run {
        val inside = 1.61803398875
        // Both outside and inside are usable and in scope
    }
    // inside is out of scope, and only outside is available
}