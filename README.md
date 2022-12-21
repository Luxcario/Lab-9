# Lab9


Nama : Muhamad David Ali

NIM : 312210291

Kelas : TI 22 A1


 ## Exception Handling
 - Exception (eksepsi) merupakan suatu kesalahan (error) yang terjadi saat proses eksekusi program sedang berjalan,
 - Kesalahan ini akan menyebabkan program berakhir dengan tidak normal.
## Handling
- Penanganan file adalah bagian penting dari aplikasi apa pun.
## Assertion
Assertion(pernyataan) adalah kewajaran program yang kamu bisa aktif/nonaktifkan ketika kamu selesai menjalankan program.
### The Assert Statement
- Saat menemukan pernyataan, Python mengevaluasi ekspresi yang menyertainya, yang mana semoga benar. Jika ekspresi salah, Python memunculkan pengecualian AssertionError.
##### Sintaks untuk pernyataan yaitu :

assert Expression[, Arguments]

Jika pernyataan gagal, Python menggunakan ArgumentExpression ArgumentExpression sebagai argumen argumen untuk AssertionError AssertionError.
Pengecualian AssertionError Pengecualian AssertionError dapat ditangkap dan ditangani ditangani seperti pengecualian lainnya menggunakan try-
kecuali pernyataan, tetapi jika dibiarkan, mereka akan menghentikan program dan menghasilkan backtrace.
#### Contoh
- Berikut adalah fungsi fungsi yang mengubah suhu dari derajat Kelvin menjadi derajat Fahrenheit.Karena nol derajat Kelvin dingin, fungsi fungsi menyimpannya jika melihat negatif negatif suhu.
- Ketika kode di bawah dijalankan, menghasilkan hasil sebagai berikut:
~~~
#!/usr/bin/python
def KelvinToFahrenheit(Temperature):
    assert (Temperature >= 0),"Colder than absolute zero!"
    return ((Temperature-273)*1.8)+32   
print (KelvinToFahrenheit(273))
print (int(KelvinToFahrenheit(505.78)))
print (KelvinToFahrenheit(-5))
~~~
![Screenshot](https://user-images.githubusercontent.com/116184002/208794838-0e090633-1a4f-475c-a8ef-41da450994f0.png)


### Menangani Pengecualian
Jika Anda memiliki beberapa kode mencurigakan yang mungkin mengeluarkan pengecualian, Anda dapat mempertahankan program Anda letakkan kode yang mencurigakan di *try: blok. Setelah coba: blok, sertakan pernyataan sertakan **except:* statemen, diikuti oleh blok kode yang menangani masalah seanggun mungkin.
#### Contoh
- Contoh-contoh ini membuka file, menulis konten file, dan keluar dengan aman karena ada tidak masalah
- Ketika kode di bawah dijalankan, menghasilkan hasil sebagai berikut:
~~~
#!/usr/bin/python
try:
    fh = open("testfile", "w")
    fh.write("This is my test file for exception handling!!")
except IOError:
    print ("Error: can\'t find file or read data")
else:
    print ("Written content in the file successfully")
fh.close()
~~~
![Screenshot](https://user-images.githubusercontent.com/116184002/208798519-4118d0a7-4a59-481a-8175-bc750440ba3b.png)


- Contoh ini mencoba membuka file yang Anda tidak memiliki izin menulis, sehingga membuat file pengecualian
- Ketika kode di bawah dijalankan, menghasilkan hasil sebagai berikut:
~~~
#!/usr/bin/python
try:
    fh = open("testfile", "r")
    fh.write("This is my test file for exception handling!!")
except IOError:
    print ("Error: can\'t find file or read data")
else:
    print ("Written content in the file successfully")
~~~
![Screenshot](https://user-images.githubusercontent.com/116184002/208798602-58486003-4798-409a-9864-225d1a364a53.png)


### Fasal kecuali tanpa Pengecualian
- Anda juga dapat menggunakan pernyataan exception tanpa exception yang didefinisikan sebagai berikut:

try:
You do your operations here;
......................
except:
If there is any exception, then execute this block.
......................
else:
If there is no exception then execute this block.

Pernyataan coba-kecuali jenis ini menangkap semua pengecualian pengecualian yang terjadi. Menggunakan percobaan seperti try-expect pernyataan tidak dianggap sebagai praktik pemrograman yang baik, karena mereka menangkap semuanya pengecualian tetapi tidak membuat programmer mengidentifikasi kemungkinan penyebab masalah terjadi
### Klausa kecuali dengan Berbagai Pengecualian
- Anda juga dapat menggunakan pernyataan exception yang sama untuk menangani beberapa exception sebagai berikut:

try:
You do your operations here;
......................
except(Exception1[, Exception2[,...ExceptionN]]]):
If there is any exception from the given exception list,
then execute this block.
......................
else:
If there is no exception then execute this block.

### Klausa coba-akhirnya
#### Contoh
- Jika Anda tidak memiliki izin untuk membuka file dalam mode tulis yang dapat ditulis, maka ini akan menghasilkan hasil berikut:
~~~
#!/usr/bin/python
try:
    fh = open("testfile", "w")
    fh.write("This is my test file for exception handling!!")
finally:
    print ("Error: can\'t find file or read data")
~~~
![Screenshot](https://user-images.githubusercontent.com/116184002/208799139-719ce62b-45ca-4105-aeb3-a8d960a3916d.png)

- Contoh yang sama dapat ditulis lebih bersih sebagai berikut:
~~~
#!/usr/bin/python
try:
    fh = open("testfile", "r")
    try:
        fh.write("This is my test file for exception handling!!")
    finally:
        print ("Going to close the file")
        fh.close()
except IOError:
    print("Error : can\'t find file or read data") 
~~~
![Screenshot](https://user-images.githubusercontent.com/116184002/208800290-febb7520-fc83-4612-9fed-208645c5629b.png)


Ketika exception dilempar ke dalam blok try, eksekusi segera dilanjutkan ke akhir memblok. Setelah semua pernyataan di blok akhirnya dieksekusi, pengecualian dimunculkan lagi dan ditangani dalam pernyataan kecuali jika ada di lapisan berikutnya yang lebih tinggi dari percobaan-kecuali penyataan.
### Argumen Pengecualian
#### Contoh
- Berikut adalah contoh untuk satu pengecualian
- Ketika kode di bawah dijalankan, menghasilkan hasil sebagai berikut:
~~~
# Define a function here.

def temp_convert(var):
    try:
        return int(var)
    except ValueError(Argument):
        print("The argument does not contain numbers\n", Argument)
# Call above function here.
temp_convert("xyz")
~~~
![Screenshot](https://user-images.githubusercontent.com/116184002/208800986-a2f1616b-2ad0-4b5c-9e11-c2275723a3a0.png)

### Melempar Pengecualian
#### Contoh
- Pengecualian dapat berupa string, kelas, atau objek. Sebagian besar pengecualian adalah pengecualian dari inti Python menimbulkan adalah kelas, dengan argumen=argumen yang merupakan turunan dari kelas. Mendefinisikan pengecualian barucukup mudah dan dapat dilakukan sebagai berikut:
~~~
def functionName( level ):
    if level < 1:
        raise("Invalid level!". level)
        # The code below to thi would not be executed
        # if we raise the exception
~~~
![Screenshot](https://user-images.githubusercontent.com/116184002/208801627-8e3d894b-7c4e-4ad0-a120-a1a4a6e660f3.png)

### Pengecualian yang Ditetapkan Pengguna
- Python juga memungkinkan Anda membuat pengecualian sendiri dengan menurunkan kelas-kelas dari yang standar pengecualian bawaan.
- Berikut adalah contoh-contoh yang terkait dengan RuntimeError. Di sini, kelas dibuat yang merupakan subkelas dari subkelas RuntimeError. Ini berguna saat Anda perlumenampilkan tampilan informasi yang lebih spesifik saat e pengecualian tertangkap.
- Di blok coba, pengecualian yang ditentukan pengguna dimunculkan dan ditangkap di blok kecuali. Itu variabel e digunakan untuk membuat instance dari kelas Networkerror.
~~~
class Networkerorr(RuntimeError):
    def __init__ (self, arg):
        self.args = arg
try:
    raise Networkerror("Bad hostname")
except Networkerror(e):
    print(e.args)
~~~
![Screenshot](https://user-images.githubusercontent.com/116184002/208802262-236a4759-d9d1-4561-b412-c8de6436dae9.png)



### Sekian dari saya terima kasih........
