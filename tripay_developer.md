Title: API Developer Guide - TriPay Payment

URL Source: https://tripay.co.id/developer

Markdown Content:
Selamat datang di halaman Dokumentasi API. Disini telah disediakan penjelasan lengkap mengenai daftar API yang tersedia dan cara akses/penggunaan dari masing-masing API

Channel pembayaran kami terbagi menjadi 2 jenis yaitu **Open Payment**&**Closed Payment**.

**Open Payment :**

*   Nominal pembayaran tidak ditentukan oleh merchant, pelanggan dapat memasukkan nominal berapapun
*   1 Kode Bayar/Nomor Virtual Account dapat digunakan berkali-kali
*   Biaya transaksi hanya dapat dibebankan ke merchant

**Closed Payment :**

*   Nominal pembayaran ditentukan oleh merchant
*   1 Kode Bayar/Nomor Virtual Account hanya dapat digunakan sekali
*   Biaya transaksi dapat dibebankan ke merchant atau ke pelanggan

Pada bagian ini kami akan menjelaskan alur proses yang akan berjalan saat menggunakan layanan kami mulai dari proses pelanggan melakukan checkout hingga pembayaran masuk ke akun Anda.

Pada layanan kami, channel pembayaran terbagi menjadi 2 jenis yakni tipe **DIRECT** dan **REDIRECT**. Pada tipe **Direct**, semua proses transaksi dapat dilakukan di situs Anda sendiri tanpa perlu dialihkan ke situs lain sehingga Anda dapat dengan leluasa mendesain halaman pembayaran Anda sendiri. Sedangkan pada tipe **Redirect**, Anda perlu mengalihkan pelanggan menuju ke URL pembayaran yang kami sediakan untuk dapat menyelesaikan proses pembayaran.

### DIRECT

1.   Pelanggan melakukan checkout di situs Anda dan memilih metode pembayaran dari channel yang kami sediakan
2.   Sistem Anda melakukan request transaksi ke API kami
3.   Sistem kami memberikan kode bayar/nomor VA
4.   Sistem Anda menginformasikan kode bayar/nomor VA ke pelanggan dan menginstruksikan pelanggan untuk membayar
5.   Pelanggan melakukan pembayaran
6.   Sistem kami menerima status penyelesaian pembayaran pelanggan Anda
7.   Dana masuk ke akun Anda dan sistem kami mengirimkan notifikasi ke sistem Anda
8.   Sistem Anda memproses notifikasi yang dikirim dan melakukan validasi pembayaran
9.   Pembayaran tervalidasi, sistem Anda memproses pesanan ke pelanggan

### REDIRECT

1.   Pelanggan melakukan checkout di situs Anda dan memilih metode pembayaran dari channel yang kami sediakan
2.   Sistem Anda melakukan request transaksi ke API kami
3.   Sistem kami memberikan URL pembayaran
4.   Sistem Anda mengalihkan pelanggan menuju ke URL pembayaran
5.   Pelanggan menyelesaikan proses pembayaran
6.   Sistem kami menerima status penyelesaian pembayaran pelanggan Anda
7.   Dana masuk ke akun Anda dan sistem kami mengirimkan notifikasi ke sistem Anda
8.   Sistem Anda memproses notifikasi yang dikirim dan melakukan validasi pembayaran
9.   Pembayaran tervalidasi, sistem Anda memproses pesanan ke pelanggan

### Mode Transaksi

Pada sistem kami terdapat 2 mode transaksi, mode sanbox dan mode production. Apabila anda ingin melakukan testing silahkan gunakan mode sanbox, apabila anda ingin live transaksi maka silahkan gunakan mode production

### Credential API

pada sistem kami terdapat 2 Credential API, Credential API sandbox dan Credential API production

1.    Apabila anda ingin menggunakan mode sandbox silahkan gunakan Credential API sandbox, untuk bisa mendapatkan credential API sandbox, pada halaman member pilih menu **API & Integrasi > Simulator > Merchant > Detail**
2.    Apabila anda ingin menggunakan mode production silahkan gunakan credential API production , untuk bisa mendapatkan credential API production pada halaman member pilih menu **Merchant > Opsi > Edit**

 *catatan: apabila anda belum mempunyai merchant silahkan tambah merchant dengan mengklik tombol tambah merchant pada halaman daftar merchant 

setelah mendapatkan credential api pastikan channel pembayaran yang anda gunakan sudah aktif. Untuk mengaktikan channel pembayaran :

1.   Apabila anda menggunakan mode sandbox maka pada halaman member silahkan pilih menu **API & Integrasi > Simulator > Merchant > Channel Pembayaran**
2.   Apabila anda menggunakan mode production maka pada halaman member silahkan pilih menu **API & Integrasi > Merchant > Opsi > Atur Channel Pembayaran**

#### Daftar Channel & Biaya

*   * Biaya admin standar, merchant Anda mungkin memiliki biaya yang berbeda dari biaya standar
*   * Khusus OVO, SHOPEEPAY dan DANA, jika hasil perhitungan fee transaksi kurang dari Rp. 1.000;-, 

maka fee akan dibulatkan menjadi Rp. 1.000;-

| Kode | Channel | Tipe | Biaya Admin * |
| --- | --- | --- | --- |
| **PERMATAVA** | **Permata Virtual Account** Min Amount : Rp 10.000 Max Amount : Rp 10.000.000 Min Expired : 60 menit Max Expired : 43.200 menit | DIRECT | Rp 4.250 |
| **BNIVA** | **BNI Virtual Account** Min Amount : Rp 10.000 Max Amount : Rp 10.000.000 Min Expired : 15 menit Max Expired : 1.440 menit | DIRECT | Rp 4.250 |
| **BRIVA** | **BRI Virtual Account** Min Amount : Rp 10.000 Max Amount : Rp 10.000.000 Min Expired : 60 menit Max Expired : 43.200 menit | DIRECT | Rp 4.250 |
| **MANDIRIVA** | **Mandiri Virtual Account** Min Amount : Rp 10.000 Max Amount : Rp 10.000.000 Min Expired : 60 menit Max Expired : 43.200 menit | DIRECT | Rp 4.250 |
| **BCAVA** | **BCA Virtual Account** Min Amount : Rp 10.000 Max Amount : Rp 10.000.000 Min Expired : 15 menit Max Expired : 43.200 menit | DIRECT | Rp 5.500 |
| **MUAMALATVA** | **Muamalat Virtual Account** Min Amount : Rp 10.000 Max Amount : Rp 10.000.000 Min Expired : 60 menit Max Expired : 180 menit | DIRECT | Rp 4.250 |
| **CIMBVA** | **CIMB Niaga Virtual Account** Min Amount : Rp 10.000 Max Amount : Rp 10.000.000 Min Expired : 15 menit Max Expired : 43.200 menit | DIRECT | Rp 4.250 |
| **BSIVA** | **BSI Virtual Account** Min Amount : Rp 10.000 Max Amount : Rp 10.000.000 Min Expired : 60 menit Max Expired : 180 menit | DIRECT | Rp 4.250 |
| **OCBCVA** | **OCBC NISP Virtual Account** Min Amount : Rp 10.000 Max Amount : Rp 10.000.000 Min Expired : 15 menit Max Expired : 43.200 menit | DIRECT | Rp 4.250 |
| **DANAMONVA** | **Danamon Virtual Account** Min Amount : Rp 10.000 Max Amount : Rp 10.000.000 Min Expired : 15 menit Max Expired : 43.200 menit | DIRECT | Rp 4.250 |
| **OTHERBANKVA** | **Other Bank Virtual Account** Min Amount : Rp 10.000 Max Amount : Rp 10.000.000 Min Expired : 15 menit Max Expired : 1.440 menit | DIRECT | Rp 4.250 |
| **ALFAMART** | **Alfamart** Min Amount : Rp 10.000 Max Amount : Rp 2.500.000 Min Expired : 60 menit Max Expired : 1.440 menit | DIRECT | Rp 3.500 |
| **INDOMARET** | **Indomaret** Min Amount : Rp 10.000 Max Amount : Rp 2.500.000 Min Expired : 15 menit Max Expired : 43.200 menit | DIRECT | Rp 3.500 |
| **ALFAMIDI** | **Alfamidi** Min Amount : Rp 5.000 Max Amount : Rp 2.500.000 Min Expired : 60 menit Max Expired : 1.440 menit | DIRECT | Rp 3.500 |
| **OVO** | **OVO** Min Amount : Rp 1.000 Max Amount : Rp 10.000.000 Min Expired : 15 menit Max Expired : 43.200 menit | REDIRECT | 3% |
| **QRIS** | **QRIS by ShopeePay** Min Amount : Rp 1.000 Max Amount : Rp 5.000.000 Min Expired : 10 menit Max Expired : 60 menit | DIRECT | Rp 750 + 0,7% |
| **QRISC** | **QRIS (Customizable)** Min Amount : Rp 1.000 Max Amount : Rp 5.000.000 Min Expired : 10 menit Max Expired : 1.440 menit | DIRECT | Rp 750 + 0,7% |
| **QRIS2** | **QRIS** Min Amount : Rp 1.000 Max Amount : Rp 5.000.000 Min Expired : 10 menit Max Expired : 1.440 menit | DIRECT | Rp 750 + 0,7% |
| **DANA** | **DANA** Min Amount : Rp 1.000 Max Amount : Rp 10.000.000 Min Expired : 15 menit Max Expired : 60 menit | REDIRECT | 3% |
| **SHOPEEPAY** | **ShopeePay** Min Amount : Rp 1.000 Max Amount : Rp 10.000.000 Min Expired : 15 menit Max Expired : 60 menit | REDIRECT | 3% |

API ini digunakan untuk mengambil instruksi pembayaran dari masing-masing channel

### Request

