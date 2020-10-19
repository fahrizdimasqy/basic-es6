# basic-es6
## Deklarasi var dan Hoisting
Variabel yang dideklarasikan menggunakan var akan selalu diangkat pada tingkatan atas sebuah fungsi walaupun kita menuliskannya bukan pada tingkatan atas fungsi. Proses pengangkatan deklarasi variabel ini disebut dengan hoisting.

```javascript
function makeTea(isCold) {
    if(isCold) {
        var tea = "Make an Ice Tea!"
    } else {            
        var tea = "Make a Hot Tea!"
    }
        return tea;
}
console.log(makeTea(false));

// hasilnya adalah make a hot tea
```

JavaScript mengangkat proses deklarasi variabel tea pada
tingkatan atas fungsi. Sehingga variabel tersebut akan tersedia selama kita berada di dalam
fungsi makeTea.

Bahkan karena proses hoisting inilah kita bisa menginisialisasi nilai dan menggunakan
variabel sebelum ia dideklarasikan. Hal ini sedikit tidak masuk akal bukan?

### let dan const
Variabel yang dideklarasikan dengan let atau const akan menghilangkan permasalahan dari
hoisting karena variabel akan tersedia pada cakupan block (sama seperti bahasa
pemrograman berbasis C), bukan pada fungsi.

Variabel yang dideklarasikan menggunakan let ataupun const juga tidak dapat diakses
sebelum ia dideklarasikan, karena variabel akan terhenti pada tempat yang biasa disebut
dengan temporal dead zone hingga akhirnya variabel tersebut dideklarasi.

### Aturan penggunaan let dan const
Variabel yang dideklarasikan dengan let atau pun const memiliki kesamaan dan perbedaan karakteristik. Persamaannya adalah variabel yang dideklarasikan dengan let atau const tidak dapat di deklarasikan ulang pada cakupan yang sama

Perbedaanya antara let dan const adalah jika kita menggunakan let maka variabel tersebut dapat diinisialisasi ulang nilainya. Sedangkan const tidak bisa, sehingga jika kita menggunakan const pastikan kita langsung menginisialisasi nilai dari variabel tersebut.

• Gunakan let ketika variabel yang kita buat akan diinisialisasikan kembali nilainya.
• Gunakan const ketika variabel yang kita buat tidak ingin diinisialisasikan kembali nilainya.

> Ada sedikit catatan, bahwa mengubah dan menginisialisasikan ulang nilai pada variabel merupakan hal yang berbeda.

### Template Literals
ES6 menawarkan kemudahan bagi developer dalam mengelola nilai string. Sebelum ES6, cara lama dalam menggabungkan nilai string adalah dengan menggunakan operator (+).

