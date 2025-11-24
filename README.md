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

## Cara Kerja Local State
- Semua state disimpan di class `_CalculatorPageState`.
- Variabel lokal:
  - `_num1Controller` → menyimpan input angka pertama.
  - `_num2Controller` → menyimpan input angka kedua.
  - `result` → menyimpan hasil perhitungan yang ditampilkan di UI.
- Saat pengguna menekan tombol operasi (`+`, `-`, `×`, `÷`):
  1. Fungsi `_calculate()` membaca nilai input dari `_num1Controller` dan `_num2Controller`.
  2. Melakukan perhitungan sesuai operasi.
  3. Memanggil `setState()` untuk memperbarui `result`.
  4. Flutter secara otomatis me-rebuild bagian widget yang menampilkan `result`.