*   [Endpoint](https://tripay.co.id/developer#payment-instruction-endpoint)
*   [Header](https://tripay.co.id/developer#payment-instruction-header)
*   [Body](https://tripay.co.id/developer#payment-instruction-body)
*   [Contoh Request](https://tripay.co.id/developer#payment-instruction-example)

Method GET
Sandbox URL https://tripay.co.id/api-sandbox/payment/instruction
Production URL https://tripay.co.id/api/payment/instruction

| Parameter | Contoh Nilai | Tipe | Wajib | Keterangan |
| --- | --- | --- | --- | --- |
| code | BRIVA [Lihat lainnya](https://tripay.co.id/developer?tab=channels) | string | YA | Kode channel pembayaran |
| pay_code | 1234567890 | string | TIDAK | Untuk memasukkan kode bayar/nomor VA ke dalam respon instruksi |
| amount | 10000 | int | TIDAK | Untuk memasukkan nominal ke dalam respon instruksi |
| allow_html | 1 | int | TIDAK | Untuk mengizinkan tag html pada instruksi 0 = Tidak diizinkan 1 = Diizinkan default = 1 |

*   [PHP](https://tripay.co.id/developer#payment-instruction-example-php)
*   [Python](https://tripay.co.id/developer#payment-instruction-example-python)
*   [NodeJS](https://tripay.co.id/developer#payment-instruction-example-nodejs)

```
<?php

$apiKey = 'api_key_anda';

$payload = ['code' => 'BRIVA'];

$curl = curl_init();

curl_setopt_array($curl, [
    CURLOPT_FRESH_CONNECT  => true,
    CURLOPT_URL            => 'https://tripay.co.id/api/payment/instruction?'.http_build_query($payload),
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_HEADER         => false,
    CURLOPT_HTTPHEADER     => ['Authorization: Bearer '.$apiKey],
    CURLOPT_FAILONERROR    => false,
    CURLOPT_IPRESOLVE      => CURL_IPRESOLVE_V4
]);

$response = curl_exec($curl);
$error = curl_error($curl);

curl_close($curl);

echo empty($error) ? $response : $error;

?>
```

```
import requests

apiKey = "api_key_anda"

try:
  payload = { "code": "BRIVA" }
  headers = { "Authorization": "Bearer " + apiKey }

  result = requests.get(url="https://tripay.co.id/api/payment/instruction", params=payload, headers=headers)
  response = result.text
  print(response)
except Exception as e:
  print("Request Error: " + str(e))
```

```
const axios = require('axios'); // using Axios library

var apiKey = "api_key_anda";

axios.get('https://tripay.co.id/api/payment/instruction?code=BRIVA', {
  headers: { 'Authorization': 'Bearer ' + apiKey },
  validateStatus: function (status) {
    return status < 999; // ignore http error
  }
})
.then((res) => {
  console.log(res)
})
.catch((error) => {
  console.error(error)
});
```

### Response

*   [Response Sukses](https://tripay.co.id/developer#payment-instruction-response-success)
*   [Response Gagal](https://tripay.co.id/developer#payment-instruction-response-failed)

```
{
  "success": true,
  "message": "",
  "data": [
      {
        "title": "Internet Banking",
        "steps": [
          "Login ke internet banking Bank BRI Anda",
          "Pilih menu <b>Pembayaran</b> lalu klik menu <b>BRIVA</b>",
          "Pilih rekening sumber dan masukkan Kode Bayar (<b>{{pay_code}}</b>) lalu klik <b>Kirim</b>",
          "Detail transaksi akan ditampilkan, pastikan data sudah sesuai",
          "Masukkan kata sandi ibanking lalu klik <b>Request</b> untuk mengirim m-PIN ke nomor HP Anda",
          "Periksa HP Anda dan masukkan m-PIN yang diterima lalu klik <b>Kirim</b>",
          "Transaksi sukses, simpan bukti transaksi Anda"
        ]
      },
      {
        "title": "Aplikasi BRImo",
        "steps": [
          "Login ke aplikasi BRImo Anda",
          "Pilih menu <b>BRIVA</b>",
          "Pilih sumber dana dan masukkan Nomor Pembayaran (<b>{{pay_code}}</b>) lalu klik <b>Lanjut</b>",
          "Klik <b>Lanjut</b>",
          "Detail transaksi akan ditampilkan, pastikan data sudah sesuai",
          "Klik <b>Konfirmasi</b>",
          "Klik <b>Lanjut</b>",
          "Masukkan kata sandi ibanking Anda",
          "Klik <b>Lanjut</b>",
          "Transaksi sukses, simpan bukti transaksi Anda"
        ]
      }
    ]
}
```

```
{
  "success": false,
  "message": "Invalid API Key"
}
```

API ini digunakan untuk mendapatkan daftar channel pembayaran yang aktif pada akun Merchant Anda beserta informasi lengkap termasuk biaya transaksi dari masing-masing channel

### Request

*   [Endpoint](https://tripay.co.id/developer#merchant-payment-channel-endpoint)
*   [Header](https://tripay.co.id/developer#merchant-payment-channel-header)
*   [Body](https://tripay.co.id/developer#merchant-payment-channel-body)
*   [Contoh Request](https://tripay.co.id/developer#merchant-payment-channel-example)

Method GET
Sandbox URL https://tripay.co.id/api-sandbox/merchant/payment-channel
Production URL https://tripay.co.id/api/merchant/payment-channel

| Parameter | Tipe | Contoh Nilai | Wajib | Keterangan |
| --- | --- | --- | --- | --- |
|  |  |  |  |  |

*   [PHP](https://tripay.co.id/developer#merchant-payment-channel-example-php)
*   [Python](https://tripay.co.id/developer#merchant-payment-channel-example-python)
*   [NodeJS](https://tripay.co.id/developer#merchant-payment-channel-example-nodejs)

```
<?php

$apiKey = 'api_key_anda';

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_FRESH_CONNECT  => true,
  CURLOPT_URL            => 'https://tripay.co.id/api/merchant/payment-channel',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_HEADER         => false,
  CURLOPT_HTTPHEADER     => ['Authorization: Bearer '.$apiKey],
  CURLOPT_FAILONERROR    => false,
  CURLOPT_IPRESOLVE      => CURL_IPRESOLVE_V4
));

$response = curl_exec($curl);
$error = curl_error($curl);

curl_close($curl);

echo empty($error) ? $response : $error;

?>
```

```
import requests

apiKey = "api_key_anda"

try:
  headers = { "Authorization": "Bearer " + apiKey }

  result = requests.get(url="https://tripay.co.id/api/merchant/payment-channel", params={}, headers=headers)
  response = result.text
  print(response)
except Exception as e:
  print("Request Error: " + str(e))
```

```
const axios = require('axios') // using Axios library

var apiKey = "api_key_anda";

axios.get('https://tripay.co.id/api/merchant/payment-channel', {
  headers: {'Authorization': 'Bearer ' + apiKey },
  validateStatus: function (status) {
    return status < 999; // ignore http error
  }
})
.then((res) => {
  console.log(res)
})
.catch((error) => {
  console.error(error)
});
```

### Response

*   [Response Sukses](https://tripay.co.id/developer#merchant-payment-channel-response-success)
*   [Response Gagal](https://tripay.co.id/developer#merchant-payment-channel-response-failed)

```
{
  "success": true,
  "message": "Success",
  "data": [
    {
      "group": "Virtual Account",
      "code": "MYBVA",
      "name": "Maybank Virtual Account",
      "type": "direct",
      "fee_merchant": {
        "flat": 4250,
        "percent": 0
      },
      "fee_customer": {
        "flat": 0,
        "percent": 0
      },
      "total_fee": {
        "flat": 4250,
        "percent": "0.00"
      },
      "minimum_fee" : 4000,
      "maximum_fee" : 4500,
      "minimum_amount" : 10000,
      "maximum_amount" : 10000000,
      "icon_url": "https://tripay.co.id/xxxxxxxxx.png",
      "active": true
    },
    {
      "group": "Virtual Account",
      "code": "PERMATAVA",
      "name": "Permata Virtual Account",
      "type": "direct",
      "fee_merchant": {
        "flat": 4250,
        "percent": 0
      },
      "fee_customer": {
        "flat": 0,
        "percent": 0
      },
      "total_fee": {
        "flat": 4250,
        "percent": "0.00"
      },
      "minimum_fee" : 4000,
      "maximum_fee" : 4500,
      "minimum_amount" : 10000,
      "maximum_amount" : 10000000,
      "icon_url": "https://tripay.co.id/xxxxxxxxx.png",
      "active": true
    },
    {
      "group": "Virtual Account",
      "code": "BNIVA",
      "name": "BNI Virtual Account",
      "type": "direct",
      "fee_merchant": {
        "flat": 4250,
        "percent": 0
      },
      "fee_customer": {
        "flat": 0,
        "percent": 0
      },
      "total_fee": {
        "flat": 4250,
        "percent": "0.00"
      },
      "minimum_fee" : 4000,
      "maximum_fee" : 4500,
      "minimum_amount" : 10000,
      "maximum_amount" : 10000000,
      "icon_url": "https://tripay.co.id/xxxxxxxxx.png",
      "active": true
    },
    {
      "group": "Virtual Account",
      "code": "BRIVA",
      "name": "BRI Virtual Account",
      "type": "direct",
      "fee_merchant": {
        "flat": 4250,
        "percent": 0
      },
      "fee_customer": {
        "flat": 0,
        "percent": 0
      },
      "total_fee": {
        "flat": 4250,
        "percent": "0.00"
      },
      "minimum_fee" : 4000,
      "maximum_fee" : 4500,
      "minimum_amount" : 10000,
      "maximum_amount" : 10000000,
      "icon_url": "https://tripay.co.id/xxxxxxxxx.png",
      "active": true
    },
    {
      "group": "Virtual Account",
      "code": "MANDIRIVA",
      "name": "Mandiri Virtual Account",
      "type": "direct",
      "fee_merchant": {
        "flat": 4250,
        "percent": 0
      },
      "fee_customer": {
        "flat": 0,
        "percent": 0
      },
      "total_fee": {
        "flat": 4250,
        "percent": "0.00"
      },
      "minimum_fee" : 4000,
      "maximum_fee" : 4500,
      "minimum_amount" : 10000,
      "maximum_amount" : 10000000,
      "icon_url": "https://tripay.co.id/xxxxxxxxx.png",
      "active": true
    },
    {
      "group": "Virtual Account",
      "code": "BCAVA",
      "name": "BCA Virtual Account",
      "type": "direct",
      "fee_merchant": {
        "flat": 5500,
        "percent": 0
      },
      "fee_customer": {
        "flat": 0,
        "percent": 0
      },
      "total_fee": {
        "flat": 5500,
        "percent": "0.00"
      },
      "minimum_fee" : 5500,
      "maximum_fee" : 6000,
      "minimum_amount" : 10000,
      "maximum_amount" : 10000000,
      "icon_url": "https://tripay.co.id/xxxxxxxxx.png",
      "active": true
    },
    {
      "group": "Virtual Account",
      "code": "SMSVA",
      "name": "Sinarmas Virtual Account",
      "type": "direct",
      "fee_merchant": {
        "flat": 4250,
        "percent": 0
      },
      "fee_customer": {
        "flat": 0,
        "percent": 0
      },
      "total_fee": {
        "flat": 4250,
        "percent": "0.00"
      },
      "minimum_fee" : 4000,
      "maximum_fee" : 4500,
      "minimum_amount" : 10000,
      "maximum_amount" : 10000000,
      "icon_url": "https://tripay.co.id/xxxxxxxxx.png",
      "active": true
    },
    {
      "group": "Virtual Account",
      "code": "MUAMALATVA",
      "name": "Muamalat Virtual Account",
      "type": "direct",
      "fee_merchant": {
        "flat": 4250,
        "percent": 0
      },
      "fee_customer": {
        "flat": 0,
        "percent": 0
      },
      "total_fee": {
        "flat": 4250,
        "percent": "0.00"
      },
      "minimum_fee" : 4000,
      "maximum_fee" : 4500,
      "minimum_amount" : 10000,
      "maximum_amount" : 10000000,
      "icon_url": "https://tripay.co.id/xxxxxxxxx.png",
      "active": true
    },
    {
      "group": "Virtual Account",
      "code": "CIMBVA",
      "name": "CIMB Virtual Account",
      "type": "direct",
      "fee_merchant": {
        "flat": 4250,
        "percent": 0
      },
      "fee_customer": {
        "flat": 0,
        "percent": 0
      },
      "total_fee": {
        "flat": 4250,
        "percent": "0.00"
      },
      "minimum_fee" : 4000,
      "maximum_fee" : 4500,
      "minimum_amount" : 10000,
      "maximum_amount" : 10000000,
      "icon_url": "https://tripay.co.id/xxxxxxxxx.png",
      "active": true
    },
    {
      "group": "Virtual Account",
      "code": "SAMPOERNAVA",
      "name": "Sahabat Sampoerna Virtual Account",
      "type": "direct",
      "fee_merchant": {
        "flat": 4250,
        "percent": 0
      },
      "fee_customer": {
        "flat": 0,
        "percent": 0
      },
      "total_fee": {
        "flat": 4250,
        "percent": "0.00"
      },
      "minimum_fee" : 4000,
      "maximum_fee" : 4500,
      "minimum_amount" : 10000,
      "maximum_amount" : 10000000,
      "icon_url": "https://tripay.co.id/xxxxxxxxx.png",
      "active": true
    },
    {
      "group": "Convenience Store",
      "code": "ALFAMART",
      "name": "Alfamart",
      "type": "direct",
      "fee_merchant": {
        "flat": 6000,
        "percent": 0
      },
      "fee_customer": {
        "flat": 0,
        "percent": 0
      },
      "total_fee": {
        "flat": 6000,
        "percent": "0.00"
      },
      "minimum_fee" : 5500,
      "maximum_fee" : 6500,
      "minimum_amount" : 10000,
      "maximum_amount" : 2500000,
      "icon_url": "https://tripay.co.id/xxxxxxxxx.png",
      "active": true
    },
    {
      "group": "Convenience Store",
      "code": "INDOMARET",
      "name": "Indomaret",
      "type": "direct",
      "fee_merchant": {
        "flat": 3500,
        "percent": 0
      },
      "fee_customer": {
        "flat": 0,
        "percent": 0
      },
      "total_fee": {
        "flat": 3500,
        "percent": "0.00"
      },
      "minimum_fee" : 3000,
      "maximum_fee" : 4000,
      "minimum_amount" : 10000,
      "maximum_amount" : 2500000,
      "icon_url": "https://tripay.co.id/xxxxxxxxx.png",
      "active": true
    },
    {
      "group": "Convenience Store",
      "code": "ALFAMIDI",
      "name": "Alfamidi",
      "type": "direct",
      "fee_merchant": {
        "flat": 6000,
        "percent": 0
      },
      "fee_customer": {
        "flat": 0,
        "percent": 0
      },
      "total_fee": {
        "flat": 6000,
        "percent": "0.00"
      },
      "minimum_fee" : 5500,
      "maximum_fee" : 6500,
      "minimum_amount" : 10000,
      "maximum_amount" : 2500000,
      "icon_url": "https://tripay.co.id/xxxxxxxxx.png",
      "active": true
    },
    {
      "group": "E-Wallet",
      "code": "QRIS",
      "name": "QRIS by ShopeePay",
      "type": "direct",
      "fee_merchant": {
        "flat": 750,
        "percent": 0.7
      },
      "fee_customer": {
        "flat": 0,
        "percent": 0
      },
      "total_fee": {
        "flat": 750,
        "percent": "0.70"
      },
      "minimum_fee" : 750,
      "maximum_fee" : 1000,
      "minimum_amount" : 1000,
      "maximum_amount" : 5000000,
      "icon_url": "https://tripay.co.id/xxxxxxxxx.png",
      "active": true
    }
  ]
}
```

```
{
  "success": false,
  "message": "Invalid API Key"
}
```

API ini digunakan untuk mendapatkan rincian perhitungan biaya transaksi untuk masing-masing channel berdasarkan nominal yang ditentukan

### Request

*   [Endpoint](https://tripay.co.id/developer#merchant-fee-calculator-endpoint)
*   [Header](https://tripay.co.id/developer#merchant-fee-calculator-header)
*   [Body](https://tripay.co.id/developer#merchant-fee-calculator-body)
*   [Contoh Request](https://tripay.co.id/developer#merchant-fee-calculator-example)

Method GET
Sandbox URL https://tripay.co.id/api-sandbox/merchant/fee-calculator
Production URL https://tripay.co.id/api/merchant/fee-calculator

| Parameter | Tipe | Contoh Nilai | Wajib | Keterangan |
| --- | --- | --- | --- | --- |
| amount | int | 100000 | YA | Nominal transaksi |
| code | string | BRIVA [Lihat lainnya](https://tripay.co.id/developer?tab=channels) | TIDAK | Kode channel pembayaran. Jika parameter ini kosong maka result yang dihasilkan adalah daftar semua channel pembayaran yang tersedia |

*   [PHP](https://tripay.co.id/developer#merchant-fee-calculator-example-php)
*   [Python](https://tripay.co.id/developer#merchant-fee-calculator-example-python)
*   [NodeJS](https://tripay.co.id/developer#merchant-fee-calculator-example-nodejs)

```
<?php

$apiKey = 'api_key_anda';

$payload = [
    'code' => 'QRIS',
    'amount' => 100000,
];

$curl = curl_init();

curl_setopt_array($curl, [
    CURLOPT_FRESH_CONNECT  => true,
    CURLOPT_URL            => 'https://tripay.co.id/api/merchant/fee-calculator?'.http_build_query($payload),
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_HEADER         => false,
    CURLOPT_HTTPHEADER     => ['Authorization: Bearer '.$apiKey],
    CURLOPT_FAILONERROR    => false,
    CURLOPT_IPRESOLVE      => CURL_IPRESOLVE_V4
]);

$response = curl_exec($curl);
$error = curl_error($curl);

curl_close($curl);

echo empty($error) ? $response : $error;

?>
```

```
import requests

apiKey = "api_key_anda"

try:
  payload = { "code": "QRIS", "amount": 100000 }
  headers = { "Authorization": "Bearer " + apiKey }

  result = requests.get(url="https://tripay.co.id/api/merchant/fee-calculator", params=payload, headers=headers)
  response = result.text
  print(response)
except Exception as e:
  print("Request Error: " + str(e))
```

```
const axios = require('axios') // using Axios library

var apiKey = "api_key_anda";

axios.get('https://tripay.co.id/api/merchant/fee-calculator?code=QRIS&amount=100000', {
  headers: { 'Authorization': 'Bearer ' + apiKey },
  validateStatus: function (status) {
    return status < 999; // ignore http error
  }
})
.then((res) => {
  console.log(res)
})
.catch((error) => {
  console.error(error)
});
```

### Response

*   [Response Sukses](https://tripay.co.id/developer#merchant-fee-calculator-response-success)
*   [Response Gagal](https://tripay.co.id/developer#merchant-fee-calculator-response-failed)

```
{
  "success": true,
  "message": "",
  "data": [
    {
      "code": "QRIS",
      "name": "QRIS",
      "fee": {
          "flat": 750,
          "percent": "0.70",
          "min": null,
          "max": null
      },
      "total_fee": {
          "merchant": 1450,
          "customer": 0
      }
    }
  ]
}
```

```
{
  "success": false,
  "message": "Invalid API Key"
}
```

API ini digunakan untuk mendapatkan daftar transaksi merchant

### Request

*   [Endpoint](https://tripay.co.id/developer#merchant-transactions-endpoint)
*   [Header](https://tripay.co.id/developer#merchant-transactions-header)
*   [Body](https://tripay.co.id/developer#merchant-transactions-body)
*   [Contoh Request](https://tripay.co.id/developer#merchant-transactions-example)

Method GET
Sandbox URL https://tripay.co.id/api-sandbox/merchant/transactions
Production URL https://tripay.co.id/api/merchant/transactions

| Parameter | Tipe | Contoh Nilai | Wajib | Keterangan |
| --- | --- | --- | --- | --- |
| page | int | 1 | TIDAK | Nomor halaman |
| per_page | int | 50 | TIDAK | Jumlah data per halaman. Maks: 50 |
| sort | string | desc | TIDAK | Sorting data. **asc** : Terlama ke Terbaru **desc** : Terbaru ke Terlama |
| reference | string | T0001000000455HFGRY | TIDAK | Untuk melakukan filter berdasarkan nomor referensi transaksi |
| merchant_ref | string | INV57564 | TIDAK | Untuk melakukan filter berdasarkan nomor referensi/invoice merchant |
| method | string | BRIVA [Lihat lainnya](https://tripay.co.id/developer?tab=channels) | TIDAK | Untuk melakukan filter berdasarkan kode channel pembayaran |
| status | string | PAID | TIDAK | Untuk melakukan filter berdasarkan status pembayaran |

*   [PHP](https://tripay.co.id/developer#merchant-transactions-example-php)
*   [Python](https://tripay.co.id/developer#merchant-transactions-example-python)
*   [NodeJS](https://tripay.co.id/developer#merchant-transactions-example-nodejs)

```
<?php

$apiKey = 'api_key_anda';

$payload = [
    'page' => 1,
    'per_page' => 25,
];

$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_FRESH_CONNECT  => true,
  CURLOPT_URL            => 'https://tripay.co.id/api/merchant/transactions?'.http_build_query($payload),
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_HEADER         => false,
  CURLOPT_HTTPHEADER     => ['Authorization: Bearer '.$apiKey],
  CURLOPT_FAILONERROR    => false,
  CURLOPT_IPRESOLVE      => CURL_IPRESOLVE_V4
]);

$response = curl_exec($curl);
$error = curl_error($curl);

curl_close($curl);

echo empty($err) ? $response : $error;

?>
```

```
import requests

apiKey = "api_key_anda"

try:
  payload = {
    "page": 1,
    "per_page": 25
  }

  headers = { "Authorization": "Bearer " + apiKey }

  result = requests.get(url="https://tripay.co.id/api/merchant/transactions", params=payload, headers=headers)
  response = result.text
  print(response)
except Exception as e:
  print("Request Error: " + str(e))
```

```
const axios = require('axios') // using Axios library

var apiKey = "api_key_anda";

axios.get('https://tripay.co.id/api/merchant/transactions?page=1&per_page=25', {
  headers: { 'Authorization': 'Bearer ' + apiKey },
  validateStatus: function (status) {
    return status < 999; // ignore http error
  }
})
.then((res) => {
  console.log(res)
})
.catch((error) => {
  console.error(error)
});
```

### Response

*   [Response Sukses](https://tripay.co.id/developer#merchant-transactions-response-success)
*   [Response Gagal](https://tripay.co.id/developer#merchant-transactions-response-failed)

```
{
  "success": true,
  "message": "Success",
  "data": [
      {
        "reference": "T015100000358440000",
        "merchant_ref": "INV123",
        "payment_selection_type": "static",
        "payment_method": "MYBVA",
        "payment_name": "Maybank Virtual Account",
        "customer_name": "Nama Customer",
        "customer_email": "emailcustomer@gmail.com",
        "customer_phone": null,
        "callback_url": null,
        "return_url": null,
        "amount": 153750,
        "fee_merchant": 3750,
	    "fee_customer": 0,
        "total_fee": 3750,
        "amount_received": 150000,
        "pay_code": 45649878666155,
        "pay_url": null,
        "checkout_url": "https://tripay.co.id/checkout/T015100000358440000",
        "order_items": [
          {
            "sku": null,
            "name": "T-Shirt",
            "price": 150000,
            "quantity": 1,
            "subtotal": 150000
          }
        ],
        "status": "UNPAID",
        "note": null,
        "created_at": 1592381058,
        "expired_at": 1592388303,
        "paid_at": null
      }
    ],
  "pagination": {
    "sort": "desc",
    "offset": {
      "from": 1,
      "to": 1
    },
      "current_page": 1,
      "previous_page": null,
      "next_page": null,
      "last_page": 1,
      "per_page": 25,
      "total_records": 1
  }
}
```

```
{
  "success": false,
  "message": "Invalid API Key"
}
```

API ini digunakan untuk melakukan binding/menghubungkan akun E-Wallet

### Request

*   [Endpoint](https://tripay.co.id/developer#ewallet-link-endpoint)
*   [Header](https://tripay.co.id/developer#ewallet-link-header)
*   [Body](https://tripay.co.id/developer#ewallet-link-body)
*   [Contoh Request](https://tripay.co.id/developer#ewallet-link-example)

Method POST
Sandbox URL-
Production URL https://tripay.co.id/api/ewallet/link

| Parameter | Contoh Nilai | Tipe | Wajib | Keterangan |
| --- | --- | --- | --- | --- |
| wallet_type | DANA | string | YA | Kode E-Wallet. Tersedia: * DANA |
| mobile_phone | 08123456789 | string | YA | Nomor Akun E-Wallet |

*   [PHP](https://tripay.co.id/developer#ewallet-link-example-php)
*   [Python](https://tripay.co.id/developer#ewallet-link-example-python)
*   [NodeJS](https://tripay.co.id/developer#ewallet-link-example-nodejs)

```
<?php

$apiKey       = 'api_key_anda';
$privateKey   = 'private_key_anda';
$merchantCode = 'kode merchant anda';
$walletType   = 'DANA';
$mobilePhone  = '08123456789';

$data = [
    'wallet_type'    => $walletType,
    'mobile_phone'   => $mobilePhone,
    'signature'      => hash_hmac('sha256', $merchantCode.$walletType.$mobilePhone, $privateKey)
];

$curl = curl_init();

curl_setopt_array($curl, [
    CURLOPT_FRESH_CONNECT  => true,
    CURLOPT_URL            => 'https://tripay.co.id/api/ewallet/link',
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_HEADER         => false,
    CURLOPT_HTTPHEADER     => ['Authorization: Bearer '.$apiKey],
    CURLOPT_FAILONERROR    => false,
    CURLOPT_POST           => true,
    CURLOPT_POSTFIELDS     => http_build_query($data),
    CURLOPT_IPRESOLVE      => CURL_IPRESOLVE_V4
]);

$response = curl_exec($curl);
$error = curl_error($curl);

curl_close($curl);

echo empty($error) ? $response : $error;

?>
```

```
import requests
import time
import hmac
import hashlib

try:
  apiKey     = "api_key_anda"
  privateKey = "private_key_anda"
  merchantCode = "kode_merchant_anda"

  walletType    = "DANA"
  mobilePhone   = "08123456789"

  expiry = int(time.time() + (24*60*60)) # 24 jam

  signStr = "{}{}{}".format(merchantCode, walletType, mobilePhone)
  signature = hmac.new(bytes(privateKey,'latin-1'), bytes(signStr,'latin-1'), hashlib.sha256).hexdigest()

  payload = {
    'wallet_type': walletType,
    'mobile_phone': mobilePhone,
    'signature': signature
  }

  headers = { "Authorization": "Bearer " + apiKey }

  result = requests.post(url="https://tripay.co.id/api/ewallet/link", data=payload, headers=headers)
  response = result.text
  print(response)
except Exception as e:
  print("Request Error: " + str(e))
```

```
const axios = require('axios'); // using Axios library
const crypto = require('crypto');

var apiKey     = "api_key_anda";
var privateKey = "private_key_anda";
var merchantCode = "kode_merchant_anda";

var walletType  = "DANA";
var mobilePhone   = "08123456789";

var signature = crypto.createHmac('sha256', privateKey)
    .update(merchantCode + walletType + mobilePhone)
    .digest('hex');

var payload = {
    'wallet_type': walletType,
    'mobile_phone': mobilePhone,
    'signature': signature
}

axios.post('https://tripay.co.id/api/ewallet/link', payload, {
  headers: { 'Authorization': 'Bearer ' + apiKey },
  validateStatus: function (status) {
    return status < 999; // ignore http error
  }
})
.then((res) => {
  console.log(res)
})
.catch((error) => {
  console.error(error)
});
```

### Response

*   [Response Sukses](https://tripay.co.id/developer#ewallet-link-response-success)
*   [Response Gagal](https://tripay.co.id/developer#ewallet-link-response-failed)

```
{
  "success": true,
  "data": {
    "wallet_type": "DANA",
    "mobile_phone": "08123456789",
    "authorization_url": "https://m.dana.id/m/portal/oauth?........."
  }
}
```

```
{
  "success": false,
  "message": "Failed to process your request. Please try again"
}
```

API ini digunakan untuk melakukan unlink/memutus hubungan akun E-Wallet

### Request

*   [Endpoint](https://tripay.co.id/developer#ewallet-unlink-endpoint)
*   [Header](https://tripay.co.id/developer#ewallet-unlink-header)
*   [Body](https://tripay.co.id/developer#ewallet-unlink-body)
*   [Contoh Request](https://tripay.co.id/developer#ewallet-unlink-example)

Method POST
Sandbox URL-
Production URL https://tripay.co.id/api/ewallet/unlink

| Parameter | Contoh Nilai | Tipe | Wajib | Keterangan |
| --- | --- | --- | --- | --- |
| wallet_type | DANA | string | YA | Kode E-Wallet. Tersedia: * DANA |
| mobile_phone | 08123456789 | string | YA | Nomor Akun E-Wallet |

*   [PHP](https://tripay.co.id/developer#ewallet-unlink-example-php)
*   [Python](https://tripay.co.id/developer#ewallet-unlink-example-python)
*   [NodeJS](https://tripay.co.id/developer#ewallet-unlink-example-nodejs)

```
<?php

$apiKey       = 'api_key_anda';
$privateKey   = 'private_key_anda';
$merchantCode = 'kode merchant anda';
$walletType   = 'DANA';
$mobilePhone  = '08123456789';

$data = [
    'wallet_type'    => $walletType,
    'mobile_phone'   => $mobilePhone,
    'signature'      => hash_hmac('sha256', $merchantCode.$walletType.$mobilePhone, $privateKey)
];

$curl = curl_init();

curl_setopt_array($curl, [
    CURLOPT_FRESH_CONNECT  => true,
    CURLOPT_URL            => 'https://tripay.co.id/api/ewallet/unlink',
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_HEADER         => false,
    CURLOPT_HTTPHEADER     => ['Authorization: Bearer '.$apiKey],
    CURLOPT_FAILONERROR    => false,
    CURLOPT_POST           => true,
    CURLOPT_POSTFIELDS     => http_build_query($data),
    CURLOPT_IPRESOLVE      => CURL_IPRESOLVE_V4
]);

$response = curl_exec($curl);
$error = curl_error($curl);

curl_close($curl);

echo empty($error) ? $response : $error;

?>
```

```
import requests
import time
import hmac
import hashlib

try:
  apiKey     = "api_key_anda"
  privateKey = "private_key_anda"
  merchantCode = "kode_merchant_anda"

  walletType    = "DANA"
  mobilePhone   = "08123456789"

  expiry = int(time.time() + (24*60*60)) # 24 jam

  signStr = "{}{}{}".format(merchantCode, walletType, mobilePhone)
  signature = hmac.new(bytes(privateKey,'latin-1'), bytes(signStr,'latin-1'), hashlib.sha256).hexdigest()

  payload = {
    'wallet_type': walletType,
    'mobile_phone': mobilePhone,
    'signature': signature
  }

  headers = { "Authorization": "Bearer " + apiKey }

  result = requests.post(url="https://tripay.co.id/api/ewallet/unlink", data=payload, headers=headers)
  response = result.text
  print(response)
except Exception as e:
  print("Request Error: " + str(e))
```

```
const axios = require('axios'); // using Axios library
const crypto = require('crypto');

var apiKey     = "api_key_anda";
var privateKey = "private_key_anda";
var merchantCode = "kode_merchant_anda";

var walletType  = "DANA";
var mobilePhone   = "08123456789";

var signature = crypto.createHmac('sha256', privateKey)
    .update(merchantCode + walletType + mobilePhone)
    .digest('hex');

var payload = {
    'wallet_type': walletType,
    'mobile_phone': mobilePhone,
    'signature': signature
}

axios.post('https://tripay.co.id/api/ewallet/unlink', payload, {
  headers: { 'Authorization': 'Bearer ' + apiKey },
  validateStatus: function (status) {
    return status < 999; // ignore http error
  }
})
.then((res) => {
  console.log(res)
})
.catch((error) => {
  console.error(error)
});
```

### Response

*   [Response Sukses](https://tripay.co.id/developer#ewallet-unlink-response-success)
*   [Response Gagal](https://tripay.co.id/developer#ewallet-unlink-response-failed)

```
{
  "success": true,
  "message": "Account has been unlinked"
}
```

```
{
  "success": false,
  "message": "Failed to process your request. Please try again"
}
```

API ini digunakan untuk mendapatkan informasi akun E-Wallet yang sudah terhubung

### Request

*   [Endpoint](https://tripay.co.id/developer#ewallet-detail-endpoint)
*   [Header](https://tripay.co.id/developer#ewallet-detail-header)
*   [Body](https://tripay.co.id/developer#ewallet-detail-body)
*   [Contoh Request](https://tripay.co.id/developer#ewallet-detail-example)

Method GET
Sandbox URL-
Production URL https://tripay.co.id/api/ewallet/detail

| Parameter | Tipe | Contoh Nilai | Wajib | Keterangan |
| --- | --- | --- | --- | --- |
| wallet_type | string | DANA | YA | Kode E-Wallet. Tersedia: * DANA |
| mobile_phone | string | 08123456789 | YA | Nomor Akun E-Wallet |

*   [PHP](https://tripay.co.id/developer#ewallet-detail-example-php)
*   [Python](https://tripay.co.id/developer#ewallet-detail-example-python)
*   [NodeJS](https://tripay.co.id/developer#ewallet-detail-example-nodejs)

```
<?php

$apiKey = 'api_key_anda';

$curl = curl_init();

curl_setopt_array($curl, [
    CURLOPT_FRESH_CONNECT  => true,
    CURLOPT_URL            => 'https://tripay.co.id/api/ewallet/detail?wallet_type=DANA&mobile_phone=08123456789',
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_HEADER         => false,
    CURLOPT_HTTPHEADER     => ['Authorization: Bearer '.$apiKey],
    CURLOPT_FAILONERROR    => false,
    CURLOPT_IPRESOLVE      => CURL_IPRESOLVE_V4
]);

$response = curl_exec($curl);
$error = curl_error($curl);

curl_close($curl);

echo empty($error) ? $response : $error;

?>
```

```
import requests

apiKey = "api_key_anda"

try:
  headers = { "Authorization": "Bearer " + apiKey }

  result = requests.get(url="https://tripay.co.id/api/ewallet/detail?wallet_type=DANA&mobile_phone=08123456789", data=None, headers=headers)
  response = result.text
  print(response)
except Exception as e:
  print("Request Error: " + str(e))
```

```
const axios = require('axios') // using Axios library

var apiKey = 'api_key_anda';

axios.get('https://tripay.co.id/api/ewallet/detail?wallet_type=DANA&mobile_phone=08123456789', {
  headers: { 'Authorization': 'Bearer ' + apiKey },
  validateStatus: function (status) {
    return status < 999; // ignore http error
  }
})
.then((res) => {
  console.log(res)
})
.catch((error) => {
  console.error(error)
});
```

### Response

*   [Response Sukses](https://tripay.co.id/developer#ewallet-detail-response-success)
*   [Response Gagal](https://tripay.co.id/developer#ewallet-detail-response-failed)

```
{
  "success": true,
  "data": {
    "wallet_type": "DANA",
    "mobile_phone": "08123456789",
    "balance": "100000.00",
    "currency": "IDR"
  }
}
```

```
{
  "success": false,
  "message": "Failed to fetch data. Make sure the account is linked and try again"
}
```

Untuk melakukan request transaksi, Anda harus membuat signature yang akan divalidasi sistem TriPay untuk memastikan integritas data dan pengirim saat ditransmisikan ke sistem TriPay. Pada permintaan request Transaksi baru, signature ini dibuat dari kombinasi Kode Merchant, Nomor referensi dari sistem merchant, dan nominal transaksi

Ketiga data tersebut di-hash menggunakan jenis algoritma HMAC-SHA256 yang dikunci dengan Private Key Merchant. Berikut adalah contoh pembuatan signature.

*   [PHP](https://tripay.co.id/developer#transaction-signature-create-example-php)
*   [Python](https://tripay.co.id/developer#transaction-signature-create-example-python)
*   [NodeJS](https://tripay.co.id/developer#transaction-signature-create-example-nodejs)

```
<?php

$privateKey   = 'ytf6ooi2gmlNPfpchd94jDOk8hRWOu';
$merchantCode = 'T0001';
$merchantRef  = 'INV55567';
$amount       = 1500000;

$signature = hash_hmac('sha256', $merchantCode.$merchantRef.$amount, $privateKey);

// result
// 9f167eba844d1fcb369404e2bda53702e2f78f7aa12e91da6715414e65b8c86a

?>
```

```
import hmac
import hashlib

privateKey    = "ytf6ooi2gmlNPfpchd94jDOk8hRWOu"
merchant_code = "T0001"
merchant_ref  = "INV55567"
amount        = 1500000

signStr = "{}{}{}".format(merchant_code, merchant_ref, amount)
signature = hmac.new(bytes(privateKey,'latin-1'), bytes(signStr,'latin-1'), hashlib.sha256).hexdigest()

# result
# 9f167eba844d1fcb369404e2bda53702e2f78f7aa12e91da6715414e65b8c86a
```

```
const crypto = require('crypto')

var privateKey    = "ytf6ooi2gmlNPfpchd94jDOk8hRWOu";
var merchant_code = "T0001";
var merchant_ref  = "INV55567";
var amount        = 1500000;

var signature = crypto.createHmac('sha256', privateKey)
    .update(merchant_code + merchant_ref + amount)
    .digest('hex');

// result
// 9f167eba844d1fcb369404e2bda53702e2f78f7aa12e91da6715414e65b8c86a
```

API ini digunakan untuk membuat transaksi baru atau melakukan generate kode pembayaran

### Request

*   [Endpoint](https://tripay.co.id/developer#transaction-create-endpoint)
*   [Header](https://tripay.co.id/developer#transaction-create-header)
*   [Body](https://tripay.co.id/developer#transaction-create-body)
*   [Contoh Request](https://tripay.co.id/developer#transaction-create-example)

Method POST
Sandbox URL https://tripay.co.id/api-sandbox/transaction/create
Production URL https://tripay.co.id/api/transaction/create

| Parameter | Contoh Nilai | Tipe | Wajib | Keterangan |
| --- | --- | --- | --- | --- |
| method | BRIVA [Lihat lainnya](https://tripay.co.id/developer?tab=channels) | string | YA | Kode channel pembayaran |
| merchant_ref | INV345675 | string | YA | Nomor invoice atau nomor order dari sistem Anda. Kami akan mengirim balik nomor ini ketika mengirim notifikasi status transaksi |
| amount | 1000000 | int | YA | Jumlah total pembayaran |
| customer_name | Nama Pelanggan | string | YA | Nama Pelanggan |
| customer_email | emailpelanggan@domain.com | string | YA | Email Pelanggan |
| customer_phone | 081234567890 | string | TIDAK (YA untuk beberapa channel) | Nomor HP Pelanggan |
| order_items | (Lihat tab Contoh Request) | array | YA | Rincian produk. Parameter ini harus berisi Array dengan key yang wajib: name, price, quantity |
| callback_url | https://domainanda.com/callback | string | TIDAK | URL untuk menerima callback notifikasi transaksi. Jika parameter ini kosong, maka akan menggunakan URL callback default pada menu Merchant |
| return_url | https://domainanda.com/redirect | string | TIDAK | URL untuk mengalihkan pelanggan Anda kembali |
| expired_time | 1582855837 | int | TIDAK | Batas waktu pembayaran dalam format unix timestamp ([https://www.unixtimestamp.com](https://www.unixtimestamp.com/)). Jika parameter ini tidak diisi, maka akan menggunakan batas waktu default yakni 24 jam |
| signature | fwehf874g547744b5ybnfhf | string | YA | Signature dibuat menggunakan hash HMAC-SHA256 yang dikunci dengan Private Key. (lihat pada tab Buat Signature) |

*   [PHP](https://tripay.co.id/developer#transaction-create-example-php)
*   [Python](https://tripay.co.id/developer#transaction-create-example-python)
*   [NodeJS](https://tripay.co.id/developer#transaction-create-example-nodejs)

```
<?php

$apiKey       = 'api_key_anda';
$privateKey   = 'private_key_anda';
$merchantCode = 'kode merchant anda';
$merchantRef  = 'nomor referensi merchant anda';
$amount       = 1000000;

$data = [
    'method'         => 'BRIVA',
    'merchant_ref'   => $merchantRef,
    'amount'         => $amount,
    'customer_name'  => 'Nama Pelanggan',
    'customer_email' => 'emailpelanggan@domain.com',
    'customer_phone' => '081234567890',
    'order_items'    => [
        [
            'sku'         => 'FB-06',
            'name'        => 'Nama Produk 1',
            'price'       => 500000,
            'quantity'    => 1,
            'product_url' => 'https://tokokamu.com/product/nama-produk-1',
            'image_url'   => 'https://tokokamu.com/product/nama-produk-1.jpg',
        ],
        [
            'sku'         => 'FB-07',
            'name'        => 'Nama Produk 2',
            'price'       => 500000,
            'quantity'    => 1,
            'product_url' => 'https://tokokamu.com/product/nama-produk-2',
            'image_url'   => 'https://tokokamu.com/product/nama-produk-2.jpg',
        ]
    ],
    'return_url'   => 'https://domainanda.com/redirect',
    'expired_time' => (time() + (24 * 60 * 60)), // 24 jam
    'signature'    => hash_hmac('sha256', $merchantCode.$merchantRef.$amount, $privateKey)
];

$curl = curl_init();

curl_setopt_array($curl, [
    CURLOPT_FRESH_CONNECT  => true,
    CURLOPT_URL            => 'https://tripay.co.id/api/transaction/create',
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_HEADER         => false,
    CURLOPT_HTTPHEADER     => ['Authorization: Bearer '.$apiKey],
    CURLOPT_FAILONERROR    => false,
    CURLOPT_POST           => true,
    CURLOPT_POSTFIELDS     => http_build_query($data),
    CURLOPT_IPRESOLVE      => CURL_IPRESOLVE_V4
]);

$response = curl_exec($curl);
$error = curl_error($curl);

curl_close($curl);

echo empty($error) ? $response : $error;

?>
```

```
import requests
import time
import hmac
import hashlib

try:
  apiKey     = "api_key_anda"
  privateKey = "private_key_anda"

  merchant_code = "T0001"
  merchant_ref  = "INV345675"
  amount        = 1000000

  expiry = int(time.time() + (24*60*60)) # 24 jam

  signStr = "{}{}{}".format(merchant_code, merchant_ref, amount)
  signature = hmac.new(bytes(privateKey,'latin-1'), bytes(signStr,'latin-1'), hashlib.sha256).hexdigest()

  payload = {
    'method': 'BRIVA',
    'merchant_ref': merchant_ref,
    'amount': amount,
    'customer_name': 'Nama Pelanggan',
    'customer_email': 'emailpelanggan@domain.com',
    'customer_phone': '081234567890',
    'return_url': 'https://domainanda.com/redirect',
    'expired_time': expiry,
    'signature': signature
  }

  order_items = [
    {
      'sku': 'PRODUK1',
      'name': 'Nama Produk 1',
      'price': 500000,
      'quantity': 1,
      'product_url': 'https://tokokamu.com/product/nama-produk-1',
      'image_url': 'https://tokokamu.com/product/nama-produk-1.jpg'
    },
    {
      'sku': 'PRODUK2',
      'name': 'Nama Produk 2',
      'price': 500000,
      'quantity': 1,
      'product_url': 'https://tokokamu.com/product/nama-produk-2',
      'image_url': 'https://tokokamu.com/product/nama-produk-2.jpg'
    }
  ]

  i = 0
  for item in order_items:
    for k in item:
      payload['order_items['+ str(i) +']['+ str(k) +']'] = item[k]
    i += 1

  headers = { "Authorization": "Bearer " + apiKey }

  result = requests.post(url="https://tripay.co.id/api/transaction/create", data=payload, headers=headers)
  response = result.text
  print(response)
except Exception as e:
  print("Request Error: " + str(e))
```

```
const axios = require('axios'); // using Axios library
const crypto = require('crypto');

var apiKey     = "api_key_anda";
var privateKey = "private_key_anda";

var merchant_code = "T0001";
var merchant_ref  = "INV345675";
var amount        = 1000000;

var expiry = parseInt(Math.floor(new Date()/1000) + (24*60*60)); # 24 jam

var signature = crypto.createHmac('sha256', privateKey)
    .update(merchant_code + merchant_ref + amount)
    .digest('hex');

var payload = {
    'method': 'BRIVA',
    'merchant_ref': merchant_ref,
    'amount': amount,
    'customer_name': 'Nama Pelanggan',
    'customer_email': 'emailpelanggan@domain.com',
    'customer_phone': '081234567890',
    'order_items': [
      {
        'sku': 'PRODUK1',
        'name': 'Nama Produk 1',
        'price': 500000,
        'quantity': 1,
        'product_url': 'https://tokokamu.com/product/nama-produk-1',
        'image_url': 'https://tokokamu.com/product/nama-produk-1.jpg'
      },
      {
        'sku': 'PRODUK2',
        'name': 'Nama Produk 2',
        'price': 500000,
        'quantity': 1,
        'product_url': 'https://tokokamu.com/product/nama-produk-2',
        'image_url': 'https://tokokamu.com/product/nama-produk-2.jpg'
      }
    ],
    'return_url': 'https://domainanda.com/redirect',
    'expired_time': expiry,
    'signature': signature
  }

axios.post('https://tripay.co.id/api/transaction/create', payload, {
  headers: { 'Authorization': 'Bearer ' + apiKey },
  validateStatus: function (status) {
    return status < 999; // ignore http error
  }
})
.then((res) => {
  console.log(res)
})
.catch((error) => {
  console.error(error)
});
```

### Response

*   [Response Sukses](https://tripay.co.id/developer#transaction-create-response-success)
*   [Response Gagal](https://tripay.co.id/developer#transaction-create-response-failed)

```
{
  "success": true,
  "message": "",
  "data": {
    "reference": "T0001000000000000006",
    "merchant_ref": "INV345675",
    "payment_selection_type": "static",
    "payment_method": "BRIVA",
    "payment_name": "BRI Virtual Account",
    "customer_name": "Nama Pelanggan",
    "customer_email": "emailpelanggan@domain.com",
    "customer_phone": "081234567890",
    "callback_url": "https://domainanda.com/callback",
    "return_url": "https://domainanda.com/redirect",
    "amount": 1000000,
    "fee_merchant": 1500,
    "fee_customer": 0,
    "total_fee": 1500,
    "amount_received": 998500,
    "pay_code": "57585748548596587",
    "pay_url": null,
    "checkout_url": "https://tripay.co.id/checkout/T0001000000000000006",
    "status": "UNPAID",
    "expired_time": 1582855837,
    "order_items": [
      {
        "sku": "PRODUK1",
        "name": "Nama Produk 1",
        "price": 500000,
        "quantity": 1,
        "subtotal": 500000,
        "product_url": "https://tokokamu.com/product/nama-produk-1",
        "image_url": "https://tokokamu.com/product/nama-produk-1.jpg"
      },
      {
        "sku": "PRODUK2",
        "name": "Nama Produk 2",
        "price": 500000,
        "quantity": 1,
        "subtotal": 500000,
        "product_url": "https://tokokamu.com/product/nama-produk-2",
        "image_url": "https://tokokamu.com/product/nama-produk-2.jpg"
      }
    ],
    "instructions": [
      {
        "title": "Internet Banking",
        "steps": [
          "Login ke internet banking Bank BRI Anda",
          "Pilih menu <b>Pembayaran</b> lalu klik menu <b>BRIVA</b>",
          "Pilih rekening sumber dan masukkan Kode Bayar (<b>57585748548596587</b>) lalu klik <b>Kirim</b>",
          "Detail transaksi akan ditampilkan, pastikan data sudah sesuai",
          "Masukkan kata sandi ibanking lalu klik <b>Request</b> untuk mengirim m-PIN ke nomor HP Anda",
          "Periksa HP Anda dan masukkan m-PIN yang diterima lalu klik <b>Kirim</b>",
          "Transaksi sukses, simpan bukti transaksi Anda"
        ]
      }
    ],
    "qr_string": null,
    "qr_url": null
  }
}
```

```
{
  "success": false,
  "message": "Invalid API Key"
}
```

API ini digunakan untuk mengambil detail transaksi yang pernah dibuat. Dapat juga digunakan untuk cek status pembayaran

### Request

*   [Endpoint](https://tripay.co.id/developer#transaction-detail-endpoint)
*   [Header](https://tripay.co.id/developer#transaction-detail-header)
*   [Body](https://tripay.co.id/developer#transaction-detail-body)
*   [Contoh Request](https://tripay.co.id/developer#transaction-detail-example)

Method GET
Sandbox URL https://tripay.co.id/api-sandbox/transaction/detail
Production URL https://tripay.co.id/api/transaction/detail

| Parameter | Contoh Nilai | Tipe | Wajib | Keterangan |
| --- | --- | --- | --- | --- |
| reference | T0001000000000000006 | string | YA | Kode referensi transaksi |

*   [PHP](https://tripay.co.id/developer#transaction-detail-example-php)
*   [Python](https://tripay.co.id/developer#transaction-detail-example-python)
*   [NodeJS](https://tripay.co.id/developer#transaction-detail-example-nodejs)

```
<?php

$apiKey = 'api_key_anda';

$payload = ['reference'	=> 'T0001000000000000006'];

$curl = curl_init();

curl_setopt_array($curl, [
    CURLOPT_FRESH_CONNECT  => true,
    CURLOPT_URL            => 'https://tripay.co.id/api/transaction/detail?'.http_build_query($payload),
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_HEADER         => false,
    CURLOPT_HTTPHEADER     => ['Authorization: Bearer '.$apiKey],
    CURLOPT_FAILONERROR    => false,
    CURLOPT_IPRESOLVE      => CURL_IPRESOLVE_V4
]);

$response = curl_exec($curl);
$error = curl_error($curl);

curl_close($curl);

echo empty($error) ? $response : $error;

?>
```

```
import requests

apiKey = "api_key_anda"

try:
  payload = { "reference": "T0001000000000000006" }
  headers = { "Authorization": "Bearer " + apiKey }

  result = requests.get(url="https://tripay.co.id/api/transaction/detail", params=payload, headers=headers)
  response = result.text
  print(response)
except Exception as e:
  print("Request Error: " + str(e))
```

```
const axios = require('axios'); // using Axios library

var apiKey    = "api_key_anda";
var reference = "T0001000000000000006";

axios.get('https://tripay.co.id/api/transaction/detail?reference=' + reference, {
  headers: { 'Authorization': 'Bearer ' + apiKey },
  validateStatus: function (status) {
    return status < 999; // ignore http error
  }
})
.then((res) => {
  console.log(res)
})
.catch((error) => {
  console.error(error)
});
```

### Response

*   [Response Sukses](https://tripay.co.id/developer#transaction-detail-response-success)
*   [Response Gagal](https://tripay.co.id/developer#transaction-detail-response-failed)

```
{
  "success": true,
  "message": "",
  "data": {
    "reference": "T0001000000000000006",
    "merchant_ref": "INV345675",
    "payment_selection_type": "static",
    "payment_method": "BRIVA",
    "payment_name": "BRI Virtual Account",
    "customer_name": "Nama Pelanggan",
    "customer_email": "emailpelanggan@domain.com",
    "customer_phone": "081234567890",
    "callback_url": "https://domainanda.com/callback",
    "return_url": "https://domainanda.com/redirect",
    "amount": 1000000,
    "fee_merchant": 1500,
    "fee_customer": 0,
    "total_fee": 1500,
    "amount_received": 998500,
    "pay_code": "57585748548596587",
    "pay_url": null,
    "checkout_url": "https://tripay.co.id/checkout/T0001000000000000006",
    "status": "PAID",
    "paid_at": "1582856000",
    "expired_time": 1582855837,
    "order_items": [
      {
        "sku": "PRODUK1",
        "name": "Nama Produk 1",
        "price": 500000,
        "quantity": 1,
        "subtotal": 500000,
        "product_url": "https://tokokamu.com/product/nama-produk-1",
        "image_url": "https://tokokamu.com/product/nama-produk-1.jpg"
      },
      {
        "sku": "PRODUK2",
        "name": "Nama Produk 2",
        "price": 500000,
        "quantity": 1,
        "subtotal": 500000,
        "product_url": "https://tokokamu.com/product/nama-produk-2",
        "image_url": "https://tokokamu.com/product/nama-produk-2.jpg"
      }
    ],
    "instructions": [
      {
        "title": "Internet Banking",
        "steps": [
          "Login ke internet banking Bank BRI Anda",
          "Pilih menu <b>Pembayaran</b> lalu klik menu <b>BRIVA</b>",
          "Pilih rekening sumber dan masukkan Kode Bayar (<b>57585748548596587</b>) lalu klik <b>Kirim</b>",
          "Detail transaksi akan ditampilkan, pastikan data sudah sesuai",
          "Masukkan kata sandi ibanking lalu klik <b>Request</b> untuk mengirim m-PIN ke nomor HP Anda",
          "Periksa HP Anda dan masukkan m-PIN yang diterima lalu klik <b>Kirim</b>",
          "Transaksi sukses, simpan bukti transaksi Anda"
        ]
      },
      {
        "title": "Aplikasi BRImo",
        "steps": [
          "Login ke aplikasi BRImo Anda",
          "Pilih menu <b>BRIVA</b>",
          "Pilih sumber dana dan masukkan Nomor Pembayaran (<b>57585748548596587</b>) lalu klik <b>Lanjut</b>",
          "Klik <b>Lanjut</b>",
          "Detail transaksi akan ditampilkan, pastikan data sudah sesuai",
          "Klik <b>Konfirmasi</b>",
          "Klik <b>Lanjut</b>",
          "Masukkan kata sandi ibanking Anda",
          "Klik <b>Lanjut</b>",
          "Transaksi sukses, simpan bukti transaksi Anda"
        ]
      }
    ]
  }
}
```

```
{
  "success": false,
  "message": "Invalid API Key"
}
```

API ini digunakan untuk mengecek dan mengupdate status transaksi apabila ada perubahan status pembayaran

### Request

*   [Endpoint](https://tripay.co.id/developer#transaction-check-status-endpoint)
*   [Header](https://tripay.co.id/developer#transaction-check-status-header)
*   [Body](https://tripay.co.id/developer#transaction-check-status-body)
*   [Contoh Request](https://tripay.co.id/developer#transaction-check-status-example)

Method GET
Sandbox URL https://tripay.co.id/api-sandbox/transaction/check-status
Production URL https://tripay.co.id/api/transaction/check-status

| Parameter | Tipe | Contoh Nilai | Wajib | Keterangan |
| --- | --- | --- | --- | --- |
| reference | string | T0001000000455HFGRY | YA | Nomor referensi transaksi yang ingin dilakukan pengecekan |

*   [PHP](https://tripay.co.id/developer#transaction-check-status-example-php)
*   [Python](https://tripay.co.id/developer#transaction-check-status-example-python)
*   [NodeJS](https://tripay.co.id/developer#transaction-check-status-example-nodejs)

```
<?php

$apiKey = 'api_key_anda';

$payload = [
    'reference' => 'T0001000000455HFGRY',
];

$curl = curl_init();

curl_setopt_array($curl, [
    CURLOPT_FRESH_CONNECT  => true,
    CURLOPT_URL            => 'https://tripay.co.id/api/transaction/check-status?'.http_build_query($payload),
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_HEADER         => false,
    CURLOPT_HTTPHEADER     => ['Authorization: Bearer '.$apiKey],
    CURLOPT_FAILONERROR    => false,
    CURLOPT_IPRESOLVE      => CURL_IPRESOLVE_V4
]);

$response = curl_exec($curl);
$error = curl_error($curl);

curl_close($curl);

echo empty($error) ? $response : $error;

?>
```

```
import requests

apiKey = "api_key_anda"

try:
  payload = {
    "reference": "T0001000000455HFGRY",
  }

  headers = { "Authorization": "Bearer " + apiKey }

  result = requests.get(url="https://tripay.co.id/api/transaction/check-status", params=payload, headers=headers)
  response = result.text
  print(response)
except Exception as e:
  print("Request Error: " + str(e))
```

```
const axios = require('axios') // using Axios library

var apiKey = "api_key_anda";

axios.get('https://tripay.co.id/api/transaction/check-status?reference=T0001000000455HFGRY', {
  headers: { 'Authorization': 'Bearer ' + apiKey },
  validateStatus: function (status) {
    return status < 999; // ignore http error
  }
})
.then((res) => {
  console.log(res)
})
.catch((error) => {
  console.error(error)
});
```

### Response

*   [Response Sukses](https://tripay.co.id/developer#transaction-check-status-response-success)
*   [Response Gagal](https://tripay.co.id/developer#transaction-check-status-response-failed)

```
{
  "success": true,
  "message": "Status transaksi saat ini PAID",
}
```

```
{
  "success": false,
  "message": "Invalid API Key"
}
```

Untuk melakukan request transaksi open payment, Anda harus membuat signature yang akan divalidasi sistem TriPay untuk memastikan integritas data dan pengirim saat ditransmisikan ke sistem TriPay. Pada permintaan request Transaksi baru, signature ini dibuat dari kombinasi Kode Merchant, Kode channel pembayaran, dan Nomor referensi dari sistem merchant

Ketiga data tersebut di-hash menggunakan jenis algoritma HMAC-SHA256 yang dikunci dengan Private Key Merchant. Berikut adalah contoh pembuatan signature.

*   [PHP](https://tripay.co.id/developer#open-payment-signature-create-example-php)
*   [Python](https://tripay.co.id/developer#open-payment-signature-create-example-python)
*   [NodeJS](https://tripay.co.id/developer#open-payment-signature-create-example-nodejs)

```
<?php

$privateKey   = 'private_key_anda';
$merchantCode = 'T0001';
$channel      = 'BCAVA';
$merchantRef  = 'INV55567';

$signature = hash_hmac('sha256', $merchantCode.$channel.$merchantRef, $privateKey);
```

```
import hmac
import hashlib

privateKey    = "private_key_anda"
merchant_code = "T0001"
merchant_ref  = "INV55567"
channel       = "BCAVA"

signStr   = "{}{}{}".format(merchant_code, channel, merchant_ref)
signature = hmac.new(bytes(privateKey,'latin-1'), bytes(signStr,'latin-1'), hashlib.sha256).hexdigest()
```

```
const crypto = require('crypto')

var privateKey    = "private_key_anda";
var merchant_code = "T0001";
var merchant_ref  = "INV55567";
var channel       = "BCAVA";

var signature = crypto.createHmac('sha256', privateKey)
    .update(merchant_code + channel + merchant_ref)
    .digest('hex');
```

API ini digunakan untuk membuat transaksi baru atau melakukan generate kode pembayaran untuk jenis Open Payment

### Request

*   [Endpoint](https://tripay.co.id/developer#open-payment-create-endpoint)
*   [Header](https://tripay.co.id/developer#open-payment-create-header)
*   [Body](https://tripay.co.id/developer#open-payment-create-body)
*   [Contoh Request](https://tripay.co.id/developer#open-payment-create-example)

Method POST
Sandbox URL-
Production URL https://tripay.co.id/api/open-payment/create

| Parameter | Contoh Nilai | Tipe | Wajib | Keterangan |
| --- | --- | --- | --- | --- |
| method | BCAVAOP [Lihat lainnya](https://tripay.co.id/developer?tab=channels) | string | YA | Kode channel pembayaran |
| merchant_ref | INV345678 | string | TIDAK | Kode referensi transaksi dari sistem Anda. Kami akan mengirim balik nomor referensi ini ketika mengirim notifikasi status transaksi |
| customer_name | Nama Pelanggan | string | TIDAK | Nama Pelanggan |
| signature | fwehf874g547744b5ybnfhf | string | YA | Signature dibuat menggunakan hash HMAC-SHA256 yang dikunci dengan Private Key. (lihat pada tab Buat Signature) |

*   [PHP](https://tripay.co.id/developer#open-payment-create-example-php)
*   [Python](https://tripay.co.id/developer#open-payment-create-example-python)
*   [NodeJS](https://tripay.co.id/developer#open-payment-create-example-nodejs)

```
<?php

$apiKey       = 'api_key_anda';
$privateKey   = 'private_key_anda';
$merchantCode = 'T0001';
$merchantRef  = 'INV345678';
$method       = 'BCAVA';

$data = [
    'method'        => $method,
    'merchant_ref'  => $merchantRef,
    'customer_name' => 'Nama Pelanggan',
    'signature'     => hash_hmac('sha256', $merchantCode.$method.$merchantRef, $privateKey)
];

$curl = curl_init();

curl_setopt_array($curl, [
    CURLOPT_FRESH_CONNECT  => true,
    CURLOPT_URL            => "https://tripay.co.id/api/open-payment/create",
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_HEADER         => false,
    CURLOPT_HTTPHEADER     => ['Authorization: Bearer '.$apiKey],
    CURLOPT_FAILONERROR    => false,
    CURLOPT_POST           => true,
    CURLOPT_POSTFIELDS     => http_build_query($data),
    CURLOPT_IPRESOLVE      => CURL_IPRESOLVE_V4
]);

$response = curl_exec($curl);
$error = curl_error($curl);

curl_close($curl);

echo empty($error) ? $response : $error;

?>
```

```
import requests
import time
import hmac
import hashlib

try:
  apiKey        = "api_key_anda"
  privateKey    = "private_key_anda"
  merchant_code = "T0001"
  merchant_ref  = "INV345678"
  method        = "BCAVA"

  signStr = "{}{}{}".format(merchant_code, method, merchant_ref)
  signature = hmac.new(bytes(privateKey,'latin-1'), bytes(signStr,'latin-1'), hashlib.sha256).hexdigest()

  payload = {
    'method': method,
    'merchant_ref': merchant_ref,
    'customer_name': 'Nama Pelanggan',
    'signature': signature
  }

  headers = {
    "Authorization": "Bearer " + apiKey
  }

  result = requests.post(url="https://tripay.co.id/api/open-payment/create", data=payload, headers=headers)
  response = result.text
  print(response)
except Exception as e:
  print("Request Error: " + str(e))
```

```
const axios = require('axios'); // using Axios library
const crypto = require('crypto');

var apiKey        = "api_key_anda";
var privateKey    = "private_key_anda";
var merchant_code = "T0001";
var merchant_ref  = "INV345678";
var method        = "BCAVA";

var signature = crypto.createHmac('sha256', privateKey)
    .update(merchant_code + method + merchant_ref)
    .digest('hex');

var payload = {
    'method': method,
    'merchant_ref': merchant_ref,
    'customer_name': 'Nama Pelanggan',
    'signature': signature
  }

axios.post('https://tripay.co.id/api/open-payment/create', payload, {
  headers: { 'Authorization': 'Bearer ' + apiKey },
  validateStatus: function (status) {
    return status < 999; // ignore http error
  }
})
.then((res) => {
  console.log(res)
})
.catch((error) => {
  console.error(error)
});
```

### Response

*   [Response Sukses](https://tripay.co.id/developer#open-payment-create-response-success)
*   [Response Gagal](https://tripay.co.id/developer#open-payment-create-response-failed)

```
{
  "success": true,
  "message": "",
  "data": {
    "uuid": "T0001OP9376HnpS",
    "merchant_ref": "INV345678",
    "customer_name": "Nama Pelanggan",
    "payment_name": "BCA Virtual Account",
    "payment_method": "BCAVA",
    "pay_code": "1234567890",
    "qr_string": null,
    "qr_url": null
  }
}
```

```
{
  "success": false,
  "message": "Invalid API Key"
}
```

API ini digunakan untuk mengambil detail transaksi open payment yang pernah dibuat

### Request

*   [Endpoint](https://tripay.co.id/developer#open-payment-detail-endpoint)
*   [Header](https://tripay.co.id/developer#open-payment-detail-header)
*   [Body](https://tripay.co.id/developer#open-payment-detail-body)
*   [Contoh Request](https://tripay.co.id/developer#open-payment-detail-example)

Method GET
Sandbox URL-
Production URL https://tripay.co.id/api/open-payment/{uuid}/detail

| Parameter | Contoh Nilai | Tipe | Wajib | Keterangan |
| --- | --- | --- | --- | --- |
| - |

*   [PHP](https://tripay.co.id/developer#open-payment-detail-example-php)
*   [Python](https://tripay.co.id/developer#open-payment-detail-example-python)
*   [NodeJS](https://tripay.co.id/developer#open-payment-detail-example-nodejs)

```
<?php

$apiKey = 'api_key_anda';
$uuid   = "T0001OP9376HnpS";

$curl = curl_init();

curl_setopt_array($curl, [
    CURLOPT_FRESH_CONNECT  => true,
    CURLOPT_URL            => 'https://tripay.co.id/api/open-payment/'.$uuid.'/detail',
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_HEADER         => false,
    CURLOPT_HTTPHEADER     => ['Authorization: Bearer '.$apiKey],
    CURLOPT_IPRESOLVE      => CURL_IPRESOLVE_V4
]);

$response = curl_exec($curl);
$error = curl_error($curl);

curl_close($curl);

echo empty($error) ? $response : $error;

?>
```

```
import requests

apiKey = "api_key_anda"
uuid   = "T0001OP9376HnpS"

try:
  headers = { "Authorization": "Bearer " + apiKey }

  result   = requests.get(url="https://tripay.co.id/api/open-payment/" + uuid + "/detail", headers=headers)
  response = result.text
  print(response)
except Exception as e:
  print("Request Error: " + str(e))
```

```
const axios = require('axios'); // using Axios library

var apiKey = "api_key_anda";
var uuid   = "T0001OP9376HnpS";

axios.get('https://tripay.co.id/api/open-payment/' + uuid + '/detail', {
  headers: { 'Authorization': 'Bearer ' + apiKey },
  validateStatus: function (status) {
    return status < 999; // ignore http error
  }
})
.then((res) => {
  console.log(res)
})
.catch((error) => {
  console.error(error)
});
```

### Response

*   [Response Sukses](https://tripay.co.id/developer#open-payment-detail-response-success)
*   [Response Gagal](https://tripay.co.id/developer#open-payment-detail-response-failed)

```
{
  "success": true,
  "message": "",
  "data": {
    "uuid": "T0001OP9376HnpS",
    "merchant_ref": "INV345675",
    "customer_name": "Nama Pelanggan",
    "payment_name": "BCA Virtual Account",
    "payment_method": "BCAVA",
    "pay_code": "1234567890",
    "qr_string": null,
    "qr_url": null
  }
}
```

```
{
  "success": false,
  "message": "Invalid API Key"
}
```

API ini digunakan untuk mengambil daftar pembayaran yang masuk pada open payment

### Request

*   [Endpoint](https://tripay.co.id/developer#open-payment-transactions-endpoint)
*   [Header](https://tripay.co.id/developer#open-payment-transactions-header)
*   [Body](https://tripay.co.id/developer#open-payment-transactions-body)
*   [Contoh Request](https://tripay.co.id/developer#open-payment-transactions-example)

Method GET
Sandbox URL-
Production URL https://tripay.co.id/api/open-payment/{uuid}/transactions

| Parameter | Contoh Nilai | Tipe | Wajib | Keterangan |
| --- | --- | --- | --- | --- |
| reference | T0001000000000000006 | string | TIDAK | Nomor referensi transaksi |
| merchant_ref | INV345675 | string | TIDAK | Nomor referensi dari sistem merchant |
| start_date | 2020-11-23 00:00:00 | string | TIDAK | Tanggal awal transaksi. Format: Y-m-d H:i:s |
| end_date | 2020-11-23 23:59:59 | string | TIDAK | Tanggal akhir transaksi. Format: Y-m-d H:i:s |
| per_page | 25 | int | TIDAK | Jumlah data per halaman (default: 25, max: 100) |

*   [PHP](https://tripay.co.id/developer#open-payment-transactions-example-php)
*   [Python](https://tripay.co.id/developer#open-payment-transactions-example-python)
*   [NodeJS](https://tripay.co.id/developer#open-payment-transactions-example-nodejs)

```
<?php

$apiKey = 'api_key_anda';
$uuid   = 'T0001OP9376HnpS';

$curl = curl_init();

curl_setopt_array($curl, [
    CURLOPT_FRESH_CONNECT  => true,
    CURLOPT_URL            => "https://tripay.co.id/api/open-payment/".$uuid."/transactions",
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_HEADER         => false,
    CURLOPT_HTTPHEADER     => ['Authorization: Bearer '.$apiKey],
    CURLOPT_FAILONERROR    => false,
    CURLOPT_IPRESOLVE      => CURL_IPRESOLVE_V4
]);

$response = curl_exec($curl);
$error = curl_error($curl);

curl_close($curl);

echo empty($error) ? $response : $error;

?>
```

```
import requests

apiKey = "api_key_anda"
uuid   = "T0001OP9376HnpS"

try:
  headers = { "Authorization": "Bearer " + apiKey }

  result   = requests.get(url="https://tripay.co.id/api/open-payment/" + uuid + "/transactions", headers=headers)
  response = result.text
  print(response)
except Exception as e:
  print("Request Error: " + str(e))
```

```
const axios = require('axios'); // using Axios library

var apiKey = "api_key_anda";
var uuid   = "T0001OP9376HnpS";

axios.get('https://tripay.co.id/api/open-payment/' + uuid + '/transactions', {
  headers: { 'Authorization': 'Bearer ' + apiKey },
  validateStatus: function (status) {
    return status < 999; // ignore http error
  }
})
.then((res) => {
  console.log(res)
})
.catch((error) => {
  console.error(error)
});
```

### Response

*   [Response Sukses](https://tripay.co.id/developer#open-payment-transactions-response-success)
*   [Response Gagal](https://tripay.co.id/developer#open-payment-transactions-response-failed)

```
{
    "success": true,
    "message": "",
    "data": [
        {
            "reference": "T0001000000000000006",
            "merchant_ref": "INV345675",
            "payment_method": "BCAVA",
            "payment_name": "BCA Virtual Account",
            "customer_name": "Nama Pelanggan",
            "amount": 10000,
            "fee_merchant": 4250,
            "fee_customer": 0,
            "total_fee": 4250,
            "amount_received": 5750,
            "checkout_url": "https://payment.tripay.co.id/checkout/T0001000000000000006",
            "status": "PAID",
            "paid_at": 1605967886
        },
        {
            "reference": "T0001000000000000007",
            "merchant_ref": "INV345675",
            "payment_method": "BCAVA",
            "payment_name": "BCA Virtual Account",
            "customer_name": "Nama Pelanggan",
            "amount": 10000,
            "fee_merchant": 4250,
            "fee_customer": 0,
            "total_fee": 4250,
            "amount_received": 5750,
            "checkout_url": "https://payment.tripay.co.id/checkout/T0001000000000000007",
            "status": "PAID",
            "paid_at": 1605975843
        }
    ],
    "pagination": {
        "total": 2,
        "data_from": 1,
        "data_to": 2,
        "per_page": 100,
        "current_page": 1,
        "last_page": 1,
        "next_page": null
    }
}
```

```
{
  "success": false,
  "message": "Invalid API Key"
}
```

Callback adalah pengiriman notifikasi transaksi dari server TriPay ke server pengguna dengan cara memanggil URL callback milik pengguna dengan membawa data terkait transaksi. Pada saat pembayaran dari pelanggan diselesaikan, maka sistem TriPay akan memberikan notifikasi yang berisi data transaksi yang kemudian dapat dikelola lebih lanjut oleh sistem pengguna.

Anda harus membuat sebuah file/controller/routing yang didaftarkan dan nantinya akan dipanggil oleh sistem TriPay saat transaksi berubah

Selain dikirim pada saat pembayaran sukses, callback juga akan dikirim ketika terjadi perubahan status transaksi sehingga sistem pengguna dapat mengambil tindakan yang sesuai dengan status pembayaran

Callback diamankan dengan adanya tanda tangan (signature) yang wajib Anda validasi untuk memastikan bahwa callback dikirim dari sistem kami dan data callback tidak berubah sewaktu dikirim. Dibawah ini adalah contoh pembuatan signature yang nantinya harus Anda cocokkan dengan X-Callback-Signature yang terkirim bersama dengan notifikasi transaksi.

### Pembuatan Signature

*   [PHP](https://tripay.co.id/developer#callback-signature-create-example-php)
*   [Python](https://tripay.co.id/developer#callback-signature-create-example-python)
*   [NodeJS](https://tripay.co.id/developer#callback-signature-create-example-nodejs)

```
<?php

$privateKey = 'private_key_anda';

// ambil data json callback notifikasi
$json = file_get_contents('php://input');
$signature = hash_hmac('sha256', $json, $privateKey);

// result
// 9f167eba844d1fcb369404e2bda53702e2f78f7aa12e91da6715414e65b8c86a

?>
```

```
from flask import Flask, request, jsonify # we use Flask as example here
import hmac
import hashlib

privateKey = "private_key_anda";

# ambil data json callback notifikasi
json = jsonify(request.get_json(force=True))
signature = hmac.new(bytes(privateKey,'latin-1'), bytes(json,'latin-1'), hashlib.sha256).hexdigest()

# result
# 9f167eba844d1fcb369404e2bda53702e2f78f7aa12e91da6715414e65b8c86a
```

```
const crypto = require('crypto');
const express = require('express'); // we use ExpressJS as example here

const privateKey = "private_key_anda"
const app = express();

app.use(express.json());

app.post('/endpoint-callback-anda', function (request, response) {
    var json = request.body;
    var signature = crypto.createHmac("sha256", privateKey)
        .update(JSON.stringify(json))
        .digest('hex');

    console.log(signature);
    console.log(json);
});

app.listen(3000);
```

### Request

*   [Endpoint](https://tripay.co.id/developer#callback-endpoint)
*   [Header](https://tripay.co.id/developer#callback-header)
*   [Body](https://tripay.co.id/developer#callback-body)
*   [Contoh Data](https://tripay.co.id/developer#callback-example-data)

Method:POST
URL:URL callback yang diatur di halaman Merchant atau pada saat request transaksi

| Parameter | Contoh Nilai | Tipe | Keterangan |
| --- | --- | --- | --- |
| reference | T00010000000006 | string | Nomor referensi transaksi |
| merchant_ref | INV364654 | string/null | Nomor referensi/invoice dari sistem merchant yang dikirim saat request transaksi |
| payment_method | BRI Virtual Account | string | Nama channel pembayaran yang digunakan |
| payment_method_code | BRIVA | string | Kode channel pembayaran yang digunakan |
| total_amount | 200000 | int | Jumlah pembayaran yang dibayar pelanggan |
| fee_merchant | 2000 | int | Jumlah biaya yang dikenakan ke merchant |
| fee_customer | 0 | int | Jumlah biaya yang dikenakan ke pelanggan |
| total_fee | 2000 | int | Jumlah total biaya yang dikenakan |
| amount_received | 198000 | int | Jumlah bersih yang diterima merchant |
| is_closed_payment | 1 | int | Apakah transaksi ini adalah closed payment? 0 = Open payment 1 = Closed payment |
| status | PAID | string | Status transaksi. Daftar status: PAID FAILED EXPIRED REFUND |
| paid_at | 1585574209 | int/null | Unix timestamp waktu pembayaran sukses |
| note | Transaksi sukses | string/null | Keterangan tambahan |

```
{
    "reference": "T0001000023000XXXXX",
    "merchant_ref": "INV123456",
    "payment_method": "BCA Virtual Account",
    "payment_method_code": "BCAVA",
    "total_amount": 200000,
    "fee_merchant": 2000,
    "fee_customer": 0,
    "total_fee": 2000,
    "amount_received": 198000,
    "is_closed_payment": 1,
    "status": "PAID",
    "paid_at": 1608133017,
    "note": null
}
```

### Response

Ketika sistem Anda berhasil menerima callback dari kami, sistem Anda **harus** merespon dengan format JSON yang telah ditentukan. Apabila sistem kami tidak menerima respon yang sesuai, maka akan dianggap gagal dan sistem kami akan mencoba mengirimkan ulang callback dengan jeda waktu 2 menit hingga maksimal 3 kali.

*   [Response Yang Diharapkan](https://tripay.co.id/developer#callback-response-success)
*   [Contoh Handle Callback](https://tripay.co.id/developer#callback-response-example)

```
{
    "success": true
}
```

*   [PHP (Native)](https://tripay.co.id/developer#callback-response-example-php)
*   [PHP (Laravel)](https://tripay.co.id/developer#callback-response-example-laravel)

```
<?php

// Include file koneksi database
require('db_connection.php');

// Ambil data JSON
$json = file_get_contents('php://input');

// Ambil callback signature
$callbackSignature = isset($_SERVER['HTTP_X_CALLBACK_SIGNATURE'])
    ? $_SERVER['HTTP_X_CALLBACK_SIGNATURE']
    : '';

// Isi dengan private key anda
$privateKey = 'private_key_anda';

// Generate signature untuk dicocokkan dengan X-Callback-Signature
$signature = hash_hmac('sha256', $json, $privateKey);

// Validasi signature
if ($callbackSignature !== $signature) {
    exit(json_encode([
        'success' => false,
        'message' => 'Invalid signature',
    ]));
}

$data = json_decode($json);

if (JSON_ERROR_NONE !== json_last_error()) {
    exit(json_encode([
        'success' => false,
        'message' => 'Invalid data sent by payment gateway',
    ]));
}

// Hentikan proses jika callback event-nya bukan payment_status
if ('payment_status' !== $_SERVER['HTTP_X_CALLBACK_EVENT']) {
    exit(json_encode([
        'success' => false,
        'message' => 'Unrecognized callback event: ' . $_SERVER['HTTP_X_CALLBACK_EVENT'],
    ]));
}

$invoiceId = $db->real_escape_string($data->merchant_ref);
$tripayReference = $db->real_escape_string($data->reference);
$status = strtoupper((string) $data->status);

if ($data->is_closed_payment === 1) {
    $result = $db->query("SELECT * FROM tbl_invoices WHERE id = '{$invoiceId}' AND tripay_reference = '{$tripayReference}' AND status = 'UNPAID' LIMIT 1");

    if (! $result) {
        exit(json_encode([
            'success' => false,
            'message' => 'Invoice not found or already paid: ' . $invoiceId,
        ]));
    }

    while ($invoice = $result->fetch_object()) {
        switch ($status) {
            // handle status PAID
            case 'PAID':
                if (! $db->query("UPDATE tbl_invoices SET status = 'PAID' WHERE id = {$invoice->id}")) {
                    exit(json_encode([
                        'success' => false,
                        'message' => $db->error,
                    ]));
                }
                break;

            // handle status EXPIRED
            case 'EXPIRED':
                if (! $db->query("UPDATE tbl_invoices SET status = 'EXPIRED' WHERE id = {$invoice->id}")) {
                    exit(json_encode([
                        'success' => false,
                        'message' => $db->error,
                    ]));
                }
                break;

            // handle status FAILED
            case 'FAILED':
                if (! $db->query("UPDATE tbl_invoices SET status = 'FAILED' WHERE id = {$invoice->id}")) {
                    exit(json_encode([
                        'success' => false,
                        'message' => $db->error,
                    ]));
                }
                break;

            default:
                exit(json_encode([
                    'success' => false,
                    'message' => 'Unrecognized payment status',
                ]));
        }

        exit(json_encode(['success' => true]));
    }
}
```

```
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use Illuminate\Support\Facades\Response;
use App\Models\Invoice;

class TripayCallbackController extends Controller
{
    // Isi dengan private key anda
    protected $privateKey = 'private_key_anda';

    public function handle(Request $request)
    {
        $callbackSignature = $request->server('HTTP_X_CALLBACK_SIGNATURE');
        $json = $request->getContent();
        $signature = hash_hmac('sha256', $json, $this->privateKey);

        if ($signature !== (string) $callbackSignature) {
            return Response::json([
                'success' => false,
                'message' => 'Invalid signature',
            ]);
        }

        if ('payment_status' !== (string) $request->server('HTTP_X_CALLBACK_EVENT')) {
            return Response::json([
                'success' => false,
                'message' => 'Unrecognized callback event, no action was taken',
            ]);
        }

        $data = json_decode($json);

        if (JSON_ERROR_NONE !== json_last_error()) {
            return Response::json([
                'success' => false,
                'message' => 'Invalid data sent by tripay',
            ]);
        }

        $invoiceId = $data->merchant_ref;
        $tripayReference = $data->reference;
        $status = strtoupper((string) $data->status);

        if ($data->is_closed_payment === 1) {
            $invoice = Invoice::where('id', $invoiceId)
                ->where('tripay_reference', $tripayReference)
                ->where('status', '=', 'UNPAID')
                ->first();

            if (! $invoice) {
                return Response::json([
                    'success' => false,
                    'message' => 'No invoice found or already paid: ' . $invoiceId,
                ]);
            }

            switch ($status) {
                case 'PAID':
                    $invoice->update(['status' => 'PAID']);
                    break;

                case 'EXPIRED':
                    $invoice->update(['status' => 'EXPIRED']);
                    break;

                case 'FAILED':
                    $invoice->update(['status' => 'FAILED']);
                    break;

                default:
                    return Response::json([
                        'success' => false,
                        'message' => 'Unrecognized payment status',
                    ]);
            }

            return Response::json(['success' => true]);
        }
    }
}
```