? Gunakanlah tanda backticks (`) untuk menggantikan
tanda single quotes (‘) atau double quotes (“) yang digunakan sebelumnya. Template literals juga dapat mengandung sebuah expression dengan menuliskannya di dalam tanda ${expression}. Hal ini sungguh membantu sekali dalam pembuatan nilai string yang kompleks menjadi jauh lebih mudah.

```javascript
const user = {
    firstName: "Dimas",
    lastName: "Saputra",
    age: 18
}
console.log(`Nama: ${user.firstName} ${user.lastName}, Umur: ${user.age}`);
// output
// Nama: Dimas Saputra, Umur: 18
```

### Destructuring Object
Penulisan destructuring object pada ES6 sintaks menggunakan objek literal { } di sisi kiri dari operasi assignment.

```javascript
const profile = {
    firstName: "John",
    lastName: "Doe",
    age: 18
}
const {firstName, lastName, age} = profile;
console.log(firstName, lastName, age);
// output
// John Doe 18
```

### Destructuring Assignment
Pada contoh sebelumnya kita melakukan destructuring object pada deklarasi variabel, namun pada kasus tertentu mungkin kita perlu melakukannya pada variabel yang sudah dideklarasikan. Atau kita ingin mengubah nilainya dengan nilai properti di objek.

```javascript
const profile = {
    firstName: "John",
    lastName: "Doe",
    age: 18
}

let firstName = "Dimas";
let age = 20;

// menginisialisasi nilai baru melalui object destruction
({firstName, age} = profile);
console.log(firstName);
console.log(age);

// output
// john, 18;
```

> Nah inilah fungsinya tanda kurung. Ia akan memberitahu JavaScript bahwa tanda kurawal yang di dalamnya bukan sebuah block statement, melainkan sebuah expression. Sehingga assignment dapat dilakukan.

### Default Values
Ketika kita mendestruksikan objek dan kita menetapkan variabel dengan nama yang bukan merupakan properti dari objek, maka nilai dari variabel tersebut menjadi undefined.

```javascript
Contohnya:
const profile = {
    firstName: "John",
    lastName: "Doe",
    age: 18
}
const {firstName, age, isMale} = profile;
console.log(firstName)
console.log(age)
console.log(isMale)

/* output:
John
18
undefined
*/

```

Alternatifnya, kita bisa secara opsional mendefinisikan nilai default pada properti tertentu jika tidak ditemukan. Untuk melakukanya tambahkan tanda assignment (=) setelah nama variabel dan tentukan nilai defaultnya seperti ini:

```javascript
Contohnya:
const profile = {
    firstName: "John",
    lastName: "Doe",
    age: 18
}
const {firstName, age, isMale=false} = profile;
console.log(firstName)
console.log(age)
console.log(isMale)

/* output:
John
18
false
*/

```

### Assigning to Different Local Variable Names
Namun sebenarnya dalam mendestruksikan objek kita bisa menggunakan penamaan variabel lokal yang berbeda. ES6 menyediakan sintaks tambahan yang membuat kita dapat melakukan hal tersebut. Penulisannya mirip seperti ketika kita membuat properti beserta nilainya pada objek.

Contohnya seperti ini:

```javascript
const profile = {
    firstName: "John",
    lastName: "Doe",
    age: 18
}

const {firstName: localFirstName, lastName: localLastName, age: localAge} = profile;
console.log(localFirstName);
console.log(localLastName);
console.log(localAge);
/* output:
John
18
*/
```

### Destructuring Array
Destructuring Array serupa dengan destructuring object. Jika objek menggunakan tanda kurung kurawal { } sedangkan array menggunakan tanda kurung siku [ ]. Perbedaan lainnya adalah destructuring array bekerja berdasarkan posisi daripada penamaan propertinya. Berikut contoh dari destructuring array pada ES6:

```javascript
const favorites = ["Seafood", "Salad", "Nugget", "Soup"];
const [firstFood, secondFood, thirdFood, fourthFood] = favorites;
console.log(firstFood);
console.log(secondFood);
console.log(thirdFood);
console.log(fourthFood);
/* output:
Seafood
Salad
Nugget
Soup
*/
```

Contoh di atas merupakan proses destructuring array. Di dalam array tersebut (favorites) terdapat 4 (empat) nilai string yang masing-masing nilainya dimasukkan ke variabel lokal firstFood, secondFood, thirdFood, dan fourthFood. Nilai pada array yang dimasukkan ke variabel lokal dipilih berdasarkan posisi di mana ia dideklarasikan pada array notasi.

> Sebenarnya nama dari variabel lokal bisa apa saja. Yang terpenting adalah urutan ketika deklarasi variabelnya saja.

Kita juga bisa memilih nilai pada index tertentu untuk didestruksikan pada array.

```javascript
const favorites = ["Seafood", "Salad", "Nugget", "Soup"];
const [, , thirdFood ] = favorites;
console.log(thirdFood);
/* output:
Nugget
*/
```

### Destructuring Assignment
Kita juga bisa melakukan destructuring assignment pada array. Namun tidak seperti objek,
kita tidak perlu membungkusnya pada tanda kurung

```javascript
const favorites = ["Seafood", "Salad", "Nugget", "Soup"];
let myFood = "Ice Cream";
let herFood = "Noodles";
[myFood, herFood] = favorites;
console.log(myFood);
console.log(herFood);
/* output:
Seafood
Salad
*/
```
Array destructuring assignment sangat berguna ketika kita hendak menukar nilai antar dua
variabel, sebelum ES6 untuk melakukan hal ini kita menggunakan cara manual menggunakan
algoritma sorting seperti ini:

var a = 1;
var b = 2;
var temp;
console.log("Sebelum swap");
console.log("Nilai a: " + a);
console.log("Nilai b: " + b);
temp = a;
a = b;
b = temp;
console.log("Setelah swap");
console.log("Nilai a: " + a);
console.log("Nilai b: " + b);

Untuk melakukan pertukaran nilai, kita membutuhkan variabel penengah. Pada contoh kode
di atas variabel tersebut adalah temp. Variabel penengah dibutuhkan untuk menyimpan data
sementara pada variabel yang akan ditukar. Hal ini menjadi kurang efektif karena kita harus
membuat variabel baru yang sebenarnya hanya bersifat sementara.

Dengan array destructuring assignment kita bisa menukar nilai variabel dengan mudah dan
tentu tanpa membuat variabel extra.

```javascript
let a = 1;
let b= 2;
console.log("Sebelum swap");
console.log("Nilai a: " + a);
console.log("Nilai b: " + b);
[a, b] = [b, a]
console.log("Setelah swap");
console.log("Nilai a: " + a);
console.log("Nilai b: " + b);
```

### Default Values
Seperti objek, pada array destructuring kita juga dapat memberikan nilai default pada variabel
yang tidak dapat terjangkau oleh array, sehingga nilai pada variabel tidak akan
menjadi undefined.

```javascript
const favorites = ["Seafood"];
const [myFood, herFood = "Salad"] = favorites
console.log(myFood);
console.log(herFood);
/* output:
Seafood
Salad
*/
```

### Spreading Operator
Spreading operator dituliskan dengan three consecutive dots (....). Sesuai namanya “Spread”,
fitur baru ES6 ini digunakan untuk membentangkan nilai array atau lebih tepatnya iterable
object menjadi beberapa elements.

menggunakan spread
operator kita dapat membentangkan nilai – nilai dalam array tersebut.

```javascript
const favorites = ["Seafood", "Salad", "Nugget", "Soup"];
console.log(...favorites);
/* output:
Seafood Salad Nugget Soup
*/
```
Terlihat kan perbedaanya? Mengapa bisa demikian? Spread operator bekerja seperti
meleburkan nilai array menjadi beberapa elemen sesuai dengan panjang nilai array-nya
sehingga jika kita menuliskan kode seperti ini:

```javascript
console.log(...favorites);
```
Sama seperti kita menuliskan kode seperti ini:
```javascript
console.log(favorites[0], favorites[1], favorites[2], favorites[3]);
```

### Spreading Operator
Spreading operator dituliskan dengan three consecutive dots (....). Sesuai namanya “Spread”,
fitur baru ES6 ini digunakan untuk membentangkan nilai array atau lebih tepatnya iterable
object menjadi beberapa elements.

Mari kita lihat contoh kode berikut:
```javascript
const favorites = ["Seafood", "Salad", "Nugget", "Soup"];
console.log(favorites);
/* output:
[ 'Seafood', 'Salad', 'Nugget', 'Soup' ]
*/
```

Nah, dengan menggunakan spread
operator kita dapat membentangkan nilai – nilai dalam array tersebut.

```javascript
onst favorites = ["Seafood", "Salad", "Nugget", "Soup"];
console.log(...favorites);
/* output:
Seafood Salad Nugget Soup
*/
```

Spread operator bekerja seperti
meleburkan nilai array menjadi beberapa elemen sesuai dengan panjang nilai array-nya,
sehingga jika kita menuliskan kode seperti ini:

```javascript
console.log(...favorites);
```

Sama seperti kita menuliskan kode seperti ini:

```
console.log(favorites[0], favorites[1], favorites[2], favorites[3]);
```
Spread operator ini cocok sekali digunakan sebagai nilai parameter pada variadic functions,
seperti console.log() atau Math.max().

```javascript
/* Math.max() -> Mencari nilai terbesar */
const numbers = [12, 32, 90, 12, 32];
// Sama seperti kita menuliskan
// console.log(Math.max(numbers[0], numbers[1], numbers[2], numbers[3])
console.log(Math.max(...numbers));
/* output
90
*/
```

Alih-alih menggabungkan nilainya,
variabel allFavorite menjadi objek array baru yang menampung dua array di dalamnya.

```javascript
const favorites = ["Seafood", "Salad", "Nugget", "Soup"];
const others = ["Cake", "Pie", "Donut"];
const allFavorites = [...favorites, ...others]
console.log(allFavorites);
```

### Rest parameter
Sebelumnya kita sudah tahu bahwa variadic function dapat menerima banyak parameter,
namun apakah kita tahu bagaimana caranya agar function dapat menerima parameter?
Jika spread operator adalah pelebur array menjadi beberapa elemen yang berbeda, rest
parameter ini adalah kebalikan dari operator tersebut.

Sebagai contoh penggunaanya, mari kita buat sebuah variadic function yang berfungsi untuk
menjumlahkan seluruh nilai argument fungsi yang diberikan.

```javascript
function sum(...numbers) {
var result = 0;
for(let number of numbers) {
result += number
}
return result;
}
console.log(sum(1,2,3,4,5));
/* output
15
*/
```

Rest parameter juga dapat digunakan pada array destructuring, di mana kita dapat
mengelompokkan nilai-nilai array yang terdestruksi pada variabel dalam bentuk array yang
lain.

```javascript
const refrigerator = ["Samsung", 50, 2, "milk", "cheese", "egg", "butter"];
const [manufacture, weight, door, ...items] = refrigerator;
console.log(manufacture);
console.log(weight);
console.log(door);
console.log(items);
/* output:
Samsung
50
2
[ 'milk', 'cheese', 'egg', 'butter' ]
*/
```

Pada kode di atas nilai dari array refrigerator dimasukkan ke individual lokal variabel
menggunakan array destructuring. Variabel manufacture, weight, door diberikan nilai index
tiga pertama dari array refrigerator, namun variabel items di mana kita menggunakan rest
parameter, akan diberikan sisa nilai yang ada sebagai array.

### Arrow Function Expression
Arrow function mirip seperti regular function secara perilaku,
namun penulisannya jauh berbeda. Sama seperti namanya, fungsi didefinisikan dengan
menggunakan tanda panah (=>) dan tentu penulisan fungsi dengan arrow ini akan lebih
singkat.

Untuk gambaran awal, perhatikan penulisan regular fungsi sebagai callback berikut:
```javascript
const upperizedNames = ["Dimas", "Widy", "Buchori"]
.map(function(name) {
return name.toUpperCase();
});
console.log(...upperizedNames);
/* output:
DIMAS WIDY BUCHORI
*/
```

Sedangkan menggunakan arrow function akan tampak seperti ini:
```javascript
const upperizedNames = ["Dimas", "Widy", "Buchori"]
.map(name => name.toUpperCase());
console.log(...upperizedNames);
/* output:
DIMAS WIDY BUCHORI
*/
```
Pada kasus fungsi yang dituliskan dalam satu baris dengan arrow function kita dapat
menghapus kata function, tanda kurung, tanda kurawal, kata return, dan semicolon (;). Kita
hanya perlu menambahkan tanda panah (=>) di antara parameter dan kode fungsinya.

### Regular function vs Arrow Function
Sekilas kita sudah tahu seperti apa arrow function, namun mungkin bila kita sama sekali
belum pernah mencobanya kita akan dibuat bingung. Pasalnya, penulisannya dibandingkan
reguler function jauh berbeda.

Untuk gambaran awal, perhatikan penulisan regular fungsi sebagai callback berikut:

```javascript
const upperizedNames = ["Dimas", "Widy", "Buchori"]
.map(function(name) {
return name.toUpperCase();
});
console.log(...upperizedNames);
/* output:
DIMAS WIDY BUCHORI
*/
```

Sedangkan menggunakan arrow function akan tampak seperti ini:

```javascript
const upperizedNames = ["Dimas", "Widy", "Buchori"]
.map(name => name.toUpperCase());
console.log(...upperizedNames);
/* output:
DIMAS WIDY BUCHORI
*/
```
Pada kasus fungsi yang dituliskan dalam satu baris dengan arrow function kita dapat
menghapus kata function, tanda kurung, tanda kurawal, kata return, dan semicolon (;). Kita
hanya perlu menambahkan tanda panah (=>) di antara parameter dan kode fungsinya.

### Regular function vs Arrow Function
Selain perbedaan dari segi sintaksis, terdapat juga perbedaan perilaku antara keduanya.
Regular function dapat berupa function declaration atau function expression, namun arrow
function hanya berupa function expression saja. Itu sebabnya arrow function memiliki nama
lengkap “arrow function expressions”.

```javascript
// function expression
const sayHello = greet => console.log(`${greet}!`);
const sayName = name => console.log(`Nama saya ${name}`);
```

Karena arrow function merupakan sebuah expression, maka ia hanya dapat digunakan untuk
disimpan pada variabel (seperti contoh kode di atas), sebagai argumen pada sebuah fungsi,
dan sebagai nilai dari properti objek.

```javascript
//disimpan dalam variabel
const sayName = name => console.log(`Nama saya ${name}`);
```

```javascript
//passed as an argument
dilemparkan sebagai argument
["Dimas", "Widdy", "Buchori"].forEach(name => console.log(`Nama saya ${name}`));
```

```javascript
//disimpan didalam properti objek
const user = {
introduce: name => console.log(`Nama saya ${name}`)
}
```

Function Parameter
Pada penggunaan arrow function kita melihat bahwa variabel yang diletakan sebelum tanda
panah (=>) adalah merupakan parameter dari fungsi.

```javascript
// name merupakan parameter dari fungsi
const sayName = name => console.log(`Nama saya ${name}`);
```
Pada arrow function jika terdapat dua atau lebih parameter fungsi kita perlu membungkusnya
dengan tanda kurung seperti ini:

```javascript
const sayHello = (name, greet) => console.log(`${greet}, ${name}!`);
sayHello("Dimas", "Selamat Pagi")
/* output:
Selamat Pagi, Dimas!
*/
```
Namun jika kita sama sekali tidak membutuhkan parameter, biarkan saja tanda kurung
tersebut kosong.

```javascript
const sayHello = () => console.log("Selamat pagi semuanya!");
sayHello()
/* output:
Selamat pagi semuanya!
*/
```

### Block Body Function
Fungsi merupakan mini program sehingga sangat mungkin terdapat lebih dari satu logika di
dalamnya. Seperti yang kita ketahui bahwa logika-logika pada pemrograman terdiri dari
banyak expression ataupun statement.
Pada contoh kode arrow function sebelumnya kita hanya menuliskan satu buah expression
sehingga penulisannya bisa sangat ringkas. Namun bagaimana jika dalam sebuah fungsi
terdapat banyak logika di dalamnya? Apakah bisa dituliskan menggunakan arrow function?
Jawabannya tentu bisa!

Sama seperti regular function, arrow function sebenarnya tidak benar-benar menghilangkan
tanda kurung kurawal ({ }) dalam penulisannya. Tanda kurung kurawal pun berfungsi sama
seperti regular function yakni menampung body function di mana tempat logika fungsi
dituliskan. Penulisan tanda kurung kurawal menjadi opsional ketika body fungsi hanya terdiri
dari satu expression atau statement saja.

Jika kita butuh lebih dari satu baris dalam body function, kita bisa menuliskannya seperti ini:
```javascript
const sayHello = language => {
if(language.toUpperCase() === "INDONESIA") {
return "Selamat Pagi!";
} else {
return "Good Morning!";
}
}
console.log(sayHello("Indonesia"));
/* output:
Selamat Pagi!
*
```
Selain itu juga, kita perlu menuliskan kembali keyword return agar fungsi tersebut dapat
mengembalikan nilai.

### This Keyword
Perbedaan karakteristik dari arrow function dan regular function selanjutnya ada pada
penggunaan keyword this. Penjelasan dari this sendiri menyusul di materi class. Namun kita
akan bahas sedikit mengenai ini untuk menggambarkan perbedaan ketika this digunakan oleh
arrow function dan regular function.

Jika sebuah regular function dipanggil dengan menggunakan keyword new. Maka nilainya
akan menjadi objek, contohnya:

```javascript
function People(name, age, hobby) {
this.name = name;
this.age = age;
this.hobby = hobby;
}
const programmer = new People("John", 18, ["Coding", "Read book", "Ping-pong"]);
console.log(programmer.name);
console.log(programmer.age);
console.log(programmer.hobby);
/* output:
John
18
[ 'Coding', 'Read book', 'Ping-pong' ]
*/
```
Objek yang dibuat menggunakan function dengan keyword new, sama halnya seperti kita
membuat objek seperti menggunakan objek literals { }.

```javascript
const programmer = {
name: "John",
age: 18,
hobby: ["Coding", "Read book", "Ping-Pong"]
}
console.log(programmer.name);
console.log(programmer.age);
console.log(programmer.hobby);
/* output:
John
18
[ 'Coding', 'Read book', 'Ping-pong' ]
*/
```

Pada objek, this keyword mengembalikan nilai objeknya sendiri. this dapat digunakan untuk
mengelola properti pada objeknya. Namun jika fungsi dipanggil tanpa menggunakan
keyword new, this akan memiliki nilai global object (Window jika di browser).

Sedangkan fungsi yang dibuat dengan menggunakan gaya arrow tidak akan pernah memiliki
nilai this, yang artinya kita tidak pernah bisa membuat objek menggunakan arrow function.
Jika kita menggunakan this pada arrow function maka nilai this itu sendiri merupakan nilai
objek di mana arrow function itu berada.

Perhatikan kedua contoh kode berikut:
### Regular Funciton ###

```javascript
function People(name, age, hobby) {
this.name = name;
this.age = age;
this.hobby = hobby;
}
// menambahkan introMyself ke People
People.prototype.introMyself = function () {
// this -> People
setTimeout(function() {
// this -> ??
console.log(`Hello! Nama saya ${this.name}, umur saya ${this.age}.`)
console.log(`Hobby saya adalah ${this.hobby}`)
}, 300)
}
const programmer = new People("John", 18, ["Coding", "Read book", "Ping-pong"]);
programmer.introMyself();
/* output:
Hello! Nama saya undefined, umur saya undefined.
Hobby saya adalah undefined
*/
```

### Arrow Function ###
```javascript
function People(name, age, hobby) {
this.name = name;
this.age = age;
this.hobby = hobby;
}
// menambahkan introMyself ke People
People.prototype.introMyself = function () {
// this -> People
setTimeout(() => {
// this -> People
console.log(`Hello! Nama saya ${this.name}, umur saya ${this.age}.`)
console.log(`Hobby saya adalah ${this.hobby}`)
}, 300)
}

const programmer = new People("John", 18, ["Coding", "Read book", "Ping-pong"]);
programmer.introMyself();


/* output:
Hello! Nama saya John, umur saya 18.
Hobby saya adalah Coding,Read book,Ping-pong
*/
```

Fungsi yang dituliskan di dalam setTimeout() dipanggil tanpa new. Itu berarti nilai
dari this jika digunakan di dalam fungsi tersebut adalah global object. Itulah mengapa output
akan menghasilkan nilai undefined ketika properti name, age, dan hobby dipanggil.
Berbeda ketika kita menuliskan arrow function di dalam setTimeout(), nilai this memiliki
nilai objek sesuai dengan konteksnya (People). Arrow function akan sangat berguna untuk
kasus seperti ini.

### Default Parameters
Fitur lainnya pada ES6 yang sangat bermanfaat adalah kita dapat menetapkan nilai default
pada parameter fungsi. Dengan menggunakan default parameters, nilai pada parameter tidak
akan menghasilkan undefined walaupun kita tidak memberikan nilai ketika fungsi tersebut
dipanggil. Default parameter dapat digunakan pada regular function ataupun arrow function.

### Reguler Function ###
```javascript
function sayHello(name = "Stranger", greet = "Hello") {
console.log(`${greet} ${name}!`);
}

sayHello("Dimas", "Hai");
sayHello();

/* output:
Hai Dimas!
Hello Stranger!
*/
```

### Arrow Function ###
```javascript
const sayHello = (name = "Stranger", greet = "Hello") => console.log(`${greet} ${name}!`);
sayHello("Dimas", "Hai");
sayHello();
/* output:
Hai Dimas!
Hello Stranger!
*/
```
Pada contoh di atas, kita menggunakan tanda assignment (=) untuk menetapkan
parameter namedengan nilai default “Stranger”, dan parameter greet dengan nilai
default “Hello”. Hal ini sangat berguna ketika kita memanggil fungsi sayHello() tanpa
menetapkan nilai parameter di dalamnya, karena walaupun kita tidak menetapkan nilainya,
kedua parameter tersebut tidak akan menghasilkan undefined.

### OOP
Paradigma OOP selalu digambarkan dengan kehidupan nyata. Visualisasi di atas
mencontohkan gambaran umum OOP di mana terdapat sebuah blueprint kucing, nilai yang
dimiliki kucing, dan kemampuan yang dapat dilakukan olehnya. Dalam OOP blueprint
tersebut dikenal dengan class (kelas), nilai yang dimiliki olehnya dikenal dengan properti,
kemampuan yang dimilikinya dikenal sebagai behaviour/method dan realisasi dari sebuah
blueprint tersebut disebut instance.

### A Class Before ES6 ###
Sebelum ES6, Hal yang paling mendekati dengan class yaitu membuat sebuah objek
menggunakan constructor function dan keyword new, lalu untuk menambahkan method kita
gunakan konsep prototype.

```javascript
function Car(manufacture, color) {
this.manufacture = manufacture;
this.color = color;
this.enginesActive = false;
}
Car.prototype.startEngines = function () {
console.log('Mobil dinyalakan...');
this.enginesActive = true;
};
Car.prototype.info = function () {
console.log("Manufacture: " + this.manufacture);
console.log("Color: " + this.color);
console.log("Engines: " + this.manufacture ? "Active" : "Inactive");
}
var johnCar = new Car("Honda", "Red");
johnCar.startEngines();
johnCar.info();
/* output:
Mobil dinyalakan...
Manufacture: Honda
Color: Red
Engines active: true
*/
```
Pada kode di atas Car merupakan constructor function yang akan membuat instance Car baru
setiapkan kode new Car() dieksekusi. Melalui Car.prototype,
method startEngines() dan carInfo() diwarisi pada setiap instance Car yang dibuat,
sehingga johnCar (sebagai instance Car) dapat mengakses kedua method tersebut.
Teknik dasar ini yang digunakan dalam membuat class di JavaScript sebelum ES6.

### ES6 Classes ### 
Dengan hadirnya class pada ES6, pembuatan class di JavaScript menjadi lebih mudah dan
juga penulisannya mirip seperti bahasa pemrograman lain berbasis class. Pembuatan class
pada ES6 menggunakan keyword class itu sendiri kemudian diikuti dengan nama class-nya.

```javascript
class Car {
// Sama seperti function constructor
constructor(manufacture, color) {
this.manufacture = manufacture;
this.color = color;
this.enginesActive = false;
}
// Sama seperti Car.prototype.startEngine
startEngines() {
console.log('Mobil dinyalanakan...');
this.enginesActive = true;
}
// Sama seperti car.prototype.info
info() {
console.log(`Manufacture: ${this.manufacture}`);
console.log(`Color: ${this.color}`);
console.log(`Engines: ${this.manufacture ? "Active" : "Inactive"}`);
}
}
const johnCar = new Car("Honda", "Red");
johnCar.startEngines();
johnCar.info();
/* output:
Mobil dinyalanakan...
Manufacture: Honda
Color: Red
engines active: true
*/Constructor
 ```
 
Jika Anda terbiasa dengan bahasa pemrograman berbasis class, pasti penulisannya sangat
serupa bukan? Walaupun dari segi sintaksis pembuatan class antara keduanya cukup berbeda,
namun perilaku dari objek yang dibuat dengan keduanya sama. Inilah mengapa class pada
ES6 hanya sebuah syntactic sugar dari konsep prototype yang sudah ada.

### Constructor ###
Deklarasi class menggunakan ES6 memiliki sifat yang sama seperti pembuatan class
menggunakan function constructor (seperti contoh sebelumnya). Namun alih-alihmenggunakan function constructordalam menginisialisasi propertinya, class ini memisahkan constructornya dan ditempatkan pada body class menggunakan method spesial yang
dinamakan constructor.

```javascript
class Car {
constructor(manufacture, color) {
this.manufacture = manufacture;
this.color = color;
this.enginesActive = false;
}
}
```
constructor biasanya hanya digunakan untuk menetapkan nilai awal pada properti
berdasarkan nilai yang dikirimkan pada constructor. Namun sebenarnya kita juga dapat
menuliskan logika di dalam constructor jika memang kita memerlukan beberapa kondisi
sebelum nilai properti diinisialisasi.constructor biasanya hanya digunakan untuk menetapkan nilai awal pada properti
berdasarkan nilai yang dikirimkan pada constructor. Namun sebenarnya kita juga dapat
menuliskan logika di dalam constructor jika memang kita memerlukan beberapa kondisi
sebelum nilai properti diinisialisasi.
Kita juga melihat penggunaan this pada constructor. Konteks dalam class,
keyword this merujuk pada instance dari class tersebut. Sehingga this dapat digunakan untuk
mengelola properti yang terdapat pada instance.

Kita juga melihat penggunaan this pada constructor. Konteks dalam class,
keyword this merujuk pada instance dari class tersebut. Sehingga this dapat digunakan untuk
mengelola properti yang terdapat pada instance.

### Instance
Setelah kita membuat class pada JavaScript, lantas bagaimana cara membuat instance dari
class tersebut? Tapi sebelumnya, apa itu instance? Instance merupakan objek yang memiliki
properti dan method yang telah ditentukan oleh blueprint-nya (class), atau singkatnya adalah
objek yang merupakan hasil realisasi dari sebuah blueprint.

Sama seperti constructor function, untuk membuat instance dari class pada ES6 kita gunakan
keyword new.

```javascript
class Car {
constructor(manufacture, color) {
this.manufacture = manufacture;
this.color = color;
this.enginesActive = false;
}
}
const johnCar = new Car("Honda", "Red");
```
Pembuatan class menggunakan ES6 lebih ketat dibandingkan dengan constructor function, di
mana dalam pembuatan instance wajib menggunakan keyword new.

Kita juga dapat membuat banyak instance dari class yang sama, dan tentunya objek yang kita
buat memiliki karakteristik (properti dan method) yang sama. Walaupun sama, namun nilai
dari propertinya bersifat unik atau bisa saja berbeda.

```javascript
class Car {
constructor(manufacture, color) {
this.manufacture = manufacture;
this.color = color;
this.enginesActive = false;
}
}
const johnCar = new Car("Honda", "Red");
const adamCar = new Car("Tesla", "Black");
console.log(johnCar.manufacture);
console.log(adamCar.manufacture);
/* output:
Honda
Tesla
*/
```

Variabel johnCar dan adamCar merupakan sebuah objek dari Car. Tentu keduanya akan
memiliki properti manufacture, color, dan enginesActive. Namun pada output kita melihat
bahwa nilai dari properti kedua objek tersebut berbeda, karena kita dapat memberikan nilai
yang berbeda pada saat objeknya dibuat.

### Property Accessor ###
Melalui objek class kita juga dapat mengubah nilai properti seperti ini:
```javascript
class Car {
constructor(manufacture, color) {
this.manufacture = manufacture;
this.color = color;
this.enginesActive = false;
}
}
const johnCar = new Car("Honda", "Red");
console.log(`Warna mobil: ${johnCar.color}`); // output -> Warna Mobil: Red
johnCar.color = "White"; // Mengubah nilai properti color menjadi white
console.log(`Warna mobil: ${johnCar.color}`); // output -> Warna Mobil: White
```


Dengan class kita juga dapat mengimplementasi getter/setter sebuah properti menjadi sebuah
method seperti ini:

```javascript
class Car {
constructor(manufacture, color) {
this.manufacture = manufacture;
this._color = color;
this.enginesActive = false;
}
get color() {
return `Warna mobile ${this._color}`;
}
set color(value) {
console.log(`Warna mobil diubah dari ${this._color} menjadi ${value}`);
this._color = value;
}
}
const johnCar = new Car("Honda", "Red");
console.log(johnCar.color); // output -> Warna Mobil: Red
johnCar.color = "White"; // Mengubah nilai properti color menjadi white
console.log(johnCar.color); // output -> Warna Mobil: White
```

Perhatikan juga ketika kita menerapkan getter/setter pada properti class. Kita perlu mengubah
atau membedakan penamaan properti aslinya dengan property accessor yang kita buat.
Berdasarkan code convention yang ada kita perlu mengubah properti asli class-nya dengan
menambahkan underscore di depan nama propertinya (_color). Tanda underscore berfungsi
sebagai tanda bahwa properti _color tidak sebaiknya diakses langsung, namun harus
melalui property accessor(getter/setter).

### Method ###
Untuk menambahkan method pada class, kita juga cukup menuliskannya pada body class,
tidak perlu melalui prototype seperti menggunakan constructor function.

```javascript
class Car {
constructor(manufacture, color) {
this.manufacture = manufacture;
this.color = color;
this.enginesActive = false;
}
startEngines() {
console.log("Mesin dinyalakan");
this.enginesActive = true;
}
info() {
console.log(`Manufacture: ${this.manufacture}`);
console.log(`Color: ${this.color}`);
console.log(`Engines: ${this.manufacture ? "Active" : "Inactive"}`);}
}
const johnCar = new Car("Honda", "Red");
johnCar.startEngines();
johnCar.info();
/* output:
Mesin dinyalakan
Manufacture: Honda
Color: Red
Engines: Active
*/
```

Dengan menggunakan class, walaupun kita menuliskan method pada body class, namun
method tersebut tetap berada pada prototype chain miliki instance yang terbuat. Kita bisa
melihat bagaimana objek yang dibuat menggunakan class pada console browser.

### Inheritance ###
Dalam gambaran dunia nyata, banyak objek yang berbeda tetapi punya kesamaan atau
kemiripan tertentu. Contohnya mobil dengan motor memiliki banyak kesamaan karena objek
tersebut merupakan kendaraan. Mobil merupakan kendaraan darat begitu juga dengan motor.
Mungkin yang membedakan objek tersebut adalah jumlah roda dan kapasitas penumpang
yang dapat ditampung.

Sama halnya pada OOP, beberapa objek yang berbeda bisa saja memiliki kesamaan dalam hal
tertentu. Di situlah konsep inheritance atau pewarisan harus diterapkan. Pewarisan dapat
mencegah kita melakukan perulangan kode.

Dengan teknik inheritance, kita bisa mengelompokkan properti dan method yang sama.
Caranya dengan membuat sebuah kelas baru yang nantinya akan diturunkan sifatnya pada

Ketika class Vehicle telah dibuat, kelas lainnya dapat melakukan extends pada kelas tersebut
untuk mewarisi sifatnya. Dalam pewarisan, class Vehicle dapat disebut sebagai super atau
parent class. Kelas yang mewarisi sifat dari parent class disebut dengan child class.

```javascript
class Vechile {
            constructor(licensePlate, manufacture) {
                this.licensePlate = licensePlate;
                this.manufacture = manufacture;
                this.engineActive = false;
            }
            startEnggines() {
                console.log(`Mesin kendaraan ${this.licensePlate} dinyalakan!`);
            }

            info() {
                console.log(`Nomor Kendaraan: ${this.licensePlate}`);
                console.log(`Manufacture: ${this.manufacture}`);
                console.log(`Mesin: ${this.engineActive ? "Active": "Inactive"}`);
            }

            parking() {
                console.log(`Kendaraan ${this.licensePlate} parkir!`);
            }
        }
        class Car extends Vechile {
            constructor(lisencePlate, manufacture, wheels) {
                super(lisencePlate, manufacture);
                this.wheels = wheels;
            }
            droveOff() {
                console.log(`Kendaraan ${this.licensePlate} melaju!`);
            }
            openDoor() {
                console.log(`Membuka pintu!`);
            }

        }
        const car = new Car("hahaha", "honda", 4);
        car.startEnggines();
```
Dalam melakukan pewarisan kelas, tidak ada tingkatan yang membatasinya. Maksudnya, kita
dapat mewariskan sifat kelas A pada kelas B, lalu kelas B mewarisi sifatnya kembali pada
kelas C dan selanjutnya. Sama halnya dengan Nenek kita mewarisi sifatnya kepada orang tua
kita kemudian orang tua kita mewarisi sifatnya kepada kita.

### Static Method ###
Seluruh kendaraan pasti butuh yang namanya perawatan bukan? Jika iya, tentu kita perlu
membuat method repair untuk memperbaiki kendaraan tersebut. Dalam analogi dunia nyata,
ketika kendaraan mengalami kerusakan maka kendaraan tersebut akan diperbaiki di bengkel
(factory), sehingga kita perlu membuat class baru yang berperan sebagai factory, sebutlah
class tersebut VehicleFactory. Di dalam kelas VehicleFactory terdapat satu
method repair() yang dapat menerima banyak kendaraan sebagai parameternya.

sebelum ada static method
```javascript
class Vehicle {
constructor(licensePlate, manufacture) {
this.licensePlate = licensePlate;
this.manufacture = manufacture;
this.engineActive = false;
}
/*
kode lainnya
*/
}
/* kode lainnya dalam pembuatan class Car,
Motorcycle, dsb. */
class VehicleFactory {
repair(vehicles) {
vehicles.forEach(vehicle => {
console.log(`Kendaraan ${vehicle.licensePlate} sedang melakukan perawatan`)
})
}
}
const johnCar = new Car("H121S", "Honda", 4);
const dimasCar = new Car("TA1408K", "Tesla", 4);
/* Membuat instance untuk memanggil fungsi repair */
const vehicleFactory = new VehicleFactory();
vehicleFactory.repair([johnCar, dimasCar]);
```

Static method merupakan method yang tidak dapat dipanggil oleh
instance dari class, namun dapat dipanggil melalui class-nya sendiri.
```javascript
class Vehicle {
constructor(licensePlate, manufacture) {
this.licensePlate = licensePlate;
this.manufacture = manufacture;
this.engineActive = false;
}
/*
kode lainnya
*/
}
/* kode lainnya dalam pembuatan class Car,
Motorcycle, dsb. */
class VehicleFactory {
static repair(vehicles) {
vehicles.forEach(vehicle => {
console.log(`Kendaraan ${vehicle.licensePlate} sedang melakukan perawatan`)
})
}
}
lass VehicleFactory {
static repair(vehicles) {
vehicles.forEach(vehicle => {
console.log(`Kendaraan ${vehicle.licensePlate} sedang melakukan perawatan`)
})
}
}
const johnCar = new Car("H121S", "Honda", 4);
const dimasCar = new Car("TA1408K", "Tesla", 4);
/* Pemanggilan method repair langsung dari class-nya */
VehicleFactory.repair([johnCar, dimasCar]);
```

## Synchronous vs Asynchronous
Dalam synchronous program, jika kita menuliskan dua baris kode maka baris kode yang
kedua tidak bisa dieksekusi sebelum mengeksekusi kode pada baris pertama.
dalam kehidupan nyata ketika mengantri membeli kopi di sebuah kedai kopi.
Kita tidak bisa mendapatkan kopi sebelum semua antrian di depan kita selesai dilayani, sama
hal nya orang yang di belakang kita pun harus menunggu gilirannya.

Dalam asynchronous program, jika kita menuliskan dua baris kode, kita dapat membuat baris
kode kedua dieksekusi tanpa harus menunggu kode pada baris pertama selesai dieksekusi.
Dalam dunia nyata kita bisa membayangkan dengan memesan kopi namun memesannya
melalui pelayan, di mana sembari kita menunggu pesannya datang, kita dapat melakukan
aktivitas lain seperti membuka laptop, menulis, hingga kopi itu datang dengan sendirinya.

### setTimeout ###
Fungsi setTimeout() merupakan cara yang paling mudah untuk membuat kode kita dijalankan
secara asynchronous. Fungsi ini menerima dua buah parameter. Pertama adalah fungsi yang
akan dijalankan secara asynchronous, dan kedua adalah
nilai number dalam milisecond sebagai nilai tunggu sebelum fungsi dijalankan.

```javascript
 console.log("Selamat datang");
        setTimeout(() => {
            console.log("Terimakasih sudah mampir, silakan datang kembali!");
        }, 300)
        console.log("Terimakasih sudah mampir, silakan datang kembali!");
```

Jika kita hanya mengenal program secara synchronous, maka kita dapat membayangkan
hasilnya memiliki urutan sebagai berikut:
* Mencetak -> Selamat datang!
* Menunggu selama tiga detik
* Mencetak -> Terima kasih sudah mampir, silakan datang kembali!
* Mencetak -> Ada yang bisa dibantu?

Namun nyatanya setTimeout() tidak akan menghentikan JavaScript untuk melakukan
eksekusi kode pada baris berikutnya. Sehingga urutannya menjadi seperti berikut:

* Mencetak -> Selamat datang!
* Mencetak -> Ada yang bisa dibantu?
* Menunggu selama tiga detik
* Mencetak -> Terimakasih sudah mampir, silakan datang kembali!

### Callback Function ###
Hal yang membuat bingung ketika kita bekerja dengan synchronous dan asynchronous
program adalah bagaimana menangani suatu nilai yang didapatkan secara asynchronous pada
program yang berjalan secara synchronous. Contohnya seperti kode berikut:

```javascript
const getCake = () => {
let cake = null;
console.log("Sedang membuat kue, silakan tunggu ....")
setTimeout(() => {
cake = "Kue Selesai!"
}, 3000)
return cake;
}
const cake = getCake();
console.log(cake);
/*output:
Sedang membuat kue, silakan tunggu ....
null
*/
```

Jika kita melakukan hal seperti ini untuk mencetak nilai cake yang sesungguhnya, maka hal
tersebut tidak akan pernah terjadi. Karena seperti yang sudah kita ketahui
fungsi setTimeout() tidak akan menghentikan JavaScript untuk mengeksekusi kode yang ada
selanjutnya. Jadi fungsi getCake()akan selalu mengembalikan nilai null, karena kode return
cake akan dieksekusi terlebih dahulu dibandingkan dengan cake = “Kue Selesai!”. Kode
asynchronous perlu disusun dengan cara yang berbeda dari synchronous code. Cara paling
dasar adalah dengan menggunakan callback function.

```javascript
const getCake = callback => {
let cake = null;
console.log("Sedang membuat kue, silakan tunggu ....")
setTimeout(() => {
cake = "Kue Selesai!";
callback(cake);
}, 3000)
}
getCake(cake => {
console.log(cake);
})
/* output:
Sedang membuat kue, silakan tunggu ....
---- setelah 3 detik ----
Kue Selesai!
*/
```

### Promise ###
Fitur ini berfungsi seperti namanya, yaitu untuk membuat janji. Mari kita analogikan kembali
dalam dunia nyata. Ketika kita memesan kopi kepada pelayan, maka secara tidak langsung
pelayan tersebut berjanji kepada kita untuk membuatkan kopi kemudian menghidangkannya
pada kita. Namun janji bisa hanya tinggal janji. Dalam dunia nyata pun, janji bisa juga tidak
terpenuhi, entah itu karena kopi pesanan kita sedang kosong, atau mesin pembuat kopi itu
sedang rusak.

Nah, Promise memiliki perilaku yang sama dengan analogi yang digambarkan tadi. Dalam
promise terdapat 3 (tiga) kondisi, yakni:

* Pending (Janji sedang dalam proses)
* Fulfilled (Janji terpenuhi)
* Rejected (Janji gagal terpenuhi)

Situs MDN mengatakan Promise merupakan sebuah objek yang digunakan untuk membuat
sebuah perhitungan (kode) ditangguhkan dan berjalan secara asynchronous. Untuk membuat
objek promise, kita gunakan keyword new diikuti dengan constructor dari Promise:

```javascript
const coffee = new Promise();
```
Namun jika kita jalankan kode tersebut, akan mengakibatkan eror seperti ini:

```javascript
/* ERROR: Promise resolver undefined is not a function */
```
Di dalam constructor Promise kita perlu menetapkan resolver function atau bisa
disebut executor function di mana fungsi tersebut akan dijalankan secara otomatis ketika
constructor Promise dipanggil.

```javascript
const executorFunction = (resolve, reject) => {
const isCoffeeMakerReady = true;
if(isCoffeeMakerReady) {
resolve("Kopi berhasil dibuat");
} else {
reject("Mesin Kopi tidak bisa digunakan!")
}
}
const makeCoffee = new Promise(executorFunction);
console.log(makeCoffee);
/* output:
Promise { 'Kopi berhasil dibuat' }
*/
```

Executor function dapat memiliki dua parameter, yang berfungsi
sebagai resolve() dan reject()function. Berikut penjelasan detailnya:

* resolve() merupakan parameter pertama pada executor function. Parameter ini
merupakan fungsi yang dapat menerima satu parameter, biasanya kita gunakan untuk
mengirimkan data ketika promise berhasil dilakukan. Ketika fungsi ini terpanggil,
kondisi Promise akan berubah dari pending menjadi fulfilled.

* reject() merupakan parameter kedua pada executor function. Parameter ini merupakan fungsi
yang dapat menerima satu parameter yang digunakan untuk memberikan alasan mengapa
Promise tidak dapat terpenuhi. Ketika fungsi ini terpanggil, kondisi Promise akan berubah
dari pending menjadi rejected.

Executor function akan berjalan secara asynchronous hingga akhirnya kondisi Promise
berubah dari pending menjadi fulfilled/rejected.
Pada contoh kode di atas, berikut ini outputnya:

```javascript
/* output:
Promise { 'Kopi berhasil dibuat' }
*/
```
Kenapa demikian? Executor function mengeksekusi resolve() dengan membawa data string
“Kopi berhasil dibuat”. Coba kita ubah nilai dari
variabel isCoffeeMakerReady menjadi false, maka executor function akan
mengeksekusi reject() dengan membawa pesan rejection "Mesin Kopi tidak bisa
digunakan!".

Dari output yang dihasilkan baik ketika fulfilled ataupun rejected masih berupa Promise,
bukan nilai yang dibawa oleh fungsi resolve atau reject itu sendiri. Lantas bagaimana cara
untuk mengakses nilai yang dibawa oleh fungsi-fungsi tersebut? Caranya adalah dengan
menggunakan method .then() yang tersedia pada objek Promise.

### onFulfilled and onRejected Functions ###
Untuk menangani nilai yang dikirimkan oleh resolve() ketika Promise onFulfilled, kita
gunakan method .then() pada objek promise yang kita buat. Lalu di dalammethod .then() kita berikan parameter berupa function yang berguna sebagai handle callback.

```javascript
const executorFunction = (resolve, reject) => {
const isCoffeeMakerReady = true;
if(isCoffeeMakerReady) {
resolve("Kopi berhasil dibuat");
} else {
reject("Mesin Kopi tidak bisa digunakan!")
}
}
const handlerSuccess = resolvedValue => {
console.log(resolvedValue);
}
const makeCoffee = new Promise(executorFunction);
makeCoffee.then(handlerSuccess)
/* output:
Kopi berhasil dibuat
*/
```
* makeCoffee merupakan objek promise yang akan menghasilkan resolve() dengan membawa
nilai ‘Kopi berhasil dibuat’.
* Lalu kita mendeklarasikan fungsi handlerSuccess() yang mencetak nilai dari parameternya.
* Kemudian kita memanggil method .then() dari makeCoffee dan
memberikan handlerSuccess sebagai parameternya.
* etika makeCoffee terpenuhi (fulfilled), maka handlerSuccess() akan terpanggil
dengan parameter nilai yang dibawa oleh resolve(). Sehingga output akan
menghasilkan “Kopi berhasil dibuat”.

Namun bagaimana jika objek promise menghasilkan kondisi rejected? Bagaimana cara
menangani nilai yang dikirimkan oleh reject()?

```javascript
const executorFunction = (resolve, reject) => {
const isCoffeeMakerReady = false;
if(isCoffeeMakerReady) {
resolve("Kopi berhasil dibuat");
} else {
reject("Mesin Kopi tidak bisa digunakan!")
}
}
const handlerSuccess = resolvedValue => {
console.log(resolvedValue);
}
const handlerRejected = rejectionReason => {
console.log(rejectionReason);
}
const makeCoffee = new Promise(executorFunction);
makeCoffee.then(handlerSuccess,handlerRejected);


/* output:
Mesin Kopi tidak bisa digunakan!
*/
```

### onRejected with Catch Method ###
Method .catch() mirip seperti .then(). Namun method ini hanya menerima satu parameter
function yang digunakan untuk rejected handler. Method .catch() ini akan terpanggil
bilamana objek promise memiliki kondisi onRejected. Berikut contoh penggunaan dari
method
```javascript
const executorFunction = (resolve, reject) => {
const isCoffeeMakerReady = false;
if(isCoffeeMakerReady) {
resolve("Kopi berhasil dibuat");
} else {
reject("Mesin Kopi tidak bisa digunakan!")
}
}
const handlerSuccess = resolvedValue => {
console.log(resolvedValue);
}
const handlerRejected = rejectionReason => {
console.log(rejectionReason);
}
const makeCoffee = new Promise(executorFunction);
makeCoffee.then(handlerSucces)
.catch(handlerRejected);


/* output:
Mesin Kopi tidak bisa digunakan!
*/
```

Dengan menggunakan method catch(), kita dapat menerapkan prinsip separation of concerns
sekaligus membuat kodenya lebih rapi

### Chaining Promise ###
Dengan promise kita dapat melakukan proses asynchronous operation secara berantai.
Contohnya, Ketika kita memesan kopi robusta, maka tahapan yang dilalui oleh barista adalah
memastikan biji kopi tersedia, membuat kopi, lalu menghidangkannya kepada pelanggan.
Tahapan tersebut harus barista lakukan secara berurutan.

```javascript
const state = {
isCoffeeMakerReady: true,
seedStocks: {
arabica: 250,
robusta: 60,
liberica: 80
}
}
const getSeeds = (type, miligrams) => {
return new Promise((resolve, reject) => {
if(state.seedStocks[type] >= miligrams) {
state.seedStocks[type] -= miligrams;
resolve("Biji kopi didapatkan!")
} else {
reject("Maaf stock kopi habis!")
}
});
}
onst makeCoffee = seeds => {
return new Promise((resolve, reject) => {
if(state.isCoffeeMakerReady) {
resolve("Kopi berhasil dibuat!")
} else {
reject("Maaf mesin tidak dapat digunakan!");
}
})
}
const servingToTable = coffee => {
return new Promise(resolve => {
resolve("Pesanan kopi sudah selesai!")
})
}
function reserveACoffee(type, miligrams) {
getSeeds(type, miligrams)
.then(makeCoffee)
.then(servingToTable)
.then(resolvedValue => {
console.log(resolvedValue);
})
.catch(rejectedReason => {
console.log(rejectedReason);
})
}
/* Silakan ubah tipe kopi dan kuantitasnya, untuk mendapatkan promise rejection*/
reserveACoffee("liberica", 80);
```
Ketika kita memesan kopi melalui fungsi reserveACoffee(), pertama barista akan mengambil
biji kopi melalui fungsi getSeeds(). Fungsi ini membutuhkan 2 (dua) parameter
yaitu type (tipe kopi), dan miligrams (banyak kopi yang diperlukan). Fungsi ini
mengembalikan objek promise, di mana jika biji yang dipesan tersedia akan
mengembalikan resolve -> “Biji kopi didapatkan!”. Namun jika biji kopi tidak tersedia, maka
akan mengembalikan reject -> “Maaf stok kopi habis!”. Berikut kode dari fungsi getSeeds:

Lalu kita panggil method .then() dari fungsi getSeeds, dan memberikan parameter
fungsi makeCoffee di dalamnya. Fungsi makeCoffee() akan menerima parameter berupa nilai
yang dibawa resolve pada getSeeds(). Fungsi ini juga mengembalikan nilai promise juga, dimana jika mesin kopi siap digunakan, maka akan mengembalikan resolve -> “Kopi berhasil
dibuat”. Namun jika sebaliknya, mesin kopi tidak siap untuk digunakan, maka akan
mengembalikan reject -> “Maaf mesin tidak dapat digunakan!”. Berikut kode dari
fungsi makeCoffee:

Setelah kita mendapatkan kopi dari fungsi makeCoffee. Lalu kopi tersebut dihidangkan
dengan menggunakan fungsi servingToTable. Fungsi ini juga mengembalikan promise
dengan resolve yang membawa nilai “Pesanan kopi sudah selesa!”.

Lalu kita gunakan method .then() yang terakhir untuk mencetak nilai yang dikembalikan oleh
fungsi servingToTable.
Kemudian yang paling terakhir adalah memanggil method .catch(). Di mana method ini akan
menangani promise rejection yang terjadi. Entah itu disebabkan oleh biji kopi yang dipesan
habis, ataupun mesin kopi tidak dapat digunakan.

### Promise All ###
Materi sebelumnya kita belajar bagaimana promise dapat menangani situasi di mana
terdapat asynchronous process yang saling membutuhkan untuk melaksanakan tugasnya.

Namun bagaimana jika kita ingin menjalankan banyak promise sekaligus namun tidak
memperdulikan urutan?

Kita sering pergi ke cafe untuk menikmati secangkir kopi bersama teman kuliah ataupun
rekan kerja. Ketika memesan kopi, biasanya kita lakukan secara bersamaan. Meskipun kopi
yang kita pesan berbeda, tak jarang pelayan menghidangkannya berbarengan dengan kopi
yang teman kita pesan. Nah pada kasus inilah pelayan menggunakan teknik Promise.all().

Method Promise.all() dapat menerima banyak promise (dalam bentuk array) pada
parameternya. Kemudian method tersebut akan mengembalikan nilai seluruh hasil dari
promise yang kita tetapkan dalam bentuk array.

```javascript
const arabicaOrder = () => {
          return new Promise(resolve => {
              setTimeout(()=>{
                  resolve("Kopi arabica selesai");
              }, 4000)
          })
      }
      const robustaOrder = () =>{
          return new Promise(resolve =>{
              setTimeout(()=>{
                  resolve("kopi robusta selesai")
              },2000)
          }) 
      }
      const libericaOrder = () =>{
          return new Promise(resolve =>{
              setTimeout(()=>{
                  resolve("kopi liberica selesai")
              },3000)
          }) 
      }
      const promises = [arabicaOrder(),robustaOrder(),libericaOrder()];
      Promise.all(promises)
      .then(resolvedValue => console.log(resolvedValue))
```

Ketika kode di atas dieksekusi, kita perlu menunggu 4 detik sebelum akhirnya output pada
console ditampilkan. Ini menunjukan bahwa Promise.all() akan mengembalikan nilai jika
seluruh proses promise di dalamnya selesai dijalankan.

Urutan nilai yang dihasilkan oleh method ini sesuai dengan urutan promise yang kita
tentukan pada parameternya
```javascriptconst promises = [arabicaOrder(), robustaOrder(), libericaOrder()];
Promise.all(promises)
.then(resolvedValue => {
console.log(resolvedValue);
})
```

### Async-Await Syntax ###
```javascript
const getCoffee = () => {
            return new Promise((resolve, reject) => {
                const seeds = 100;
                setTimeout(() => {
                    if (seeds >= 10) {
                        resolve("Coffee didapatkan!");
                    } else {
                        reject("Biji kopi habis!")
                    }
                }, 1000)
            })
        }

        async function makeCoffee() {
            const coffee = await getCoffee();
            console.log(coffee);
        }
        makeCoffee();
```
Keyword async digunakan untuk memberitahu JavaScript untuk menjalankan
fungsi makeCoffee()secara asynchronous. Lalu keyword await digunakan untuk
menghentikan proses pembacaan kode selanjutnya sampai fungsi getCoffee() mengembalikan
nilai promise resolve.

> “Walaupun await menghentikan proses pembacaan kode selanjutnya pada
fungsi makeCoffee. Tapi ini tidak akan mengganggu proses runtime sesungguhnya pada
JavaScript (global). Karena fungsi makeCoffee berjalan secara asynchronous. Kita tidakdapat menggunakan await tanpa membuat function dalam scope-nya berjalan secara asynchronous.”

### Handle onRejected using async/await ###
Perlu jadi catatan bahwa await hanya akan mengembalikan nilai jika promise berhasil
dilakukan (onFulfilled). Lantas bagaimana jika promise gagal dilakukan (onRejected)?
Kembali lagi kepada prinsip synchronous code. Kita dapat menangani sebuah eror atau
tolakan dengan menggunakan try...catch.

Ketika menggunakan async/await, biasakan ketika mendapatkan resolved value dari sebuah
promise, untuk menempatkannya di dalam block try
```javascript
const getCoffee = () => {
            return new Promise((resolve, reject) => {
                const seeds = 9;
                setTimeout(() => {
                    if (seeds >= 10) {
                        resolve("Coffee didapatkan!");
                    } else {
                        reject("Biji kopi habis!")
                    }
                }, 1000)
            })
        }

        async function makeCoffee() {
            try{
            const coffee = await getCoffee();
            console.log(coffee);
            } catch(rejectedReason) {
              console.log(rejectedReason);
            }
        }
        makeCoffee();
        /* output
        Biji kopi habis!
        */
```

### Chaining Promise using async/await ###
```javascript
const state = {
            isCoffeeMakerReady: true,
            seedStocks: {
                arabica: 250,
                robusta: 60,
                liberica: 80
            }
        }
        const getSeeds = (type, miligrams) => {
            return new Promise((resolve, reject) => {
                if (state.seedStocks[type] >= miligrams) {
                    state.seedStocks[type] -= miligrams;
                    resolve("Biji kopi didapatkan!")
                } else {
                    reject("Maaf stock kopi habis!")
                }
            });
        }
        const makeCoffee = seeds => {
            return new Promise((resolve, reject) => {
                if (state.isCoffeeMakerReady) {
                    resolve("Kopi berhasil dibuat!")
                } else {
                    reject("Maaf mesin tidak dapat digunakan!");
                }
            })
        }
        const servingToTable = coffee => {
            return new Promise(resolve => {
                resolve("Pesanan kopi sudah selesai!")
            })
        }

        async function reserveACoffee(type, miligrams) {
            try{
            const seeds = await getSeeds(type, miligrams);
            const coffee = await makeCoffee(seeds);
            const result = await servingToTable(coffee);
            console.log(result);
        } catch (rejectionReason){
            console.log(rejectionReason);
        }
        }
        reserveACoffee("liberica", 80);
```
Async/await ini menjadi fitur baru yang sangat berguna. Terlebih untuk kita yang lebih
nyaman menangani proses asynchronous dengan menggunakan gaya synchronous.

### Node.js Export and Import Modules ###
module bekerja dengan cara exporting atau importing nilai baik itu variabel, fungsi, array, objek ataupun
class agar dapat digunakan pada berkas JavaScript lain. Dalam satu berkas
JavaScript terdiri dari satu module, dan di dalamnya kita dapat
melakukan exportlebih dari satu nilai.
Dalam environment Node.js, untuk melakukan import dan export module kita
gunakan module.exports. Setiap berkas JavaScript yang berjalan pada Node,
memiliki objek module lokal yang memiliki properti exports. Properti tersebut
digunakan untuk mendefinisikan nilai apa yang akan diekspor dari berkas tersebut.
Kode di bawah ini merupakan contoh bagaimana cara melakukan export nilai
dengan menggunakan module.exports.
```javascript
const coffeeStock = {
    arabica: 100,
    robusta: 150,
    liberica: 200
 }
module.exports = coffeeStock
```
Berkas state.js

Kode module.exports = coffeeStock membuat object coffeeStock diterapkan
sebagai nilai dari module.exports. Di mana nanti nilai properti exports ini akan
digunakan (import) pada berkas JavaScript lain.
Jika mencoba melihat nilai module yang ada pada berkas state.js dengan
menambahkan kode console.log(module) di akhir berkasnya. Maka kita akan
melihat objek coffeeStock menjadi nilai dari properti exports.

Lalu bagaimana caranya untuk melakukan import atau menggunakan objek yang
sudah di-export pada berkas lain? Caranya adalah dengan menggunakan
method require().

* index.js
```javascript
const coffeeStock = require('./state.js');
console.log(coffeeStock);
/* output
{ arabica: 100, robusta: 150, liberica: 200 }
*/
```

* state.js
```javascript
const coffeeStock = {
    arabica: 100,
    robusta: 150,
    liberica: 200
}
module.exports = coffeeStock;
```
Dengan begitu variabel coffeeStock akan memiliki
nilai module.exports yang sama pada berkas state.js. Setelah mendapatkan
nilainya, kita bebas menggunakannya layaknya variabel lokal pada biasanya.

```javascript
const coffeeStock = require('./state.js');
const makeCoffee = (type, miligrams) => {
if(coffeeStock[type] >= miligrams) {
console.log("Kopi berhasil dibuat!")
} else {
console.log("Biji kopi habis!")
}
}
makeCoffee("robusta", 80);

/* output:module.exports = {coffeeStock, isCoffeeMakerReady};
Kopi berhasil dibuat!
 *
```

### Multiple export value in Node.js ###

Sebenarnya nilai yang diekspor tetaplah satu, namun jika terdapat kasus di mana
kita ingin mengekspor lebih dari satu nilai, kita dapat memanfaatkan objek literals { }.
Contohnya, mari kita kita tambahkan variabel isCoffeeMakerReady pada
berkas state.js.
* state.js

```javascript
const coffeeStock = {
    arabica: 100,
    robusta: 150,
    liberica: 200
}
const isCoffeeMakerReady = true;
module.exports = {coffeeStock, isCoffeeMakerReady};
```

* index.js
```javascript
const {coffeeStock, isCoffeeMakerReady} = require('./state.js');
console.log(coffeeStock);
/* output
{ arabica: 100, robusta: 150, liberica: 200 }
true
*/
```
### ES6 Modules ###
Jika kita berada di luar environment Node.js, contohnya browser, kita tetap bisa
melakukan impor dan ekspor module JavaScript dengan menggunakan keyword
import dan export yang tersedia mulai dari ES6.

Pada ES6 module, jika kita hanya mengekspor satu nilai
pada sebuah berkas JavaScript baik itu primitive value, function, array, object
ataupun class, kita gunakan keyword export default

```javascript
const coffeeStock = {
    arabica: 100,
    robusta: 150,
    liberica: 200
}
export default coffeeStock;
```

Lalu bagaimana cara untuk mengimpor nilainya? Kita dapat melakukannya dengan
menggunakan keyword import ... from seperti berikut ini:



