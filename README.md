A new Flutter project.
# tugas06
Nama    : Egha Arya Affandi  
NIM     : 221080200077

# Flutter Calculator - Local State

## Deskripsi
Aplikasi kalkulator sederhana di Flutter yang menggunakan **local state** untuk menyimpan input angka dan hasil perhitungan sementara.  
Local state memungkinkan widget **memperbarui UI secara otomatis ketika data berubah** tanpa memengaruhi widget lain.

## Contoh Kode Local State
```dart
class _CalculatorPageState extends State<CalculatorPage> {
  final TextEditingController _num1Controller = TextEditingController();
  final TextEditingController _num2Controller = TextEditingController();
  String? result;

  void _calculate(String op) {
    double num1 = double.tryParse(_num1Controller.text) ?? 0;
    double num2 = double.tryParse(_num2Controller.text) ?? 0;
    double res = 0;
    String operasi = '';

    switch (op) {
      case '+': res = num1 + num2; operasi = 'penjumlahan'; break;
      case '-': res = num1 - num2; operasi = 'pengurangan'; break;
      case '*': res = num1 * num2; operasi = 'perkalian'; break;
      case '/': res = num2 != 0 ? num1 / num2 : double.nan; operasi = 'pembagian'; break;
    }

    setState(() {
      result = 'Hasil $operasi ${num1.toString()} dan ${num2.toString()} adalah $res';
    });
  }
}
```

## 1. Deklarasi State Class dan Variabel Lokal
Class `_CalculatorPageState` adalah State class untuk widget `CalculatorPage`.  
Variabel `_num1Controller` dan `_num2Controller` menyimpan input angka sementara dari pengguna.  
Variabel `result` menyimpan hasil perhitungan.  
Semua ini merupakan **local state**, hanya berlaku di widget ini.

## 2. Fungsi _calculate
Fungsi `_calculate(String op)` membaca input dari TextField dan mengubahnya menjadi `double`.  
Variabel `res` menyimpan hasil sementara perhitungan, sedangkan `operasi` menyimpan nama operasi yang dilakukan.

## 3. Switch Case untuk Operasi
Switch case digunakan untuk menentukan operasi matematika sesuai parameter `op` (`+`, `-`, `*`, `/`).  
Untuk pembagian, dicek agar tidak terjadi error jika pembagi nol.  
Nama operasi disimpan ke variabel `operasi` agar hasil yang ditampilkan lebih jelas.

## 4. Memperbarui UI dengan setState
Fungsi `setState()` memberi tahu Flutter bahwa **state berubah**, sehingga UI yang menampilkan `result` akan di-rebuild.  
Variabel `result` menampilkan angka pertama, angka kedua, jenis operasi, dan hasilnya.  
Perubahan state ini hanya mempengaruhi widget `_CalculatorPageState` dan tidak mempengaruhi widget lain.