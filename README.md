# my app
A new Flutter project.

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

  Ganti konten lib/main.dart. Hapus semua kode dari lib/main.dart. Ganti dengan kode berikut, yang menampilkan "Hello World" di tengah layar\
 
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

 Pengamatan
Contoh ini membuat aplikasi Material. Materi adalah bahasa desain visual yang standar di seluler dan web. Flutter menawarkan serangkaian widget Material yang kaya. Sebaiknya gunakan desain bahan-penggunaan: entri yang benar di bagian flutter file pubspec.yaml Anda. Ini akan memungkinkan Anda untuk menggunakan lebih banyak fitur Material, seperti kumpulan Ikon yang telah ditentukan sebelumnya.

Metode main() menggunakan notasi panah (=>). Gunakan notasi panah untuk fungsi atau metode satu baris.
Aplikasi ini memperluas StatelessWidget, yang menjadikan aplikasi itu sendiri sebagai widget. Di Flutter, hampir semuanya adalah widget, termasuk perataan, padding, dan tata letak.
Widget Scaffold, dari pustaka Material, menyediakan bilah aplikasi default, dan properti badan yang menampung pohon widget untuk layar beranda. Subpohon widget bisa sangat kompleks.
Tugas utama widget adalah menyediakan metode build() yang menjelaskan cara menampilkan widget dalam kaitannya dengan widget tingkat rendah lainnya.
Badan untuk contoh ini terdiri dari widget Pusat yang berisi widget turunan Teks. Widget Tengah menyelaraskan subpohon widgetnya ke tengah layar.

lalu kita akan menggunakan external paket Pada langkah ini, Anda akan mulai menggunakan paket sumber terbuka bernama english_words , yang berisi beberapa ribu kata bahasa Inggris yang paling sering digunakan ditambah beberapa fungsi utilitas.Anda dapat menemukan english_wordspaket tersebut, serta banyak paket open source lainnya, di pub.dev . The pubspec.yamlberkas mengelola aset dan dependensi untuk aplikasi Flutter. Di pubspec.yaml, tambahkan english_words (3.1.5 atau lebih tinggi) ke daftar dependensi:

Pada langkah ini, Anda akan menambahkan widget stateful, RandomWords, yang membuat Statekelasnya, _RandomWordsState. Anda kemudian akan menggunakan RandomWordssebagai anak di dalam MyAppwidget stateless yang ada .

Buat kode boilerplate untuk widget stateful. Di lib/main.dart, posisikan kursor Anda setelah semua kode, masukkan Return beberapa kali untuk memulai pada baris baru. Di IDE Anda, mulailah mengetik stful. Editor menanyakan apakah Anda ingin membuat Statefulwidget. Tekan Kembali untuk menerima. Kode boilerplate untuk dua kelas muncul, dan kursor diposisikan bagi Anda untuk memasukkan nama widget stateful Anda.

Masukkan RandomWordssebagai nama widget Anda. The RandomWordswidget tidak sedikit yang lain di samping menciptakan nya Statekelas.

Setelah Anda memasukkan RandomWordsnama widget stateful, IDE secara otomatis memperbarui Statekelas yang menyertainya , menamainya _RandomWordsState. Secara default, nama Statekelas diawali dengan underbar. Awalan pengenal dengan garis bawah memberlakukan privasi dalam bahasa Dart dan merupakan praktik terbaik yang direkomendasikan untuk Stateobjek.

IDE juga secara otomatis memperbarui kelas status ke extend State, yang menunjukkan bahwa Anda menggunakan State kelas generik yang dikhususkan untuk digunakan denganRandomWords. Sebagian besar logika aplikasi berada di sini—ini mempertahankan status RandomWordswidget. Kelas ini menyimpan daftar pasangan kata yang dihasilkan, yang tumbuh tanpa batas saat pengguna menggulir dan, di bagian 2 lab ini, pasangan kata favorit saat pengguna menambahkan atau menghapusnya dari daftar dengan mengalihkan ikon hati.

membuat statefull widget

class MyApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
  	      final wordPair = WordPair.random();
      return MaterialApp(
        title: 'Welcome to Flutter',
        home: Scaffold(

            title: const Text('Welcome to Flutter'),
          ),
          body: Center(
        child: Text(wordPair.asPascalCase),
        child: RandomWords(),
          ),
        ),
      );
    }
Langkah 4: Buat ListView bergulir tak terbatas Pada langkah ini, Anda akan memperluas _RandomWordsStateuntuk menghasilkan dan menampilkan daftar pasangan kata. Saat pengguna menggulir daftar (ditampilkan dalam ListViewwidget) tumbuh tanpa batas. ListView's builderpabrik konstruktor memungkinkan Anda untuk membangun sebuah tampilan daftar malas, pada permintaan.

Lanjutan dari program sebelumnya, menambahkan icon pada setiap nama random yang muncul, menambahkan class _saved sebagai tempat menampung nama favorit
class _RandomWordsState extends State { final _suggestions = []; final _saved = {}; // NEW final _biggerFont = TextStyle(fontSize: 18.0); ... } Menambahkan class alreadySaved agar memastikan nama yang sudah favorit tidak dapat difavoritkan lagi Widget _buildRow(WordPair pair) { final alreadySaved = _saved.contains(pair); // NEW ... } Menambahkan listTitle berisi bentuk icon hati sebagai tanda favorit Widget _buildRow(WordPair pair) { final alreadySaved = _saved.contains(pair); return ListTile( title: Text( pair.asPascalCase, style: _biggerFont, ), trailing: Icon( // NEW from here... alreadySaved ? Icons.favorite : Icons.favorite_border, color: alreadySaved ? Colors.red : null, semanticLabel: alreadySaved ? 'Remove from saved' : 'Save', ), // ... to here. ); }

Jika app di reload maka akan dapat dilihat bedanya sekarang sudah ada icon hati Membuat icon hati dapat berinteraksi ketika disentuh

	Widget _buildRow(WordPair pair) {
 	 final alreadySaved = _saved.contains(pair);
  	return ListTile(
    title: Text(
      pair.asPascalCase,
      style: _biggerFont,
    ),
    trailing: Icon(
      alreadySaved ? Icons.favorite : Icons.favorite_border,
      color: alreadySaved ? Colors.red : null,
      semanticLabel: alreadySaved ? 'Remove from saved' : 'Save',
    ),
    onTap: () {      // NEW lines from here...
      setState(() {
	if (alreadySaved) {
	  _saved.remove(pair);
	} else { 
	  _saved.add(pair); 
	} 
      });
    },               // ... to here.
  );
}
Sekarang jika disentuh maka icon hati akan berubah warna merah tanda item sudah difavoritkan. Membuat aplikasi dapat berpindah dengan "navigator" dengan kode dibwh ini

	class _RandomWordsState extends State<RandomWords> {
	  ...
 	 @override
 	 Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
	title: Text('Startup Name Generator'),
	actions: [
	  IconButton(
	    icon: const Icon(Icons.list),
	    onPressed: _pushSaved,
	    tooltip: 'Saved Suggestions',
	  ),
	],
      ),
      body: _buildSuggestions(),
    );
  }
  ...
}
Menambahakan list favorit sebagai tempat item item favorit void _pushSaved() { } void _pushSaved() { Navigator.of(context).push( ); } Reload aplikasi maka sekarang sudah bisa dilihat item favoritnya void _pushSaved() { Navigator.of(context).push( // Add lines from here... MaterialPageRoute( builder: (context) { final tiles = _saved.map( (pair) { return ListTile( title: Text( pair.asPascalCase, style: _biggerFont, ), ); }, ); final divided = tiles.isNotEmpty ? ListTile.divideTiles( context: context, tiles: tiles, ).toList() : [];

      return Scaffold(
        appBar: AppBar(
          title: const Text('Saved Suggestions'),
        ),
        body: ListView(children: divided),
      );
    },
	  ), // ...to here.
	);
	}

Membuat tema untuk aplikasi

class MyApp extends StatelessWidget { @override Widget build(BuildContext context) { return MaterialApp( title: 'Startup Name Generator', theme: ThemeData( // Add the 5 lines from here... appBarTheme: const AppBarTheme( backgroundColor: Colors.white, foregroundColor: Colors.black, ), ), // ... to here. home: RandomWords(), ); } }

Reload maka aplikasi sudah dapat diganti temanya



	import 'package:english_words/english_words.dart';
	import 'package:flutter/material.dart';

	void main() => runApp(MyApp());

	// #docregion MyApp
	class MyApp extends StatelessWidget {
	// #docregion build
	@override
	Widget build(BuildContext context) {
	return MaterialApp(
 	title: 'Startup Name Generator',
  	home: RandomWords(),
	);
	}
	 // #enddocregion build
	}
	// #enddocregion MyApp

	// #docregion RWS-var
	class _RandomWordsState extends State<RandomWords> {
	final _suggestions = <WordPair>[];
	final _biggerFont = const TextStyle(fontSize: 18.0);
	// #enddocregion RWS-var

	// #docregion _buildSuggestions
	Widget _buildSuggestions() {
	return ListView.builder(
    	padding: const EdgeInsets.all(16.0),
    	itemBuilder: /*1*/ (context, i) {
     	 if (i.isOdd) return const Divider(); /*2*/

      	final index = i ~/ 2; /*3*/
      	if (index >= _suggestions.length) {
        	_suggestions.addAll(generateWordPairs().take(10)); /*4*/
      	}
     	 return _buildRow(_suggestions[index]);
    	});
	}
	// #enddocregion _buildSuggestions

	// #docregion _buildRow
	Widget _buildRow(WordPair pair) {
	return ListTile(
  	title: Text(
    	pair.asPascalCase,
    	style: _biggerFont,
  	),
	);
	}
 	// #enddocregion _buildRow

	// #docregion RWS-build
	@override
		Widget build(BuildContext context) {
	 return Scaffold(
 	 appBar: AppBar(
    	title: const Text('Startup Name Generator'),
  	),
  	body: _buildSuggestions(),
	);
	}
	// #enddocregion RWS-build
	// #docregion RWS-var
	}
	// #enddocregion RWS-var

	class RandomWords extends StatefulWidget {
	 @override
	State<RandomWords> createState() => _RandomWordsState();
	}
Sejauh ini kita telah menjalankan aplikasi Anda dalam mode debug . Mode debug memperdagangkan kinerja untuk fitur pengembang yang berguna seperti hot reload dan step debugging. Bukan hal yang tidak terduga untuk melihat kinerja yang lambat dan animasi yang tersendat-sendat dalam mode debug. Setelah Anda siap untuk menganalisis kinerja atau merilis aplikasi, Anda dapat menggunakan mode build "profil" atau "rilis" Flutter.\
  
# Write Your First Flutter App, part 2
   1. Introduction
	Flutter adalah toolkit UI Google untuk membuat aplikasi cantik yang dikompilasi secara native untuk seluler, web, dan desktop dari satu basis kode. Flutter bekerja dengan kode yang ada, digunakan oleh pengembang dan organisasi di seluruh dunia, dan gratis serta open source.

Dalam codelab ini, Anda akan memperluas aplikasi Flutter seluler dasar untuk menyertakan interaktivitas. Anda juga akan membuat halaman kedua (disebut rute) yang dapat dinavigasi oleh pengguna. Terakhir, Anda akan memodifikasi tema (warna) aplikasi.
  2. Tambahkan ikon ke daftar
     Pada langkah ini, Anda akan menambahkan ikon hati ke setiap baris. Pada langkah berikutnya, Anda akan membuatnya dapat diketuk dan menyimpan favorit.
    
	add a _saved Set to _RandomWordsState. This Set stores the word pairings that the user favorited. Set is preferred to List because a properly implemented Set doesn't         allow duplicate entries.
	class _RandomWordsState extends State<RandomWords> {
  	final _suggestions = <WordPair>[];
  	final _saved = <WordPair>{};     // NEW
  	final _biggerFont = TextStyle(fontSize: 18.0);
  	...
	}
