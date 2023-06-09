[![Build Status](https://travis-ci.org/rioastamal/terbilang.svg?branch=master)](https://travis-ci.org/rioastamal/terbilang)
[![Latest Stable Version](https://poser.pugx.org/rioastamal/terbilang/v/stable)](https://packagist.org/packages/rioastamal/terbilang)
[![License](https://poser.pugx.org/rioastamal/terbilang/license)](https://packagist.org/packages/rioastamal/terbilang)
[![codecov](https://codecov.io/gh/rioastamal/terbilang/branch/master/graph/badge.svg)](https://codecov.io/gh/rioastamal/terbilang)

## Tentang

Terbilang merupakan sebuah pustaka sederhana untuk menterjemahkan angka kedalam bentuk bilangan dalam Bahasa Indonesia. Terbilang dapat menterjemahkan angka hingga satuan septiliun atau 1.0E+32 (32 nol). Terbilang menggunakan extension **bcmath** untuk memproses angka yang besar sehingga perhitungan dapat dilakukan melebihi maksimum `PHP_INT_MAX`.

Berikut contoh singkat penggunaan Terbilang.

```php
<?php
use Indonesia\AngkaTerbilang\Terbilang;

echo Terbilang::create()->terbilang('5678');
// lima ribu enam ratus tujuh puluh delapan

echo Terbilang::create()->terbilang('5000,000,000,000,000,000,000,000,000.0021');
// lima ribu septiliun koma nol nol dua satu
```

## Kebutuhan

- PHP >= 5.5
- bcmath extension

## Instalasi

Untuk instalasi Terbilang dapat digunakan composer atau melalui cara manual yaitu `require`.

### Composer

Pastikan `composer` sudah terinstal pada sistem anda. Lalu jalankan perintah berikut untuk menginstal Terbilang.

```
$ composer require coijiryuna/terbilang -vvv
```

### Instalasi Manual

Clone project Terbilang dari Github.

```
$ git clone git@github.com:coijiryuna/terbilang.git
$ cd terbilang
```

Pustaka Terbilang hanya terdiri dari sebuah file jadi cukup menggunakan `require` pada file Terbilang.php dan Terbilang sudah siap digunakan.

```php
<?php

require '/path/ke/terbilang/src/Terbilang.php';
```

### Instalasi bcmath

Extension bcmath secara default sudah terinstall dihampir semua sistem seperti pada MacOS X (via homebrew) dan Windows. Untuk mengeceknya jalankan perintah berikut pada terminal.

```
$ php -m|grep bcmath
bcmath
```

Jika bcmath muncul maka extension ini sudah terinstall di sistem. Jika belum terinstall gunakan perintah berikut untuk menginstall.

Instalasi pada Ubuntu:

```
$ sudo apt-get install php-bcmath
```

## Contoh

Berikut beberapa contoh penggunaan pustaka Terbilang dan outputnya. Argumen yang diberikan pada method terbilang() **harus** berupa string angka. Untuk contoh lebih banyak anda dapat melihat pada file tests/TerbilangTest.php.

```php
<?php
use Indonesia\AngkaTerbilang\Terbilang;

$terbilang = new Terbilang();
$terbilang->terbilang('5');
// lima

$terbilang->terbilang('15');
// lima belas

$terbilang->terbilang('99');
// sembilan puluh sembilan

$terbilang->terbilang('787654321');
// tujuh ratus delapan puluh tujuh juta enam ratus lima puluh empat ribu tiga ratus dua puluh satu

$terbilang->terbilang('11000000001000222');
// sebelas ribu triliun satu juta dua ratus dua puluh dua

$terbilang->terbilang('1,000,000,000,000,000,000,000,000.0001');
// satu septiliun koma nol nol nol satu

```

Terbilang juga mendukung penggunakan pemisah ribuan.

```php
$terbilang->terbilang('3,900');
// tiga ribu sembilan ratus

$terbilang->terbilang('1,011,000');
// satu juta sebelas ribu
```

Penggunaan desimal (pemisah titik) pada angka.

```php
$terbilang->terbilang('0.005');
// nol koma nol nol lima

$terbilang->terbilang('1,000,000.025');
// satu juta koma nol dua lima
```

Penggunaan desimal (pemisah koma) pada angka. Ini adalah penulisan yang lazim digunakan di Indonesia.

```php
// Ubah pemisah desimal ke ','
$terbilang->pemisahDesimal = ',';

$terbilang->terbilang('0,005');
// nol koma nol nol lima

$terbilang->terbilang('1.000.000,025');
// satu juta koma nol dua lima
```

Shortcut `t()` untuk method `terbilang()`.

```php
$terbilang->t('1,200,000');
// satu juta dua ratus
```

## Unit Test

Untuk menjalankan unit test disarankan menggunakan phpunit yang berada pada vendor direktori. Ini adalah phpunit yang diinstall melalui composer.

```
$ ./vendor/bin/phpunit --debug
PHPUnit 6.5.8 by Sebastian Bergmann and contributors.

Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testStaticInstance' started
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testStaticInstance' ended
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangKurangDari12' started
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangKurangDari12' ended
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangBelasan' started
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangBelasan' ended
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangPuluhan' started
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangPuluhan' ended
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangRatusan' started
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangRatusan' ended
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangRibuan' started
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangRibuan' ended
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangJutaan' started
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangJutaan' ended
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangMilyaran' started
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangMilyaran' ended
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangTriliunan' started
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangTriliunan' ended
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangSeptiliun' started
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangSeptiliun' ended
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangDenganKoma' started
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testTerbilangDenganKoma' ended
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testAngkaKomaGanda' started
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testAngkaKomaGanda' ended
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testPemisahRibuanDenganBeberapaPemisah' started
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testPemisahRibuanDenganBeberapaPemisah' ended
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testPemisahDesimalBukanTitik' started
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testPemisahDesimalBukanTitik' ended
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testShortcutMethod' started
Test 'Indonesia\AngkaTerbilang\Test\TerbilangTest::testShortcutMethod' ended


Time: 174 ms, Memory: 4.00MB
```

## Penulis

Pustaka Terbilang ditulis oleh Rio Astamal <rio@rioastamal.net>

## Lisensi

Pustaka ini menggunakan lisensi MIT [http://opensource.org/licenses/MIT](http://opensource.org/licenses/MIT).

## Alternatif

Terbilang menggunakan teknik bagi, modulus, dan rekursif. Terdapat beberapa pustaka sejenis dengan ini yang menggunakan teknik lain.

* [https://github.com/mul14/terbilang-php](https://github.com/mul14/terbilang-php)
* [https://github.com/pebriana/Fungsi-Terbilang-Rupiah](https://github.com/pebriana/Fungsi-Terbilang-Rupiah)
