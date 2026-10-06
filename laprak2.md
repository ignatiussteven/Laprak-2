# <h1 align="center">Laporan Praktikum Modul 2 - Pengenalan Bahasa C++ (Bagian Kedua)</h1>
<p align="center">Ignatius Steven Manurung - 109082500089</p>

## Dasar Teori
Dasar teori pada praktikum ini meliputi konsep array, pointer, fungsi, prosedur, dan parameter fungsi dalam bahasa pemrograman C++.

Array merupakan kumpulan data yang memiliki nama yang sama dan tipe data yang sama. Setiap elemen array dapat diakses menggunakan indeks tertentu. Array dapat berupa array satu dimensi, dua dimensi, maupun multidimensi sesuai dengan kebutuhan penyimpanan data.
Pointer adalah variabel yang digunakan untuk menyimpan alamat memori dari variabel lain. Dengan pointer, program dapat mengakses maupun memanipulasi data melalui alamat memori yang ditunjuk. Untuk memperoleh alamat suatu variabel digunakan operator alamat (&), sedangkan untuk memperoleh nilai yang ditunjuk oleh pointer digunakan operator dereference (*).
Pointer memiliki hubungan yang erat dengan array. Nama array dapat dianggap sebagai alamat elemen pertama array sehingga pointer dapat digunakan untuk mengakses elemen-elemen array melalui operasi aritmetika pointer.
Fungsi merupakan blok program yang dirancang untuk melaksanakan tugas tertentu. Penggunaan fungsi membuat program lebih terstruktur, mudah dipahami, mudah dikembangkan, serta mengurangi pengulangan kode. Fungsi umumnya menerima parameter sebagai masukan dan menghasilkan nilai balik sebagai keluaran.

Prosedur adalah fungsi yang tidak mengembalikan nilai (void). Prosedur digunakan untuk menjalankan suatu tugas tertentu tanpa menghasilkan nilai balik kepada pemanggilnya.

Parameter pada fungsi terdiri dari parameter formal dan parameter aktual. Selain itu, terdapat beberapa cara pengiriman parameter, yaitu call by value, call by pointer, dan call by reference. Call by value hanya menyalin nilai parameter sehingga perubahan tidak memengaruhi variabel asli, sedangkan call by pointer dan call by reference memungkinkan fungsi mengubah nilai variabel yang dikirimkan dari luar fungsi.
Dengan memahami konsep array, pointer, fungsi, prosedur, dan parameter fungsi, mahasiswa dapat membangun program yang lebih efisien, terstruktur, serta mampu mengelola data dan memori dengan lebih baik.


## Unguided 

### 1. Buatlah program yang dapat melakukan operasi penjumlahan, pengurangan, dan perkalian matriks 3x3 

```C++
#include <iostream>
using namespace std;

int main() {
    int A[3][3], B[3][3], C[3][3];

    cout << "Masukkan elemen matriks A (3x3):\n";
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) cin >> A[i][j];
    }

    cout << "Masukkan elemen matriks B (3x3):\n";
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) cin >> B[i][j];
    }

    cout << "\nHasil Penjumlahan (A + B):\n";
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) cout << A[i][j] + B[i][j] << " ";
        cout << endl;
    }

    cout << "\nHasil Pengurangan (A - B):\n";
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) cout << A[i][j] - B[i][j] << " ";
        cout << endl;
    }

    cout << "\nHasil Perkalian (A * B):\n";
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            C[i][j] = 0;
            for (int k = 0; k < 3; k++) C[i][j] += A[i][k] * B[k][j];
            cout << C[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
```
### Output Unguided 1 :

##### Output 1
![Screenshot Output Unguided 1_1](https://github.com/ignatiussteven/Laprak-2/blob/main/Screenshot%20(359).png)

Program ini menerima dua matriks 3x3 lalu menghitung dan menampilkan hasil penjumlahan, pengurangan, serta perkalian keduanya.

### 2. Berdasarkan guided pointer dan reference sebelumnya, buatlah keduanya dapat menukar nilai dari 3 variabel 

```C++
#include <iostream>
using namespace std;

void tukarPointer(int *a, int *b, int *c) {
    int temp = *a;
    *a = *b;
    *b = *c;
    *c = temp;
}

void tukarReference(int &a, int &b, int &c) {
    int temp = a;
    a = b;
    b = c;
    c = temp;
}

int main() {
    int x = 10, y = 20, z = 30;

    cout << "Nilai Awal : x = " << x << ", y = " << y << ", z = " << z << endl;

    tukarPointer(&x, &y, &z);
    cout << "Pointer    : x = " << x << ", y = " << y << ", z = " << z << endl;

    tukarReference(x, y, z);
    cout << "Reference  : x = " << x << ", y = " << y << ", z = " << z << endl;

    return 0;
}
```
### Output Unguided 2 :

##### Output 1
![Screenshot Output Unguided 2_1](https://github.com/ignatiussteven/Laprak-2/blob/main/Screenshot%20(360).png)

Program ini menukar urutan nilai dari tiga variabel menggunakan dua pendekatan fungsi yang berbeda, yaitu pointer dan reference.

### 3. Buatlah program yang dapat mencari nilai minimum, maksimum, dan rata – rata dari array tersebut! Gunakan function cariMinimum() untuk mencari nilai minimum dan function cariMaksimum() untuk mencari nilai maksimum, serta gunakan prosedur hitungRataRata() untuk menghitung nilai rata – rata! Buat program menggunakan menu switch-case
```C++
#include <iostream>
using namespace std;

int cariMinimum(int arr[], int n) {
    int minVal = arr[0];
    for (int i = 1; i < n; i++) {
        if (arr[i] < minVal) minVal = arr[i];
    }
    return minVal;
}

int cariMaksimum(int arr[], int n) {
    int maxVal = arr[0];
    for (int i = 1; i < n; i++) {
        if (arr[i] > maxVal) maxVal = arr[i];
    }
    return maxVal;
}

void hitungRataRata(int arr[], int n) {
    double total = 0;
    for (int i = 0; i < n; i++) total += arr[i];
    cout << "Nilai Rata-rata: " << total / n << endl;
}

int main() {
    int arrA[] = {11, 8, 5, 7, 12, 26, 3, 54, 33, 55};
    int n = sizeof(arrA) / sizeof(arrA[0]);
    int pilihan;

    do {
        cout << "\n--- Menu Program Array ---\n";
        cout << "1. Tampilkan isi array\n";
        cout << "2. cari nilai maksimum\n";
        cout << "3. cari nilai minimum\n";
        cout << "4. Hitung nilai rata - rata\n";
        cout << "0. Keluar\n";
        cout << "Pilihan: ";
        cin >> pilihan;

        switch (pilihan) {
            case 1:
                for (int i = 0; i < n; i++) cout << arrA[i] << " ";
                cout << endl;
                break;
            case 2:
                cout << "Nilai Maksimum: " << cariMaksimum(arrA, n) << endl;
                break;
            case 3:
                cout << "Nilai Minimum: " << cariMinimum(arrA, n) << endl;
                break;
            case 4:
                hitungRataRata(arrA, n);
                break;
        }
    } while (pilihan != 0);

    return 0;
}
```
### Output Unguided 3 :

##### Output 1
![Screenshot Output Unguided 3_1](https://github.com/ignatiussteven/Laprak-2/blob/main/Screenshot%20(361).png)

Program ini mengolah data array untuk menampilkan isi, mencari nilai maksimum, mencari nilai minimum, dan menghitung rata-rata melalui menu interaktif berbasis switch-case.

## Kesimpulan
Program-program C++ yang telah dirancang mengimplementasikan berbagai konsep dasar hingga menengah dalam pemrograman terstruktur dan pengolahan memori. Pemrosesan matriks dua dimensi tiga kali tiga menunjukkan bagaimana perulangan bersarang digunakan untuk mengelola data array multidimensi dalam operasi matematika. Penerapan pointer dan reference memperlihatkan cara efektif memanipulasi alamat memori serta variabel secara langsung untuk menukar nilai tanpa harus mengembalikan nilai baru secara konvensional. Selain itu, penggabungan fungsi, prosedur, dan struktur switch-case pada pemrosesan array satu dimensi menekankan pentingnya modularitas program, sehingga penanganan data seperti pencarian nilai ekstrem dan perhitungan rata-rata dapat terorganisasi secara rapi dan interaktif.

## Referensi
Deitel, P., & Deitel, H. (2017). C++ How to Program (10th ed.). Pearson.

Malik, D. S. (2014). Data Structures Using C++ (2nd ed.). Cengage Learning.

Stroustrup, B. (2013). The C++ Programming Language (4th ed.). Addison-Wesley.