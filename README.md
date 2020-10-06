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
