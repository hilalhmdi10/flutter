# [![Flutter logo][]][flutter.dev]

## Documentation

* [Install Flutter](https://flutter.dev/get-started/)
* [Flutter documentation](https://flutter.dev/docs)
* [Development wiki](https://github.com/flutter/flutter/wiki)
* [Contributing to Flutter](https://github.com/flutter/flutter/blob/master/CONTRIBUTING.md)

# Flutter

Setiap aplikasi Flutter yang Anda buat juga dikompilasi untuk web. Di IDE Anda di bawah pulldown perangkat, atau di baris perintah menggunakan perangkat flutter, Anda sekarang akan melihat Chrome dan server Web terdaftar. Perangkat Chrome secara otomatis memulai Chrome. Server Web memulai server yang menghosting aplikasi sehingga Anda dapat memuatnya dari browser apa pun. Gunakan perangkat Chrome selama pengembangan sehingga Anda dapat menggunakan DevTools, dan server web saat Anda ingin menguji di browser lain. Untuk informasi selengkapnya, lihat Membuat aplikasi web dengan Flutter dan Menulis aplikasi Flutter pertama Anda di web.

#Langkah 1: Buat aplikasi Flutter pemula
  Buat aplikasi Flutter dengan template sederhana, menggunakan petunjuk di Memulai dengan aplikasi Flutter pertama Anda. Beri nama proyek startup_namer (bukan flutter_app).
  Tip: Jika Anda tidak melihat “New Flutter Project” sebagai opsi di IDE Anda, pastikan Anda telah menginstal plugin untuk Flutter dan Dart.
  
  sebagian besar akan mengedit lib/main.dart, tempat kode Dart berada.

  Ganti konten lib/main.dart. Hapus semua kode dari lib/main.dart. Ganti dengan kode berikut, yang menampilkan "Hello World" di tengah layar.
  
 

import 'package:flutter/material.dart';

   void main() => runApp(MyApp());

  class MyApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
        title: 'Welcome to Flutter',
        home: Scaffold(
          appBar: AppBar(
            title: const Text('Welcome to Flutter'),
          ),
          body: const Center(
            child: Text('Hello World'),
          ),
        ),
      );
    }
  }
