# STRUKTUR KONTROL
Struktur Kontrol adalah mekanisme dalam struktur aplikasi atau algoritma. Di dalam suatu algoritma,alurnya tidak boleh melompat secara sembarangan atau tidak jelas, harus mengikuti urutan logika yang jelas dan terarah. 
- Prinsip dasarnya: jika ada kondisi tertentu, maka ada eksekusi tertentu yang dijalankan. Kalau kondisi yang disyaratkan tidak terpenuhi, program bisa error. 
- Contoh sederhananya: jika dia tidak datang, maka tidak ikut ujian.

## Struktur kontrol memiliki 4 fungsi utama, yaitu: 
1. mengatur alur eksekusi 
2. ⁠pengambilan keputusan logis.
   - Contohnya: sebuah kasus membeli gula satu bungkus, sebagai penggambaran awal sebelum masuk ke penjelasan percabangan yang lebih detail.
3. ⁠mengotomasikan perulangan tugas 
4. ⁠mencegah terjadinya eksekusi acak

# Logika Sekuensial
Algoritma runtunan ini adalah proses yang dilakukan secara beruntun dari langkah 1 sampai langkah n, atau langkah akhir. Tiap barisnya hanya dikerjakan satu-persatu tanpa ada loncatan atau perulangan, dilakukan sekali tiap instruksi.
 
# Logika Percabangan (Selection)
Kasus percabangan digambarkan, jika ada kecap dan gula maka membali satu gula; jika tidak ada kecap, maka beli dua gula.

## IF-THEN (TUNGGAL): adalah bentuk paling sederhana, di mana suatu perintag dieksekusi ketika nilainya dianggap benar (true).
- Contohnya: “belikan saya gula jika ada kecap”, hal ini disebut logika percabangan tunggal, karena ganya ada satu jalur eksekusi.

## IF-THEN-ELSE (GANDA): memiliki dua jalur pilihan sekaligus. 
- Contohnya: jika ada kecap beli satu gula dan jika tidak ada kecap beli 2 gula.

CATATAN: (Beda dengan IF-THEN tunggal, di sini selalu ada aksi yang dijalankan apapun hasil kondisinya).

## SWITCH-CASE (MAJEMUK): digunakan ketika ada banyak kemungkinan kondisi yang perlu diuji satu per satu. Begitu ketika salah satu kondisi terbukti benar, maka kondisi-kondisi berikutnya langsung diabaikan atau tidak perlu di cek lagi, hal ini menjadi lebih efisien dibanding menumpuk banyak IF ELSE.
- Contohnya: memetakan seluruh warung menggunakan konsep Array, misalnya warung A,B,C,D, di mana tiap warung di cek satu per satu sampai ketemu yang sesuai dengan apa yang dicari.

## logika perulangan (iteration)
perulangan adalah proses yang terus berjalan sampai kondisi tertentu terpenuhi.
### Ada tigas jenisnya:
1. For Loop (count controlled), dipakai ketika jumlah perulangan yang ingin dilakukan sudah pasti atau ditentukan sejak awal.
2. ⁠Pre-tested condition (While Loop), dimana kondisi di cek terlebih dahulu di awal sebelum intruksinya dijalankan.
   - Contohnya: mengecek warung indomaret satu per satu, kalau kondisinya bernilai true (misalnya barang yang dicari ada), maka langsung beli di situ. Kalau false, maka lanjut cek ke warung berikutnya.
3. ⁠Pre-tested condition (Repeat-Until), di mana kondisi baru dicek di akhir. Kalau perlu dilanjutkan lagi. Namun karena pengecekan kondisinya ada diakhir, maka blok instruksinya wajib di eksekusi minimal satu kali terlebih dahulu, walaupun ternyata kondisinya salah

## Pseudcode
memiliki 3 karakteristik utama: 
- Mirip dengan bahasa pemograman (memakai kata kunci baku)
- Independen flatfrom (tidak terikat pada suatu bahasa pemograman tertentu seperti C++, Java, atau Phython)
- Mudah diterjemahkan ke kode program sungguhan, karena logikanya sudah mendekatkan cara berpikir manusia dengan cara kerja komputer

Di dalam pseudocode, disinilah operator perbandingan atau aljabar bekerja, seperti lebih dari atau kurang dari, yang di pakai untuk menguji suatu kondisi.

## CONTOH  NOTASI UMUM PSEUDOCODE
<img src="Screenshot (86).png" alt="Screenshot (86).png" width="500" height="500">

- Contoh penerapannya: untuk menghitung nilai rata rata. prosesnya di awali dengan input nilai, kemudian dilakukan perulangan sebanyak 10 kali, makanya ini disebut Forloop, karena jumlah perulangannya sudah pasti 10 kali, bukan tergantung kondisi seperti while atau repeat until.

Interger adalah tipe data bilangan bulat, artinya tanpa angka desimal dan bisa bernilai positif maupun negatif

Flowchart adalah representasi visual dari sebuah algoritma, sebagai pembanding dari pseudocode yang berbasis teks.

















